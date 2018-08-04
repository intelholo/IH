What is IH?
-------------

IH is a decentralized blockchain project built on Bitcoin's UTXO model, with support for Ethereum Virtual Machine based smart contracts, and secured by a proof of stake consensus model. It achieves this through the revolutionary Account Abstraction Layer which allows the EVM to communicate with IH's Bitcoin-like UTXO blockchain. For more general information about IH as well as links to join our community, go to https://IH.org

Welcome to the IH Ignition Main Network. This is the main network where the tokens hold value and should be guarded very carefully. If you are testing the network, or developing unstable software on IH, we highly recommend using either testnet or regtest mode. 

The major features of the IH network include:

1. Compatibility with the Ethereum Virtual Machine, which allows for compatibility with most existing Solidity based smart contracts. No special solidity compiler is required to deploy your smart contract to IH. 
2. A Proof of Stake consensus system which is optimized for IH's contract model. Any user can stake and help to secure the network. There is no voting, master nodes, or minimum amount required. There have been transactions as small as 2 IH that have created blocks in the past. 
3. The Decentralized Governance Protocol is completely implemented and functional, which allows certain network parameters to be modified without a fork or other network disruption. This currently controls parameters like block size, gas prices, etc. 
4. Uses the UTXO transaction model and is compatible with Bitcoin, allowing for existing tooling and workflows to be used with IH. This allows for the infamous SPV protocol to be used which is ideal for light wallets on mobile phones and IoT devices.

Note: IH Core is considered beta software. We make no warranties or guarantees of its security or stability.

IH Documentation and Usage Resources
---------------

These are some resources that might be helpful in understanding IH. Note that the unofficial documents are not created by the IH team.

Basic usage resources:

* [Official IH Usage Guide](https://github.com/IHproject/IH/wiki/IH-Wallet-Tutorial)
* [Unofficial IH staking tutorial](https://steemit.com/IH/@cryptominder/IH-staking-tutorial-using-IH-qt)
* [Unofficial IH staking tutorial on Raspberry Pi](https://steemit.com/IH/@cryptominder/IH-staking-tutorial-using-IHd-on-a-raspberry-pi-3)
* [Unofficial guide for keeping your wallet safe](https://steemit.com/IH/@cryptominder/encrypting-backing-up-and-restoring-your-IH-wallet)
* [Block explorer](https://explorer.IH.org)
* [Unofficial block explorer](https://IHexplorer.io/)
* [Unofficial Raspberry Pi Web UI](https://github.com/rpiwalletui/IH-ui)

Development resources:

* [Deploying a custom token to IH](https://blog.IH.org/IH-custom-token-walkthrough-467d725fa27d)
* [Early example faucet contract](http://earlz.net/view/2017/06/30/2144/the-IH-sparknet-faucet)
* [Unofficial IH Hello World tutorial](https://steemit.com/IH/@cryptominder/quantum-IH-blockchain-developer-tutorial-hello-world)
* [IH Book - A Developer's Guide To IH](https://github.com/IHproject/IHbook)

General Info about IH:

* [Mainnet event AMA](https://www.reddit.com/r/IH/comments/6zs8t0/official_IH_ama_thread_starts_at_10pm_beijing/)
* [IH's PoS vs CASPER](https://www.reddit.com/r/IH/comments/788oa5/IHs_pos_vs_casper_and_the_nothingatstake_problem/)
* [Technical article explaining IH's PoS model in depth](http://earlz.net/view/2017/07/27/1904/the-missing-explanation-of-proof-of-stake-version)
* [Unofficial What is IH article](https://storeofvalue.github.io/posts/what-is-IH-without-the-bullshit/)

Developer's Tools
-----------------

* Smart contract deployment tool
  * https://github.com/IHproject/solar
* DApp JavaScript Library
  * https://github.com/IHproject/IHjs
* A toolkit for building IH light wallets
  * https://github.com/IHproject/IHjs-wallet
* CORS IHd RPC proxy for DApp
  * https://github.com/IHproject/IHportal
* Docker images for running IH services
  * https://github.com/IHproject/IH-docker
* HTTP API that powers the block explorer and the IH web wallet
  * https://github.com/IHproject/insight-api


What is IH Core?
------------------

IH Core is our primary mainnet wallet. It implements a full node and is capable of storing, validating, and distributing all history of the IH network. IH Core is considered the reference implementation for the IH network. 

IH Core currently implements the following:

* Sending/Receiving IH
* Sending/Receiving QRC20 tokens on the IH network
* Staking and creating blocks for the IH network
* Creating and interacting with smart contracts
* Running a full node for distributing the blockchain to other users
* "Prune" mode, which minimizes disk usage
* Regtest mode, which enables developers to very quickly build their own private IH network for Dapp testing
* Compatibility with the Bitcoin Core set of RPC commands and APIs

Alternative Wallets
-------------------

IH Core uses a full node model, and thus requires downloading the entire blockchain. If you do not need the entire blockchain, and do not intend on developing smart contracts, it may be more ideal to use an alternative wallet such as one of our light wallets that can be synchronized in a matter of seconds. 

### IH Electrum

A light wallet that supports the Ledger hardware wallet and is based on the well known Electrum wallet software. 

Download: https://github.com/IHproject/IH-electrum/releases

### iOS and Android Wallets

These wallets run on mobile devices and synchronize quickly. 

Android Download: https://play.google.com/store/apps/details?id=org.IH.wallet

iOS Download: https://github.com/IHproject/IH-ios (open source, we are still working with Apple to get approval for their app store)

### Ledger Chrome Wallet

This light wallet runs in your Chrome browser as a browser extension. This wallet requires a Ledger device to use.

How to install: https://ledger.zendesk.com/hc/en-us/articles/115003776913-How-to-install-and-use-IH-with-Ledger


Building IH Core
----------

### Build on Ubuntu

    This is a quick start script for compiling IH on  Ubuntu


    sudo apt-get install build-essential libtool autotools-dev automake pkg-config libssl-dev libevent-dev bsdmainutils git cmake libboost-all-dev
    sudo apt-get install software-properties-common
    sudo add-apt-repository ppa:bitcoin/bitcoin
    sudo apt-get update
    sudo apt-get install libdb4.8-dev libdb4.8++-dev

    # If you want to build the Qt GUI:
    sudo apt-get install libqt5gui5 libqt5core5a libqt5dbus5 qttools5-dev qttools5-dev-tools libprotobuf-dev protobuf-compiler qrencode

    git clone https://github.com/IHproject/IH --recursive
    cd IH

    # Note autogen will prompt to install some more dependencies if needed
    ./autogen.sh
    ./configure 
    make -j2
    
### Build on CentOS

Here is a brief description for compiling IH on CentOS, for more details please refer to [the specific document](https://github.com/IHproject/IH/blob/master/doc/build-unix.md)

    # Compiling boost manually
    sudo yum install python-devel bzip2-devel
    git clone https://github.com/boostorg/boost.git
    cd boost
    git checkout boost-1.66.0
    git submodule update --init --recursive
    ./bootstrap.sh --prefix=/usr --libdir=/usr/lib64
    ./b2 headers
    sudo ./b2 -j4 install
    
    # Installing Dependencies for IH
    sudo yum install epel-release
    sudo yum install libtool libdb4-cxx-devel openssl-devel libevent-devel
    
    # If you want to build the Qt GUI:
    sudo yum install qt5-qttools-devel protobuf-devel qrencode-devel
    
    # Building IH
    git clone --recursive https://github.com/IHproject/IH.git
    cd IH
    ./autogen.sh
    ./configure
    make -j4

### Build on OSX

The commands in this guide should be executed in a Terminal application.
The built-in one is located in `/Applications/Utilities/Terminal.app`.

#### Preparation

Install the OS X command line tools:

`xcode-select --install`

When the popup appears, click `Install`.

Then install [Homebrew](https://brew.sh).

#### Dependencies

    brew install cmake automake berkeley-db4 libtool boost --c++11 --without-single --without-static miniupnpc openssl pkg-config protobuf qt5 libevent imagemagick --with-librsvg qrencode

NOTE: Building with Qt4 is still supported, however, could result in a broken UI. Building with Qt5 is recommended.

#### Build IH Core

1. Clone the IH source code and cd into `IH`

        git clone --recursive https://github.com/IHproject/IH.git
        cd IH

2.  Build IH-core:

    Configure and build the headless IH binaries as well as the GUI (if Qt is found).

    You can disable the GUI build by passing `--without-gui` to configure.

        ./autogen.sh
        ./configure
        make

3.  It is recommended to build and run the unit tests:

        make check

### Run

Then you can either run the command-line daemon using `src/IHd` and `src/IH-cli`, or you can run the Qt GUI using `src/qt/IH-qt`

For in-depth description of Sparknet and how to use IH for interacting with contracts, please see [sparknet-guide](doc/sparknet-guide.md).

License
-------

IH is GPLv3 licensed.

Development Process
-------------------

The `master` branch is regularly built and tested, but is not guaranteed to be
completely stable. [Tags](https://github.com/IHproject/IH/tags) are created
regularly to indicate new official, stable release versions of IH.

The contribution workflow is described in [CONTRIBUTING.md](CONTRIBUTING.md).

Developer IRC can be found on Freenode at #IH-dev.

Testing
-------

Testing and code review is the bottleneck for development; we get more pull
requests than we can review and test on short notice. Please be patient and help out by testing
other people's pull requests, and remember this is a security-critical project where any mistake might cost people
lots of money.

### Automated Testing

Developers are strongly encouraged to write [unit tests](src/test/README.md) for new code, and to
submit new unit tests for old code. Unit tests can be compiled and run
(assuming they weren't disabled in configure) with: `make check`. Further details on running
and extending unit tests can be found in [/src/test/README.md](/src/test/README.md).

There are also [regression and integration tests](/qa) of the RPC interface, written
in Python, that are run automatically on the build server.
These tests can be run (if the [test dependencies](/qa) are installed) with: `qa/pull-tester/rpc-tests.py`

### Manual Quality Assurance (QA) Testing

Changes should be tested by somebody other than the developer who wrote the
code. This is especially important for large or high-risk changes. It is useful
to add a test plan to the pull request description if testing the changes is
not straightforward.

