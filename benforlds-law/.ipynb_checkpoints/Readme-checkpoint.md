This folder use Benford's Law to analysis public data to get an indicator to see whether it's possible the US 2020 voting is fraudulent.


- Prepare environment

    ``` bash
    virtualenv -p python3 venv
    source venv/bin/activate
    pip3
    pip3 install -r ./requirements.txt
    ```

- Start

    ``` bash
    source venv/bin/activate
    jupyter-lab
    ```


## Reference

1. [ 拜登选票不符合本福特定律？如何识别数据造假？](https://mp.weixin.qq.com/s/pXEr11FAesA2TmPSC8cN4A)

    > Use this article to get the rationale of using Benford's Law to analysis potential voting fraudulent.


2. [ cjph8914 / 2020_benfords ](https://github.com/cjph8914/2020_benfords)

    > Use this Github repo to get the source of data.
