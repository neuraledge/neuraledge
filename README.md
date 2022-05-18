# download required binaries
curl -sSL http://bit.ly/2ysbOFE | bash -s -- 1.4.4 1.4.4 0.4.22

# create bft orderer and gen tool
make orderer-docker

make configtxgen

copy generated 'orderer' and 'configtxgen' to bft/bin folder

# other envirnment setting
- GO installation

download go1.15

mkdir ${HOME}/gopath

mv go ${HOME}/gopath

chmod -R 777 go

mkdir -p ${HOME}/gopath/src/github.com/hyperledger/

gedit ~/.bashrc

add the following at the end:

export PATH=$PATH:$HOME/go/bin

export GOPATH=$HOME/gopath

export GOROOT=$HOME/go

export GOBIN=$GOROOT/bin

export PATH=$HOME/gopath/src/github.com/hyperledger/fabric/bft/bin:$PATH

Update:

source ~/.bashrc

View:

go env

- GO package installation:

mkdir -p $GOPATH/src/golang/x

cd $GOPATH/src/golang/x

chmod -R 777 golang

- Download the required package:

go env -w GO111MODULE=on

go mod init

git clone https://github.com/golang/tools.git

go get golang/x/tools/go/packages

go mod vendor

- nodejs v8
- docker

# build bft network
- start network with couchdb
in bft/pbft-network folder

./byfn.sh up -a -s couchdb

- close network
./byfn.sh down

# run application to access ledger
in /bft/client

node enrollAdmin.js
node registerUser.js 

