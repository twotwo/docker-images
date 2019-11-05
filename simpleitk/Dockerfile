FROM hub.infervision.com/vendor/python:3.7-slim-stretch
COPY ./requirements.txt /
RUN apt-get update && apt-get install --no-install-recommends -y \
      gcc libc-dev \
   && echo "[global]" > /etc/pip.conf \
   && echo "index-url = https://mirrors.aliyun.com/pypi/simple" >> /etc/pip.conf \
   && python -m pip install --upgrade pip \
   && python -m pip install --no-cache-dir -r requirements.txt
