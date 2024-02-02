---
description: About Handshake's Vickrey-style name auctions
---

# Name minting auction

{% embed url="https://www.youtube.com/watch?v=KfRDofpzEF8&ab_channel=JohnnyWu" %}

## Minting process

The cost to mint a Handshake name is determined by the name's on-chain auction.

You can place a bid on any unminted name with [Handshake coins (HNS)](handshake-coin.md). This triggers the start of the name's 720-[block](mining-hns.md#handshake-blocks) (\~5 days) bidding period. You can bid any amount and optionally add a blind to hide your actual bid from others. Your bid + blind is called your [lockup](handshake-auction.md#lockup), which is the only value that other bidders see. 

After the bidding period ends, the 1440-block reveal period begins, during which bidders must reveal the true value of their bids. The bidder with the highest bid (NOT the highest lockup) wins the auction and mints the name. If you placed a blind, it's immediately returned to you when you reveal your bid. A note of caution: If you forget to reveal your bid, it will not be counted and you will permanently lose your entire lockup (both your bid and any blind). However, you don't have to worry about losing your coins if you use Namebase as Namebase reveals your bids automatically.

After the reveal period ends, the winning bidder pays only the second highest bid amount — not their winning bid — and is refunded the difference between the two. Losing bidders get their entire lockup amount back in full. If there is only one bid, the sole bidder mints the name for free because the second highest bid is effectively zero. No one receives the coins paid by the winner; they are burned from the blockchain, creating a deflationary effect on the HNS price.

Check your understanding of the Handshake name auctions with these [case studies](handshake-auction.md#case-studies).

![](<../.gitbook/assets/Life cycle of a name.png>)

## Blinds and lockups

Lockup Amount = Bid Amount + Added Blind

Your lockup is the sum of your bid and your blind. It's called a "lockup" because these coins are locked up until the auction ends. This is to prevent people from bidding more than they have and from spamming bids on names they don't want to actually purchase.

It's worth emphasizing that only bids determine the auction winners — the blinds, which are completely optional, are disregarded. In other words, the **highest bid wins the auction, **_**not**_** the highest lockup**! Blinds can be helpful because they hide your bid and make it appear higher to others (only you can see your bid amount while others see only the lockup amount). You also receive your blind back right at the beginning of the reveal period, whereas your bid is returned only once the reveal period has ended.

Your lockup cannot be changed after you submit it. You can submit additional lockups but any previous ones will remain locked up (e.g. if you submit two lockups of 1,000 HNS and 10,000 HNS, 11,000 HNS will be locked up for the duration of the auction).

## What happens if there's a tie?

If you tied with someone else but they won, there are two possibilities:

1. You were outbid by a tiny amount. Go to the auction page on a computer (not on mobile) and mouseover the bid amounts to show more decimal places. Namebase shows two decimal places by default, so if you bid 1 HNS, and someone else bid 1.0001 HNS, they will have won. Unless you mouseover your competitor’s lockup, their bid will look identical.
2. The winner’s bid was revealed before yours. If you and your competitor place identical bids, whoever reveals their bid first wins. However if you’re both Namebase users, the winner is chosen at random because Namebase reveals all bids at nearly the same time in no preset order.

Many ties are caused by use of whole numbers. If you add a fractional amount to your bid, you are less likely to tie.

## Case Studies

Check your understanding of the name auction process by seeing if you can answer:&#x20;

1. Which bidder won?
2. How much HNS did the winner burn?
3. How much HNS will the winner receive back?

#### Case Study 1

| Bidder | Lockup    | Bid Amount | Added Blind |
| ------ | --------- | ---------- | ----------- |
| A      | 1,000 HNS | 1,000 HNS  | 0 HNS       |
| B      | 1,000 HNS | 100 HNS    | 900 HNS     |
| C      | 1,000 HNS | 10 HNS     | 990 HNS     |

#### Case Study 2

| Bidder | Lockup    | Bid Amount | Added Blind |
| ------ | --------- | ---------- | ----------- |
| A      | 1,100 HNS | 100 HNS    | 1,000 HNS   |
| B      | 650 HNS   | 150 HNS    | 500 HNS     |
| C      | 2,050 HNS | 50 HNS     | 2,000 HNS   |

#### Case Study 3

| Bidder | Lockup      | Bid Amount | Added Blind |
| ------ | ----------- | ---------- | ----------- |
| A      | 1,000 HNS   | 1,000 HNS  | 0 HNS       |
| B      | 10,000 HNS  | 1,000 HNS  | 9,000 HNS   |
| C      | 100,000 HNS | 1,000 HNS  | 99,000 HNS  |

### Answers

#### Case Study 1

1. Bidder A won because they had the highest bid amount at 1,000 HNS
2. Bidder A burned 100 HNS because the second highest bid was 100 HNS
3. Bidder A receives a 900 HNS rebate because they burned only 100 HNS of their 1,000 HNS bid

#### Case Study 2

1. Bidder B won because they had the highest bid amount at 150 HNS
2. Bidder B burned 100 HNS because the second highest bid was 100 HNS
3. Bidder B receives a 50 HNS rebate because they burned only 100 HNS of their 150 HNS bid; they'll also receive their entire added blind as does everyone else

#### Case Study 3

1. The winner here is a bit difficult to determine because all 3 bidders [tied](handshake-auction.md#what-happens-if-theres-a-tie) with identical bid amounts of 1,000 HNS. The winner of a name auction with identical winning bid amounts is determined by whichever bidder reveals their bid amount first. However if all 3 bidders are Namebase users, then the winner is random.
2. The winner burned 1,000 HNS because the second highest bid was also 1,000 HNS
3. The winner receives no bid rebate because they've burned their entire 1,000 HNS bid; they'll get back their entire added blind as does everyone else

## Notes on "sniping"

While Namebase submits your bids promptly to the blockchain, it may still take a few blocks for miners to add your bids to the blockchain. Given this, there's a risk-reward spectrum for placing bids at the last minute (colloquially called "sniping"): the later you place a bid, the less likely someone will see it in time to post a higher bid, but the greater the chance your bid won't make it onto the blockchain.&#x20;

When bidding on a name you really care about (e.g. your first+last name), we highly recommend placing your highest true bid amount well before the end of an auction. This way you can ensure your bid is mined in time, and that if you do get outbid, you'll know it was by someone who was simply willing to pay more. For example, if you place a 5 HNS bid on your name, you're signaling that you wouldn't be willing to pay more than that and would be okay giving your name up to someone who bids more.

## More

Check out this detailed writeup on Handshake Auctions and strategies by blockdomains: [Thoughts On Hansdhake Top-Level Domain Market Dynamics](https://blockdomains.substack.com/p/thoughts-on-handshake-top-level-domain)

Still not entirely sure how to proceed? Visit the [Namer Community Discord](https://discord.gg/V3aTrkp)’s [#auctions-and-marketplace ](https://discord.gg/9v5QP6r)channel to ask about and discuss bidding strategies. 
