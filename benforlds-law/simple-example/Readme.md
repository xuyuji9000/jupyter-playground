This folder contains a simple example demonstrates Benford's Law.


- Prepare environment

    ``` bash
    virtualenv -p python3 venv
    source venv/bin/activate
    pip3 install jupyterlab
    pip3 freeze > requirements.txt

    # use this command during non-first time environment setup 
    # pip3 install -r ./requirements.txt 
    ```


- Start

    ``` bash
    source venv/bin/activate
    jupyter-lab
    ```
