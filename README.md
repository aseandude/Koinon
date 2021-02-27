# What is Koin ?
koinon is the complete solution for payments, serving the needs of both merchants and consumers. Our “OmniChannel” payment system is a single solution enabling merchants to seamlessly accept crypto, mobile, and card payments – all with a single piece of hardware. Koinon’s multi-currency eWallet and linked debit card give consumers a convenient way of making transactions and sending funds using their stored tokens.

![KOINON Logo](https://koinon.io/wp-content/uploads/2018/12/Koinon_Brandbook-02-Copy.jpg "Koinon Logo")

# Development Resources
- Official Website: https://koinon.io/
- Komodo Web: https://komodoplatform.com/
- Forum: https://forum.komodoplatform.com/
- Knowledgebase & How-to: https://komodoplatform.atlassian.net/wiki/spaces/KPSD/pages
- API references: http://docs.komodoplatform.com/
- Blog: http://blog.komodoplatform.com/
- Whitepaper: https://koinon.io/wp-content/uploads/2018/12/Koinon-WP-Year-End-2018.pdf
- Komodo Platform public material: Komodo Platform public material

# Komodo Platform Technologies
- Delayed Proof of Work (dPoW) - Additional security layer and Komodos own consensus algorithm.
- zk-SNARKs - Komodo Platform's privacy technology for shielded transactions
- Tokens/Assets Technology - create "colored coins" on the Komodo Platform and use them as a layer for securites
- Reward API - Komodo CC technology for securities
- CC - Crypto Conditions to realize "smart contract" logic on top of the Komodo Platform
- Jumblr - Decentralized tumbler for KMD and other cryptocurrencies
- Assetchains - Create your own Blockchain that inherits all Komodo Platform functionalities and blockchain interoperability
- Pegged Assets - Chains that maintain a peg to fiat currencies
- Peerchains - Scalability solution where sibling chains form a network of blockchains
- More in depth covered here
- Also note you receive 5% APR on your holdings. See this article for more details

# Koin Tech Specification
- Coin Ticker: KOIN
- Coin Name: Koinon Coin
- Max Supply: 125M KOIN
- Block Time: 60 seconds
- Block Reward: 0.001 KOIN
- Mining Algorithm: Equihas
- rpcport: 10702
- p2pport: 10701
- pubtype: 48
- taddr: 0
- p2shtype: 50
- wiftype: 176
- txfee: 1000000
- active: 1


# BUILD NOTES

## Notes
The dev branch is considered the bleeding edge codebase while the master-branch is considered tested (unit tests, runtime tests, functionality). At no point of time do the Koin developers take any responsbility for any damage out of the usage of this software. Koin builds for all operating systems out of the same codebase. Follow the OS specific instructions from below.

## Dependencies
```
 sudo apt-get install build-essential pkg-config libc6-dev m4 g++-multilib autoconf libtool ncurses-dev unzip git python python-zmq zlib1g-dev wget libcurl4-gnutls-dev bsdmainutils automake curl
 ```

## Linux
```
git clone https://github.com/aseandude/Koinon --branch master --single-branch
cd Koinon
./zcutil/fetch-params.sh
# -j8 = using 8 threads for the compilation - replace 8 with number of threads you want to use
./zcutil/build.sh -j8
#This can take some time.
```

## OSX
```
# Install brew
/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
# Install Xcode, opens a pop-up window to install CLT without installing the entire Xcode package
xcode-select --install 
# Update brew and install dependencies
brew update
brew upgrade
brew tap discoteq/discoteq; brew install flock
brew install autoconf autogen automake
brew update && brew install gcc@8
brew install binutils
brew install protobuf
brew install coreutils
brew install wget
# Clone the Koinon repo
git clone https://github.com/aseandude/Koinon --branch master --single-branch
# Change master branch to other branch you wish to compile
cd Koinon
./zcutil/fetch-params.sh
# -j8 = using 8 threads for the compilation - replace 8 with number of threads you want to use
./zcutil/build-mac.sh -j8
# This can take some time.

```

## Windows
Use a debian cross-compilation setup with mingw for windows and run:
```
sudo apt-get install build-essential pkg-config libc6-dev m4 g++-multilib autoconf libtool ncurses-dev unzip git python python-zmq zlib1g-dev wget libcurl4-gnutls-dev bsdmainutils automake curl cmake mingw-w64
curl https://sh.rustup.rs -sSf | sh
source $HOME/.cargo/env
rustup target add x86_64-pc-windows-gnu
git clone https://github.com/aseandude/Koinon --branch master --single-branch
cd Koinon
./zcutil/fetch-params.sh
# -j8 = using 8 threads for the compilation - replace 8 with number of threads you want to use
./zcutil/build-win.sh -j8
#This can take some time.
```

## Create KOIN.conf
```
mkdir -p ~/.komodo/KOIN
cd ~/.komodo/KOIN
touch KOIN.conf

#Add the following lines to the KOIN.conf file:
rpcuser=yourrpcusername
rpcpassword=yoursecurerpcpassword
rpcbind=127.0.0.1
txindex=1
server=1
daemon=1
addnode=18.136.218.202
addnode=18.140.207.130
addnode=18.140.174.120
```

## Start deamon
```
~/Koinon/src/komodod -ac_name=KOIN -ac_supply=125000000 -gen &
```
It will start in background. Please wait sometime to full synchronize with other network. Once your node fully sync test foloowing command to check status
Meanwhile you can check debug.log file in ~/.komodo/KOIN/debug.log if any error

```
~/Koinon/src/komodo-cli -ac_name=KOIN getinfo
```
It will show you following output
```
{
  "version": 2001526,
  "protocolversion": 170007,
  "KMDversion": "0.3.3b",
  "notarized": 54274,
  "prevMoMheight": 54274,
  "notarizedhash": "05486d028ec57a77c656760128b2c9ff21c40548f77914a11764c03641a422b4",
  "notarizedtxid": "e0bd6865a74e831b77a5f37261c1d4a55892b04d90d11ad418a446985cf6e9d6",
  "notarizedtxid_height": "mempool",
  "KMDnotarized_height": 0,
  "notarized_confirms": 0,
  "walletversion": 60000,
  "balance": 1.34314113,
  "blocks": 54452,
  "longestchain": 54452,
  "timeoffset": 0,
  "tiptime": 1569366013,
  "connections": 26,
  "proxy": "",
  "difficulty": 1,
  "testnet": false,
  "keypoololdest": 1567798301,
  "keypoolsize": 101,
  "paytxfee": 0.00000000,
  "relayfee": 0.00000100,
  "errors": "",
  "name": "KOIN",
  "sapling": 266,
  "p2pport": 10701,
  "rpcport": 10702,
  "magic": -1235858314,
  "premine": 125000000
}

```
Wow!! You have successfully completed setup

Cheers
