
# Dtor -  deviation from a direct course! ↪️

Copyright (c) 2020 Dtor Project.   
Copyright (c) Props to the Wownero community ;)  
Copyright (c) 2014-2019 The Monero Project.   
Portions Copyright (c) 2012-2013 The Cryptonote developers.



## Resources

- Web: [dtor.org](http://dtor.org)
- Twitter: [_dt0r](https://twitter.com/_dt0r)
- Mail: [dtor-dev@protonmail.com](mailto:dtor-dev@protonmail.com)
- GitHub: [https://github.com/Dtor-Project/dtor](https://github.com/Dtor-Project/dtor)
- Discord: [https://discord.gg/m54wz8p} (https://discord.gg/m54wz8p)

Blockchain Explorers
- http://explorer.dtor.org/
- http://dtorexplorer.2xminer.com/

Free Public Nodes
- TBD
- .onion:23468
- :23468 (US)
- :23468 (CAN)
- :23468 (KP)
- :23468 (UK)

Tor Peers
- COMMING SOON?
- .onion
- .onion

## Introduction

Dtor is an experimental privacy-centric coin that launched on August 1, 2020 with no pre-mine, stealth-mine or ICO. Dtor has a maximum supply of around 18.4 million with a slow and steady emission over 50 years. It is a copy and paste of Monero and Cryptonote, but with its own genesis block, and direction of travel deviating from a direct course. There is no degradation of privacy due to ring signatures using different participants for the same tx outputs on opposing forks.

## Scheduled software upgrades

Dtor uses a fixed-schedule software upgrade (hard fork) mechanism to implement new features. This means that users of Dtor (end users and service providers) should run current versions and upgrade their software on a regular schedule. The required software for these upgrades will be available prior to the scheduled date. Please check the repository prior to this date for the proper Dtor software version. Below is the historical schedule and the projected schedule for the next upgrade.
Dates are provided in the format YYYY-MM-DD. 

| Software upgrade block height | Date       | Release Name | Minimum Dtor version | Recommended Dtor version | Details                                                                            |  
| ------------------------------ | -----------| ----------------- | ---------------------- | -------------------------- | ---------------------------------------------------------------------------------- |
| 1                              | 2020-08-01 | Runone                | v0.1.0.0               | v0.1.0.0                  | Cryptonight variant 2, LWMA v2, ringsize = 22, MMS sorted inputs


X's indicate that these details have not been determined as of commit date.

\* indicates estimate as of commit date

## Release staging and Contributing

**Anyone is welcome to contribute to Dtor's codebase!** 

If you have a fix or code change, feel free to submit it as a pull request. Ahead of a scheduled software upgrade, a development branch will be created with the new release version tag. Pull requests that address bugs should be made to Master. Pull requests that require review and testing (generally, optimizations and new features) should be made to the development branch. All pull requests will be considered safe until the US dollar valuation of 1 Dtor equals $1000. After this valuation has been reached, more research will be needed to introduce experimental cryptography and/or code into the codebase.  

## Installing from a package

Packages are available for

TBD

## Building from Source  
'only tested Ubuntu 18.04. 07-2020'

* Arch Linux/Manjaro

        sudo pacman -Syu && sudo pacman -S base-devel cmake boost openssl zeromq libpgm unbound libsodium git
        git clone https://github.com/Dtor-Project/dtor
        cd dtor
        make -j2


* Debian/Ubuntu

        sudo apt update && sudo apt install build-essential cmake pkg-config libboost-all-dev libssl-dev libzmq3-dev libunbound-dev libsodium-dev libpgm-dev git
        git clone https://github.com/Dtor-Project/dtor
        cd dtor
        make -j2


## Running Binaries

The build places the binary in `bin/` sub-directory within the build directory
from which cmake was invoked (repository root by default). To run in
foreground:

    ./bin/dtord

To list all available options, run `./bin/dtord --help`.  Options can be
specified either on the command line or in a configuration file passed by the
`--config-file` argument.  To specify an option in the configuration file, add
a line with the syntax `argumentname=value`, where `argumentname` is the name
of the argument without the leading dashes, for example `log-level=1`.

To run in background:

    ./bin/dtord --log-file dtord.log --detach

To run as a systemd service, copy
[dtord.service](utils/systemd/dtord.service) to `/etc/systemd/system/` and
[dtord.conf](utils/conf/dtord.conf) to `/etc/`. The [example
service](utils/systemd/dtord.service) assumes that the user `dtor` exists
and its home is the data directory specified in the [example
config](utils/conf/dtord.conf).

Once node is synced to network, run the CLI wallet by entering:

    ./bin/dtor-wallet-cli

Type `help` in CLI wallet to see standard commands (for advanced options, type `help_advanced`).

## Tor Anonymity Network

* Install [Tor Browser](https://www.torproject.org/download/)
* Open `torrc` file in a text editor ([installation directory]/Browser/TorBrowser/Data/Tor/torrc) and add hidden service information as follows:

```
HiddenServiceDir [installation directory]/Browser/TorBrowser/Data/Tor/dtor_node
HiddenServiceVersion 3
HiddenServicePort 44568 127.0.0.1:44568
```
* Save `torrc` file and restart Tor Browser (keep open)
* Change directory to the `dtor_node` folder, open `hostname` file, and copy your node's ".onion" address
* Start dtord with the following parameters:

```
./dtord --tx-proxy tor,127.0.0.1:9150,10 --add-peer xxxxxx.onion:44568 --anonymous-inbound YOUR_NODE_ADDRESS.onion:44568,127.0.0.1:44568,25
```

### Access remote Tor node from CLI wallet

```
./dtor-wallet-cli --proxy 127.0.0.1:9150 --daemon-address dtorxxxxx.onion:34568
```

Use port `9050` instead of `9150` if you installed Tor as a standalone daemon. For more information, check out [ANONYMITY_NETWORKS](https://github.com/Dtor-Project/dtor/src/branch/master/ANONYMITY_NETWORKS.md).

## Donating to Dtor District Project

Developers are volunteers doing this mostly for shits and giggles. If you would like to support our shenanigans and stimulant addictions, please consider donating 

Donations may also be sent to: 

XMR: `45cg5muo2tTWCxWy2iRcMsSsLUCjx3zQYGGwWuAhDTUWMUGgY2U5nbb252SGDFLm2JjCyVCsoypCNfBw3WiN2nduKp4c2Sw`

BTC: `3JLkCYa8UcBn1TR9sVbPZXz1PCcdo3kupP`
