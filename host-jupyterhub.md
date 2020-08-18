## Prepare JupyterHub

1. Get a server from cloud provider 

2. Install JupyterHub

``` bash
pip3 install jupyterhub
pip3 install notebook
pip3 install jupyterlab
npm install -g configurable-http-proxy
```

3. Generate default configurations

``` bash
jupyterhub --generate-config
```

3. Set up listening port

```
#/path/to/jupyterhub_config.py
c.JupyterHub.bind_url = 'http://127.0.0.1:8000'
```

4. Nginx configuration

```
location / {
    proxy_pass http://127.0.0.1:8000;
    proxy_set_header X-Real-IP $remote_addr;
    proxy_set_header Host $host;
    proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;

    # websocket headers
    proxy_http_version 1.1;
    proxy_set_header Upgrade $http_upgrade;
    proxy_set_header Connection "Upgrade";
    proxy_set_header Host $host;
}
```

5. Prepare user

``` bash
adduser jupyterhub-user1
passwd jupyterhub-user1
```

# Reference 

1. [Quickstart](https://jupyterhub.readthedocs.io/en/stable/quickstart.html)

2. [Using a reverse proxy](https://jupyterhub.readthedocs.io/en/stable/reference/config-proxy.html)

3. [NGINX as a WebSocket Proxy](https://www.nginx.com/blog/websocket-nginx/)
