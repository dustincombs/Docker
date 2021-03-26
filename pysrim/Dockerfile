FROM dccombs/srim:latest
MAINTAINER Dustin Combs <dccombs@gmail.com>
#modified from costrouc/pysrim

ARG VERSION=v0.4.0
ARG USERNAME=costrouc
ARG PROJECT=pysrim

RUN apt update && \
    apt install python3.6 python3-pip -y && \
    rm -rf /var/lib/apt/lists/*

RUN pip3 install --no-cache-dir https://gitlab.com/$USERNAME/$PROJECT/repository/$VERSION/archive.tar.gz

# xvfb-run -a python3.6 <script.py>
