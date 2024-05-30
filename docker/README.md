# Purpose
This directory contains a [Dockerfile](Dockerfile) that adds the [oqs-provider](https://github.com/open-quantum-safe/oqs-provider) to OpenSSL.
This allows OpenSSL to use quantum safe algorithms within the standard operations.

# Quick Start

[Install Docker](https://docs.docker.com/install) and run the following commands:

1. Run
```
    docker build -t oqs-openssl-img . 
```
to build a new docker image that is called `oqs-openssl-img`.

2. Start the container using the following command:
```
docker run --name oqs-openssl -dit --rm oqs-openssl-img
```
3. Connect to the container using:
```
docker exec -it oqs-openssl bash
```
4. Confirm that the installation was successfull using:
```
openssl list -signature-algorithms -provider oqsprovider
```
which should list all algorithms that have been made available through oqs-provider.

# Next steps

Additional information for usage can be found at https://github.com/open-quantum-safe/oqs-provider/blob/main/USAGE.md#activation
