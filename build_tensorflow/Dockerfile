FROM debian:buster

RUN dpkg --add-architecture armhf && dpkg --add-architecture arm64 \
    && apt-get update && apt-get install -y \
        openjdk-11-jdk automake autoconf libpng-dev \
        curl zip unzip libtool swig zlib1g-dev pkg-config git wget xz-utils \
        python-numpy python-pip python-mock \
        python3-numpy python3-pip python3-mock python-future \
        libpython-dev libpython-all-dev libpython3-dev libpython3-all-dev \
        libpython-dev:armhf libpython-all-dev:armhf libpython3-dev:armhf libpython3-all-dev:armhf \
        libpython-dev:arm64 libpython-all-dev:arm64 libpython3-dev:arm64 libpython3-all-dev:arm64 g++ gcc

RUN pip install -U --user keras_applications==1.0.5 --no-deps \
    && pip install -U --user keras_preprocessing==1.0.3 --no-deps \
    && pip3 install -U --user keras_applications==1.0.5 --no-deps \
    && pip3 install -U --user keras_preprocessing==1.0.3 --no-deps \
    && ldconfig

RUN /bin/bash -c "update-alternatives --install /usr/bin/python python /usr/bin/python2 100" \
    && /bin/bash -c "update-alternatives --install /usr/bin/python python /usr/bin/python3 150"

WORKDIR /root
RUN git clone https://github.com/lhelontra/tensorflow-on-arm/

WORKDIR /root/tensorflow-on-arm/build_tensorflow/
RUN git checkout v2.0.0
CMD ["/bin/bash"]
