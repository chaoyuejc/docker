# Base images 基础镜像
FROM python:3.7
# MAINTAINER 维护者信息
MAINTAINER chaoyuejc@163.com
# 设置工作目录
WORKDIR /root/
# 获取开源 searx 源码
RUN git clone https://github.com/asciimoo/searx.git && \
  cd searx && \
  pip install -r requirements.txt && \
  sed -i "s/ultrasecretkey/`openssl rand -hex 16`/g" searx/settings.yml && \
  sed -i 's/bind_address : "127.0.0.1"/bind_address : "0.0.0.0"/g' searx/settings.yml && \
  sed -i 's/language : "en-US"/language : "zh-CN"/g' searx/settings.yml
# EXPOSE 映射端口
EXPOSE 8888
# CMD 运行以下命令
CMD python /root/searx/searx/webapp.py