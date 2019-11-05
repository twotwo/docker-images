FROM hub.infervision.com/vendor/python:3.7-slim-stretch
RUN echo "[global]" > /etc/pip.conf \
   && echo "index-url = https://mirrors.aliyun.com/pypi/simple" >> /etc/pip.conf \
   && python -m pip install --upgrade pip \
   && python -m pip install --no-cache-dir -r requirements.txt
