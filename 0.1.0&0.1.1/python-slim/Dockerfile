FROM python:3.10-slim

WORKDIR /staticjinjaplus

ARG SJP_TAG=0.1.1

ARG SJP_HASH=30d9424df1eddb73912b0e2ad5375fa2c876c8e30906bec91952dfb75dcf220b

ADD --checksum=sha256:${SJP_HASH} https://github.com/MrDave/StaticJinjaPlus/archive/refs/tags/${SJP_TAG}.tar.gz /tmp/app.tar.gz

RUN tar xzf /tmp/app.tar.gz --strip-components=1 -C /staticjinjaplus && rm /tmp/app.tar.gz

RUN python3 -m venv venv && venv/bin/pip install -r requirements.txt --no-cache-dir

ENTRYPOINT ["venv/bin/python3", "main.py"]

CMD ["--srcpath=./templates", "--outpath=./build"]