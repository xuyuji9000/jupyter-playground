1. Get a server from cloud provider 

2. Prepare jupyterlab environment

``` bash
python3 -m venv ./venv
source ./venv/bin/activate
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

6. Enable as daemon

```
# /srv/jupyterlab/jupyterlab.service
[Unit]
Description=Jupyter Lab

[Service]
Type=simple
PIDFile=/run/jupyter.pid
Environment=WORKING_DIRECTORY=/srv/jupyterlab/notebook
ExecStart=/bin/bash -c ". /srv/jupyterlab/venv/bin/activate;jupyter lab --allow-root --no-browser --ip='0.0.0.0' --port=8888 --notebook-dir=$WORKING_DIRECTORY"
User=root
Group=root
WorkingDirectory=/srv/jupyterlab
Restart=always
RestartSec=10

[Install]
WantedBy=multi-user.target
```


# Reference

1. [Jupyter notebook as a service on Ubuntu 18.04 with Python 3](https://naysan.ca/2019/09/07/jupyter-notebook-as-a-service-on-ubuntu-18-04-with-python-3/)

2. [IPython: Blocking Cross Origin API request](https://github.com/twosigma/beakerx/issues/1963#issuecomment-334721791)
