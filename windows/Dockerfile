FROM ubuntu:latest
ENTRYPOINT ["/bin/bash"]

ARG DEBIAN_FRONTEND="noninteractive"
RUN \
apt-get -y update && \
apt-get -y upgrade && \
apt-get -y install build-essential iputils-ping nano \
    autoconf automake autopoint bash bison bzip2 flex gettext \
    git g++ gperf intltool libffi-dev libgdk-pixbuf2.0-dev \
    libtool-bin libltdl-dev libssl-dev libxml-parser-perl lzip make \
    openssl p7zip-full patch perl pkg-config python ruby scons \
    sed unzip wget xz-utils \
    g++-multilib libc6-dev-i386 && \
apt-get -y autoremove && \
apt-get -y autoclean && \
apt-get -y clean && \
exit 0

RUN \
cd /opt && \
git clone https://github.com/mxe/mxe.git && \
cd /opt/mxe && \
NPROC=$(($(nproc)+4)) && \
make --jobs=$NPROC JOBS=$NPROC MXE_TARGETS='x86_64-w64-mingw32.static' qtbase qtcharts qtdeclarative qtquickcontrols qtquickcontrols2 && \
ln -s /opt/mxe/usr/bin/x86_64-w64-mingw32.static-qmake-qt5 /usr/bin/qmake && \
qmake --version && \
exit 0

ENV PATH="${PATH}:/opt/mxe/usr/bin"

# qt5 qtmultimedia
# i686-w64-mingw32
