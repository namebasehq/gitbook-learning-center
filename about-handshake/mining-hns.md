---
description: A guide for mining Handshake coins with 6block
---

# Mining HNS

Handshake mining fees are currently \~0.1 HNS — at an exchange rate of 1 HNS = $0.10, this costs about a penny.

{% embed url="https://www.youtube.com/watch?v=vE0mfLMuocE&feature=emb_title" %}

{% hint style="info" %}
This tutorial video was created solely by Namer [skyinclude/](https://hns.to/skyinclude/)
{% endhint %}

## Handshake Blocks

### Block time

1 Handshake block time is = 10 minutes, which is the average amount of time it takes to mine the next Handshake block. That being said, in reality it's more likely for blocks to be mined in _less_ than 10 minutes because a block that takes particularly long would need to be balanced by many "fast" blocks. For example if we assume "fast" blocks take 9 minutes to mine (in reality it's totally random), a single "slow" block that takes 1 hour to mine would need to be balanced by _fifty_ "fast" blocks to average out to 10 minutes.

### Block limits

Each Handshake block has the following limits:

* [600 "updates"](https://github.com/handshake-org/hsd/blob/af86d4899791601d10212115c80a2f2136fdb004/lib/protocol/consensus.js#L200) which are `OPEN`, `UPDATE`, `TRANSFER` and `REVOKE` covenants
  * a sub-limit of [300 opens](https://github.com/handshake-org/hsd/blob/af86d4899791601d10212115c80a2f2136fdb004/lib/protocol/consensus.js#L192), which are just `OPEN`s. Note that these 300 opens are a subset of the 600 updates
* [600 "renewals"](https://github.com/handshake-org/hsd/blob/af86d4899791601d10212115c80a2f2136fdb004/lib/protocol/consensus.js#L208), which are `FINALIZE`, `REGISTER`, and `RENEW` covenants

## HS1 and HS1+ by Goldshell

{% hint style="info" %}
This guide was entirely created by Namer [tigs/](https://hns.to/tigs/)!
{% endhint %}

Hi Guys & Gals!

Just thought I should finally write something regarding how to configure and properly setup the Goldshell HS1+ for mining on a Windows machine!

WARNING!!! Please keep in mind, these instructions are ONLY for the HS1 and HS1+ devices manufactured by Goldshell. Under no circumstance should you ever follow this guide on any other ASIC miners or HNS Miners.

First of, probably best to grab some a few files from here and there to make this installation and setup much more breezier! The first thing you’re going to want to grab is the latest firmware version for your ASIC miner. This is terribly important as it’s the firmware usually which dictates the stability and longevity of your new hardware device. Not to mention that the more recent the firmware, the more likely that things will just “click” and work when it comes to that time.

[https://github.com/goldshellminer/HS1/tree/master/firmware](https://github.com/goldshellminer/HS1/tree/master/firmware) ← is the website to go to download the latest firmware for your device. As of this writing v0.0.4 was the latest.

### Windows Users Prerequisites:

Download STM32 serial driver [STSW\_STM32102\_V1.5.0.rar](https://github.com/goldshellminer/HS1/tree/master/miner/serial\_driver). Select your OS version driver to install.

#### Download supported miner softwares (two options):

Option1: Goldshell Miner version 1.0.4 or above: (Windows only)&#x20;

[https://github.com/goldshellminer/HS1/tree/master/miner](https://github.com/goldshellminer/HS1/tree/master/miner)

Option2: Handyminer CLI\&GUI (Windows, Linux, MacOs)

[https://github.com/HandyMiner/HandyMiner-Goldshell-CLI ](https://github.com/HandyMiner/HandyMiner-Goldshell-CLI)(Command Line Interface)

[https://github.com/HandyMiner/HandyMiner-Goldshell-GUI](https://github.com/HandyMiner/HandyMiner-Goldshell-GUI) (Graphical User Interface)

#### Connect the hardware in sequence

A. plug in the power cable.

B. Connect the HS1 or HS1-PLUS miner with the USB cable to the computer

[https://www.goldshell.com/2020/09/23/hs1%e3%80%81hs1-plus-firmware-update-2020-9-21/](https://www.goldshell.com/2020/09/23/hs1%E3%80%81hs1-plus-firmware-update-2020-9-21/) ← Updating your firmware is much recommended and can be achieved by following this guide here. Sorry for the broken english folks but the jist of it is this. Basically follow step 2 FIRST! Make sure the miner is in an idle state (still plugged into the power and computer of course and showing up as a blue box when clicked within the Goldshell software.) Click off, and after it has spun down, Click the box that is the second from the far right; It should say ‘Update Firmware’ if you hover the mouse over it for a second or two. One clicked, navigate to the HS1-Plus firmware file you downloaded earlier and let that install into the ASIC Miner.&#x20;

Now! This is where it comes down to personal preference which mining program you use; but myself? I prefer to use the GUI (Graphical User Interface) version of HandyMiner. Has never steered me wrong and I get quite a bit of juice out of it, reaching as high as 115GH/S rather than 105GH/S! This doesn’t happen to everyone though, I’ve tried mining on a myriad of computers and I can’t put my finger on what exactly makes them tick faster or at the advertised speed.

Speaking on behalf of the strength and stability that I myself have seen afforded to me through HandyMiner; I highly recommend using that. Plug the power into your ASIC, then the USB cable to the computer. Upon running HandyMiner it already knows the major pools being used for HNS mining making things a bit easier. Anyways; I happen to use Dxpool.com - because that happened to be what Goldshell recommended on their website. By all means, please choose the mining pool which you prefer; but try to stay on top of which sites are more popular than others and the total rewards they will tax. (In some cases 2-3%, others 4%)

Also I have set a auto-withdraw amount for the pool/site I mine for; making it very simple to leave the machine on 24/7 and still receiving a decent payout. I use https://bobwallet.io/ - A wallet dedicated purely for the use of Handshake and which lets you save your private key. That way I just keep the words safe and can sleep sound knowing my HNS won’t be gone if my username+password have been compromised.&#x20;

There’s alot more to this mining thing than it seems so PLEASE, come to me for any questions and I would be more than happy to help if I can!

Can reach me at tigs#2777 on Discord!

Happy Mining!

## 6miner <a href="#lets-get-started." id="lets-get-started."></a>

{% hint style="warning" %}
This section is outdated, if you have a mining tutorial please share it in the [Namer Community ](https://hns.to/community.nb/)and we'll update this page with yours!
{% endhint %}

### Let’s get started.

There are three main steps to get you ready to start mining HNS.&#x20;

1. [Register on Namebase to get your HNS wallet address](mining-hns.md#step-1:)
2. [Run 6block mining software](mining-hns.md#step-2:-run-6miner)
3. [Withdraw HNS to your HNS wallet address](mining-hns.md#step-3:-withdraw-to-your-hns-wallet-address)

### Step 1: Register on Namebase

The first part of this process is to create a Handshake wallet address. To do this, simply [create](https://www.namebase.io/register) your Namebase account and complete your registration.

After completing your registration, you will notice a \[Dashboard] tab at the top navigation. When you arrive at the Dashboard page, you will notice a card that will show your available HNS balance. At the bottom of the card, you’ll notice a string of numbers. This is your HNS wallet address. You can easily copy this by using the clipboard feature next to your wallet address. See screenshot below for reference.&#x20;

![Getting your wallet address](https://images.ctfassets.net/v3ez3dek3dk6/nL4gnWryoociAFJdl0YKG/830e91a1843bb31ad0c486f55eaa8a2d/Dashboard\_image.png?fit=pad\&w=720)

### Step 2: Run 6miner &#x20;

This step requires registering, installing and running a Handshake mining software. This walkthrough uses 6miner and the 6block mining pool.&#x20;

To start this process, register for 6block [here](https://6block.com/register) before Handshake mining for the wallet address configuration, worker and revenue monitoring and payment records checking.

The algorithm of Handshake is blake2b+sha3.

#### What is 6block?

6block is one of the first mining pools to be ready for the Handshake launch. 6block is built for performance and designed to be stable, fast and secure.

#### What is 6miner?&#x20;

6miner is a highly optimized miner for Handshake and it performs over 20% faster than HandyMiner on most GPUs tested. It is a direct competitor to HandyMiner, which is also a very good miner.&#x20;

Links to both miners are provided and we encourage people to test and decide which option will suit them best.&#x20;

### Install GPU Drivers&#x20;

In order to mine Handshake, you will need to have your GPU's drivers installed in your computer. 6miner works with both AMD and Nvidia cards, here's how to install the drivers:&#x20;

#### Nvidia GPU&#x20;

Here's a very good tutorial on how to install Nvidia Drivers on Ubuntu: [https://www.linuxbabe.com/ubuntu/install‐nvidia‐driver‐ubuntu‐18‐04 ](https://www.linuxbabe.com/ubuntu/install%E2%80%90nvidia%E2%80%90driver%E2%80%90ubuntu%E2%80%9018%E2%80%9004)

#### AMD GPU&#x20;

Here's the official AMD tutorial for installing amdgpu‐pro on Ubuntu and CentOS: [https://amdgpu‐install.readthedocs.io/en/latest/ ](https://xn--amdgpuinstall-gm6g.readthedocs.io/en/latest/)

For Ubuntu, please make sure to download from this link — Version 19.50 is recommended as it'll support up to the 5700XT (aprox 240mh hashrate): [https://drivers.amd.com/drivers/linux/19.50/amdgpu‐pro‐19.50‐967956‐ubuntu‐18.04.tar.xz ](https://drivers.amd.com/drivers/linux/19.50/amdgpu%E2%80%90pro%E2%80%9019.50%E2%80%90967956%E2%80%90ubuntu%E2%80%9018.04.tar.xz)

### Setting up 6 miner

1. Go to http://github.com/6block/6miner/releases&#x20;
2. Download the release file, currently: https://github.com/6block/6miner/releases/download/v0.0.1/6miner‐v0.0.1‐amd64‐ linux.tar.gz&#x20;
3. Open the terminal and decompress the file: tar -xpf 6miner-v0.0.1-amd64-linux.tar.gz&#x20;
4. Go inside the folder that was just created: cd 6miner-v0.0.1-amd64-linux&#x20;
5. As seen below, open the mining script with your preferred editor, here we used "nano":nano mine\_hns.sh&#x20;
6. Edit the config and change the following: 6.1 POOL (if mining on a pool different from 6block)
7. USERNAME: This is the username you registered on the pool, you can do something like myusername.1 6.3 PWD: This can be anything, just a "x" will suffice 6.4 VENDOR: amd/nvidia depending on your GPU&#x20;
8. After you've finished, save and exit the file by pressing "ctrl +x and then press Y when asked"&#x20;
9. Start mining with ./mine\_hns.sh and press Enter

![6miner download](https://images.ctfassets.net/v3ez3dek3dk6/qPFTr3sfS97ynwvqQuNmC/141771957b7be99be5d8e62750646683/6miner1.png?fit=pad\&w=720)

Currently there's only a Linux‐64bit build, please choose that one. The miner will work on any Linux distribution, please make sure to have the correct GPU drivers installed.

![6miner download](https://images.ctfassets.net/v3ez3dek3dk6/63Hd01YJ3Mkfm3q6rRTfvh/ffee9244d61eaa998d4d4d6c0473a21d/6miner2.png?fit=pad\&w=720)

![6miner folder](https://images.ctfassets.net/v3ez3dek3dk6/4xCHci1ZQXyWcPoMHPAmp1/54f2ae2bfe010f7f7a137e07d3edadff/6miner3.png?fit=pad\&w=720)

![Editing 6miner config](https://images.ctfassets.net/v3ez3dek3dk6/2Rs0HnYZNlGMum2rZSJmkd/dd708841383904dc1e9b46abe680a9c1/6miner4.png?fit=pad\&w=720)

![Mining successful!](../.gitbook/assets/image.png)

Note the 64.7 MH/s reading, that is your hashrate. This is from a Radeon RX 580 8GB. Pretty good results on this one. Go to https://6block.com and go to "My Homepage", this will show you your current dashboard and all the mining stats you'll need.&#x20;

### Setting up Handyminer&#x20;

Full install steps are detailed here: [https://github.com/HandshakeAlliance/HandyMiner‐CLI](https://github.com/HandshakeAlliance/HandyMiner%E2%80%90CLI)&#x20;

### Step 3: Withdraw to your HNS wallet address

Go to [https://6block.com](https://6block.com), click on your email address in the top right corner and then "Settings".

![Withdrawing HNS from 6block. ](https://images.ctfassets.net/v3ez3dek3dk6/2SZcD2m8syU8xa6VT02J6y/6d912d81baa0c0bd0580a46239d4e68d/Image\_from\_iOS\_\_11\_.jpg?fit=pad\&w=720)

From your settings, click on Mining Accounts and paste in your Namebase HNS wallet address to withdraw your HNS to Namebase.

All in all it should be straightforward to get started mining HNS. Visit the [Namer Community](https://discord.gg/V3aTrkp)'s [#mining ](https://discord.gg/A4f7CNr)channel, where even the creators of these miners lurk, to ask about and discuss Handshake mining.
