FROM debian:buster
MAINTAINER Dustin Combs <dccombs@gmail.com>
# modified from costrouc/srim

ARG SRIM_DIR="/srim"

RUN dpkg --add-architecture i386

RUN apt update && \
    apt install wget unzip xvfb wine32 cabextract -y && \
    rm -rf /var/lib/apt/lists/*

# winetricks
RUN cd /opt && \
    wget -q https://raw.githubusercontent.com/Winetricks/winetricks/master/src/winetricks && \
    chmod +x winetricks && \
    cp winetricks /usr/local/bin

# https://appdb.winehq.org/objectManager.php?sClass=version&iId=27152
RUN xvfb-run winetricks -q comdlg32ocx msflxgrd richtx32 vb5run comctl32ocx tabctl32

RUN mkdir -p $SRIM_DIR && \
    cd $SRIM_DIR && \
    wget -q https://gitlab.com/costrouc/pysrim/raw/master/assets/srim.2013.zip && \
    unzip srim.2013.zip -d / && \
    cd "$SRIM_DIR" && \
    echo "1" > $SRIM_DIR/TRIMAUTO


WORKDIR "$SRIM_DIR"
CMD ["xvfb-run", "-a", "wine", "TRIM.exe"]

# Modify $SRIM_DIR/srim/TRIM.IN for input file
# Outputfiles in $SRIM_DIR/
