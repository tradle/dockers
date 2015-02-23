# Dockerfile for cpp-ethereum
Dockerfile to install latest package from ppa:ethereum/ethereum-dev

    docker build -t consensys/cpp-ethereum < Dockerfile

Connect to the test net

    docker run -i consensys/cpp-ethereum -m off -o peer -x 256 --remote poc-8.ethdev.com
