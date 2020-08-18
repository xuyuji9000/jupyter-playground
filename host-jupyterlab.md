1. Get a server from cloud provider 

2. Install JupyterLab

``` bash
pip3 install jupyterlab
```

3. Use password instead of token for accessing service

``` bash
jupyter notebook password
```

4. Generate configuration 

``` bash
jupyter lab --generate-config
```

5. Start 

``` bash
jupyter lab --allow-root --no-browser --ip="0.0.0.0"
```

5. Nginx configuration

```
location / {
    proxy_pass http://127.0.0.1:8888;
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


# Reference

1. [Jupyter notebook as a service on Ubuntu 18.04 with Python 3](https://naysan.ca/2019/09/07/jupyter-notebook-as-a-service-on-ubuntu-18-04-with-python-3/)
