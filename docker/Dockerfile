FROM ubuntu:latest as dev

RUN apt-get update && \
    apt-get upgrade -y && \
    apt-get install -y openssl libssl-dev git pkg-config

# Install liboqs dependencies

RUN apt install -y astyle cmake gcc ninja-build libssl-dev python3-pytest python3-pytest-xdist unzip xsltproc doxygen graphviz python3-yaml valgrind

WORKDIR /opt
RUN git clone -b main https://github.com/open-quantum-safe/liboqs.git
RUN git clone -b main https://github.com/open-quantum-safe/oqs-provider.git
WORKDIR /opt/liboqs
RUN cmake -GNinja
RUN ninja install

WORKDIR /opt/oqs-provider
RUN cmake -S . -B _build && cmake --build _build && ctest --test-dir _build && cmake --install _build
RUN mv _build/lib/oqsprovider.so /usr/lib/x86_64-linux-gnu/ossl-modules