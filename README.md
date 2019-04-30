wget https://drive.google.com/open?id=1oH8eIPy_964HT3uuQYEhd5rRcqNHSuzZ

tar -xvzf private-tangle-docker.gz

sudo apt-get install pkg-config zip g++ zlib1g-dev unzip python

cd private-tangle

chmod +x bazel-0.18.0-installer-linux-x86_64.sh

sudo ./bazel-0.18.0-installer-linux-x86_64.sh

sudo apt install apt-transport-https ca-certificates curl software-properties-common

curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -

sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu bionic stable"

sudo apt update

sudo apt install docker-ce

sudo add-apt-repository universe

sudo apt install jq

cd compass/docs/private-tangle

sudo ./02_run_iri.sh

sudo docker run -d --name iota-node iotaledger/iri:latest --testnet --remote --testnet-coordinator 99CSYEB9OALOWHMTKEDONWWQXDQZWBOMFPBQJETIAVBZNHAMFWPZTWFPTQAWLIDO9T9MLQYFX9FNTLTKR --neighbors udp://172.17.0.1:14600 --mwm 9

sudo ./03_run_coordinator.sh -broadcast -bootstrap

cd ../../../iritop
python iritop.py

cd ../iota-2.5.7
./iota
