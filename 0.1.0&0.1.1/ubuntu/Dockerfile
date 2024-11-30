FROM ubuntu:22.04

RUN apt-get update && apt-get install -y \
    python3 \
    python3-pip \
    python3.10-venv \
    && rm -rf /var/lib/apt/lists/*

WORKDIR /staticjinjaplus

ARG SJP_TAG=0.1.1

ARG SJP_HASH=e3b0c44298fc1c149afbf4c8996fb92427ae41e4649b934ca495991b7852b855

ADD --checksum=sha256:${SJP_HASH} https://github.com/MrDave/StaticJinjaPlus/archive/refs/tags/${SJP_TAG}.tar.gz /tmp/app.tar.gz

RUN tar xzf /tmp/app.tar.gz --strip-components=1 -C /staticjinjaplus && rm /tmp/app.tar.gz

RUN python3 -m venv venv && venv/bin/pip install -r requirements.txt --no-cache-dir

ENTRYPOINT ["venv/bin/python3", "main.py"]

CMD ["--srcpath=./templates", "--outpath=./build"]
