# SimpleITK 1.2 under Python 3.7

## Reference

- [SimpleITK/GettingStarted](https://itk.org/Wiki/SimpleITK/GettingStarted)
- [pip wheel](https://pip.pypa.io/en/stable/reference/pip_wheel/)
- [pip User Guide](https://pip.pypa.io/en/stable/user_guide/)
- [Building Wheels](https://wheel.readthedocs.io/en/stable/user_guide.html#building-wheels)

## 3.7-alpine can't install wheels

    $ docker run -it --rm python:3.7-alpine sh
    / # pip install --upgrade pip && pip install --no-cache-dir simpleitk
    Requirement already up-to-date: pip in /usr/local/lib/python3.7/site-packages (19.3.1)
    Collecting simpleitk
    Downloading https://files.pythonhosted.org/packages/11/f5/dfc5fe1ee82baa0bf35579ab49f0b0d318ae528a7557552579a587f9d7a3/SimpleITK-1.2.0.tar.gz (2.0MB)
        |████████████████████████████████| 2.0MB 918kB/s
        ERROR: Command errored out with exit status 1:
        command: /usr/local/bin/python -c 'import sys, setuptools, tokenize; sys.argv[0] = '"'"'/tmp/pip-install-k9j966j5/simpleitk/setup.py'"'"'; __file__='"'"'/tmp/pip-install-k9j966j5/simpleitk/setup.py'"'"';f=getattr(tokenize, '"'"'open'"'"', open)(__file__);code=f.read().replace('"'"'\r\n'"'"', '"'"'\n'"'"');f.close();exec(compile(code, __file__, '"'"'exec'"'"'))' egg_info --egg-base /tmp/pip-install-k9j966j5/simpleitk/pip-egg-info
            cwd: /tmp/pip-install-k9j966j5/simpleitk/
        Complete output (4 lines):
        python -m pip install scikit-build
        scikit-build is required to build from source.
        Please run:

        ----------------------------------------
    ERROR: Command errored out with exit status 1: python setup.py egg_info Check the logs for full command output.

## 3.7-slim-stretch can install latest wheels

    $ docker run -it --rm python:3.7-slim-stretch bash
    root@c493dd41ca0b:/# du -sh /
    159M	/
    root@c493dd41ca0b:/# pip install --no-cache-dir --install-option="--prefix=/install" simpleitk
    Collecting simpleitk
    Downloading https://files.pythonhosted.org/packages/58/5f/f592b07d0f04504bf4a48dfa6bbd9fcaa8591169513f845908caf3e8c9f8/SimpleITK-1.2.3-cp37-cp37m-manylinux1_x86_64.whl (42.5MB)
        |████████████████████████████████| 42.5MB 1.2MB/s
    Installing collected packages: simpleitk
    Successfully installed simpleitk-1.2.3
    root@c493dd41ca0b:/# du -sh /
    379M	/

## SimpleITK under 3.7-slim-stretch

    FROM hub.infervision.com/vendor/python:3.7-slim-stretch
    RUN echo "[global]" > /etc/pip.conf \
    && echo "index-url = https://mirrors.aliyun.com/pypi/simple" >> /etc/pip.conf \
    && python -m pip install --upgrade pip \
    && python -m pip install --no-cache-dir simpleitk

