---
description: A guide for transferring Handshake entities
---

# Transferring entities

## Transfer in HNS

### From BTC

Use [this](../starting-from-zero/buy-hns.md#buy-hns-with-btc) guide to transfer BTC to your Namebase wallet to convert to HNS. Note BTC-HNS transactinos take 6 BTC block confirmations (about an hour) to process.

### From another HNS wallet&#x20;

You can transfer HNS from another wallet directly to your Namebase wallet using the address on your [dashboard](https://www.namebase.io/dashboard). Due to the current volatility in Handshake's hash rate, Namebase confirms HNS deposits after 20 blocks, which typically takes 3-4 hours. Namebase will decrease the number of blocks needed to confirm deposits as the hash rate increases and stabilizes.

## Transfer out HNS

If you're outside of the USA, you can use [Namebase Pro](https://www.namebase.io/pro) to transfer out your HNS — please note HNS transfers currently take 20 block confirmations to complete.

If you're inside the USA, unfortunately due to regulations you're currently unable to transfer out your HNS though you can always sell it for BTC or USD.

## Transfer in Handshake names

To initiate the transfer, please transfer your name to your Namebase HNS wallet address, which you can generate through your [dashboard](https://www.namebase.io/dashboard). Once you've sent the TRANSFER and FINALIZE transactions — these must be spaced 288 blocks (\~2 days) apart, the transfer will automatically process in 20 block confirmations.

{% hint style="warning" %}
Remember to submit your FINALIZE transaction!
{% endhint %}

## Transfer out Handshake name

You can transfer your Handshake names to any HNS address by visiting your names' domain manager page and clicking "Transfer domain".

We handle name transfer requests in the same order of when they are submitted, so there may be a queue of up to 7 days before the TRANSFER transaction is sent for your name. In addition, there is an inherent 288 blocks that must past before we submit your FINALIZE transaction (this is a Handshake restrction, not a Namebase one), thus completing the name transfer. This may also take up to 7 days to process.

There are inherent blockchain limitations for the number of TRANSFER and FINALIZE transactions we can submit each block, which you can read more about [here](../about-handshake/mining-hns.md#block-limits).

![](<../.gitbook/assets/Transfer this domain.png>)
