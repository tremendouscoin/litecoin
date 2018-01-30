Cheat sheet for running a tremendouscoind (node daemon) after logging in to a brand new AWS Ubuntu 14.04 instance)
====================

####For real / definitive instructions related to this:
See Litecoin's regular [UNIX BUILD NOTES](/doc/build-unix.md). Seriously!

#### OK Then.
First:

```
sudo apt-get update
sudo apt-get install build-essential libtool autotools-dev automake pkg-config libssl-dev libevent-dev bsdmainutils
sudo apt-get install libboost-system-dev libboost-filesystem-dev libboost-chrono-dev libboost-program-options-dev libboost-test-dev libboost-thread-dev
sudo apt-get install software-properties-common
sudo add-apt-repository ppa:bitcoin/bitcoin
sudo apt-get install git
```

Then

```
sudo -i
```

Then:


```
git clone https://github.com/tremendouscoin/tremendouscoin.git
cd tremendouscoin/
```

Depending on which branch, you may or may not want to do something like:
```
git checkout dev
git status
```

Then:
```
./autogen.sh

```

I've found that the upcoming ./configure command will not work unless you either
a) run it as ```./configure --without-wallet``` or b) first, run:

```
wget http://download.oracle.com/berkeley-db/db-4.8.30.NC.tar.gz
sudo apt-get install libdb4.8-dev libdb4.8++-dev
```

Now you can do:
```
./configure
make
```

Then:
```
cd src
./tremendouscoind &
```

To make sure your wallet will be able to connect to your daemon, use your AWS EC2 Management Console
to edit the instance's corresponding Security Group's Inbound settings, for example adding:
```
Type: Custom TCP Rule
Protocol: TCP
Port range: 10347
Source: 0.0.0.0/0
```