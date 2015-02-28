# Dockerfile for cpp-ethereum
Dockerfile to install latest package from ppa:ethereum/ethereum-dev

    docker build -t consensys/cpp-ethereum < Dockerfile

Connect to the test net

    docker run -i consensys/cpp-ethereum -m off -o peer -x 256 --remote poc-8.ethdev.com

To start ethereum-cli via docker container based on a phusion docker image and json rpc port mapped from 8080 inside docker to 8383 on your host (mapped to 8383 as 8080 is usually already used):

    docker run -p 8383:8080 -i afdudley/cpp-ethereum:pbi -j -m off -o peer -x 256 --remote poc-8.ethdev.com 

On Mac, if you are using boot2docker, run boot2docker ip, as [described in this tutorial](http://webiphany.com/technology/2014/06/12/what-ip-do-i-access-when-using-docker-and-boot2docker.html)
On my machine it returns 192.168.59.103

Test JSON-RPC using this IP and port 8383

    curl -X POST --data '{"jsonrpc":"2.0","method":"web3_sha3","params":["0x68656c6c6f20776f726c64"],"id":64}' http://192.168.59.103:8383

You should get something like this:
    {"id":64,"jsonrpc":"2.0","result":"0x47173285a8d7341e5e972fc677286384f802f8ef42a5ec5f03bbfa254cb01fad"}



