To build on a clear Linux server (Ubuntu 16.04)
===============================================

The build script will instruct on process to install dependecies, retrieve latest source and perform a full build for Linux

1. Prepare dependencies
======================

sudo add-apt-repository ppa:bitcoin/bitcoin
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
sudo apt-get install autogen curl git nano software-properties-common build-essential libtool autotools-dev automake pkg-config bsdmainutils
sudo apt-get install libssl-dev libevent-dev libboost-all-dev libdb4.8-dev libdb4.8++-dev libminiupnpc-dev libzmq5-dev libqrencode-dev
sudo apt-get install libqt5gui5 libqt5core5a libqt5dbus5 qttools5-dev qttools5-dev-tools libprotobuf-dev protobuf-compiler

2. Get latest source from Git
=============================

git clone https://github.com/mobitglobal/mobitglobal build

3. Perform build of source
==========================

cd build
chmod 764 autogen.sh
./autogen.sh
./configure
make
cd ..
cp build/src/mobitglobald .
cp build/src/mobitglobal-cli .
cp build/src/mobitglobal-tx .
cp build/src/qt/mobitglobal-qt .

4. Remove debug symbols (optional, improves performance)
========================================================

strip mobitglobald
strip mobitglobal-cli
strip mobitglobal-qt
strip mobitglobal-tx

5. Tidy up
==========
rm -rf build