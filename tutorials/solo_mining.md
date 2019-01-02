# Solo Mining

Kevacoin can be mined through CPU, AMD and Nvidia GPU. If you want to mine Kevacoin using CPU, it is highly recommended that your CPU supports AES-NI instrcution as the Cryptonight hash algorithm performs much faster using the instruction. Most modern Intel Core <sup>TM</sup> and AMD CPUs support the AES-NI instruction.

## Overview

You need to run the following programs in order to do solo-mining:

1. Kevacoin client.
2. Customized NOMP(Node Open Mining Portal) with Kevacoin support.
3. One of the miners (CPU, Nvidia or AMD).

## Setup and run Kevacoin client

Download the Kevacoin client from [https://kevacoin.org](https://kevacoin.org), choose the specific client for your platform. Alternatively, you can also build the client from the source (<https://github.com/kevacoin-project/kevacoin>). When building from the source, make sure to use the current release tag.

Before running the client, add a file `kevacoin.conf` to the Kevacoin data directory with the following content:

<pre>
rpcuser=yourusername
rpcpassword=yourpassowrd
rpcport=19332
</pre>

Make sure to replace `yourusername` and `yourpassword` with your own user name and secure password.

The table below lists the Kevacoin data directory for different platforms.

| OS        | Location |
|---        | ---      |
|Linux      | ~/.kevacoin |
|Windows    | C:\Users\YourUserName\Appdata\Roaming\Kevacoin |
|macOS      | ~/Library/Application Support/Kevacoin |

Once the `kevacoin.conf` file is added, start the Kevacoin client:

<pre>
kevacoind
</pre>

If you don't have a Kevacoin address yet, generate a new one:

<pre>
kevacoin-cli getnewaddress

VFgAsW4SP7GtMwb4Uvf9Z6nZ4j8qWbs5fV
</pre>

Kevacoin address always starts with a prefix 'V'.

## Setup and run NOMP

NOMP requires Node.js and Redis. So before running NOMP, you need to install both.

### Install Node.js

Download Node.js from <https://nodejs.org/en/download/> and follow the instructions.

### Install Redis

For Linux, follow the instructions: <https://redis.io/topics/quickstart>

For Windows, download the installer from <https://github.com/MicrosoftArchive/redis/releases> and run the installer.

For macOS, follow the instructions: <https://medium.com/@petehouston/install-and-config-redis-on-mac-os-x-via-homebrew-eb8df9a4f298>


### Install NOMP

Once Node.js and Redis are installed, we are ready to install NOMP:

<pre>
git clone https://github.com/kevacoin-project/node-open-mining-portal.git nomp
cd nomp
npm update
</pre>

NOMP needs two configuration files, one for the general configuration and the other for the pool configuration.

Kevacoin NOMP comes with an example general configuration file `config_keva_solo.json`, just rename it to `config.json`.

The pool configuration file is under `pool_configs/kevacoin.json`. Make sure to make the following changes:

1. Change the address to point to your wallet address.
2. Replace `yourusername` and `yourpassword` with your own user name and secure password, as specified in your Kevacoin client's `kevacoin.conf` file.

Run NOMP:

<pre>
node init.js
</pre>


## Run the miner

Download and install the miner according to your platform from <https://kevacoin.org/mining.html>.

### Nvidia GPU miner

To run the Nvidia GPU miner:

<pre>
ccminer -a keva -o stratum+tcp://127.0.0.1:3032 -u "your address" -p x
</pre>

### AMD GPU miner

AMD GPU miner requires a configuration file `config.json`. You should configure the "threads" section to optimize for your GPU. The config file has the same format as XMRig-AMD (<https://github.com/xmrig/xmrig-amd>) and can be configured in the same way. Note that the "pools" section in the config file is not used.

To run the AMD GPU miner:

<pre>
ccminer -a keva -o stratum+tcp://127.0.0.1:3032 -u "your address" -p x
</pre>

### CPU miner

CPU miner requires a configuration file `config.json`. You should change settings in the file to optimize for your CPU. The config file has the same format as XMRig-AMD (<https://github.com/xmrig/xmrig>) and can be configured in the same way. Note that the "pools" section in the config file is not used.

To run the CPU miner:

<pre>
ccminer -a keva -o stratum+tcp://127.0.0.1:3032 -u "your address" -p x
</pre>










