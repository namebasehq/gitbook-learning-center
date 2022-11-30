---
description: About Handshake's name auctions
---

# Handshake拍卖

## Vickery-style auction

Handshake auctions are Vickrey-style auctions, which is a type of sealed-bid auction. Bidders submit their bids without knowing the bid of the other people in the auction, and the highest bidder wins but the price paid is the **second-highest** bid! So the bid you place is the maximum you’ll pay if you win the auction, though in practice you’ll pay less than your bid because it's a second price Vickrey auction.&#x20;

For example, if you bid 1000 HNS for nakamoto/ and someone else bids 500 HNS, you’d win the auction and only pay 500 HNS for nakamoto/.&#x20;

## How does the auction work?

You can place a bid with Handshake coins (HNS) anytime after a top-level domain is released—Handshake names are released sequentially each week according to their hash for one year after launch to impede early adopters from buying up all the "best names".

Bids can take on any value and you can optionally add a blind to your bid to hide the true value of your bid from others. Your bid + blind is called your [lockup](handshake-auction.md#whats-a-lockup), which is what the other bidders (and the rest of the network) sees. Your HNS lockup will be non transferable for the duration of the auction, but the blind will be returned to you regardless of whether you win the auction. 

After the first bid, bidding is open to everyone for 720 [blocks](blockchain-refresher.md#block-time). After the bidding period ends, the reveal period begins. Everyone will have 1440 blocks to reveal their bid price and your blind is immediately returned to you once your bid is revealed—Namebase does this automatically for you so if you’re a Namebase user you won’t need to worry about this step.&#x20;

The winning bid is chosen at the end of the 1440 blocks reveal period and the winner pays the second highest bid amount while the other bidders get their entire lockup back. Note the winner’s payment is **burned** by the network, so the winner doesn’t pay bids to anyone per se. This creates a deflationary effect on the network.

The winner gets to use their Handshake top-level domain however they wish (Namebase helps you manage its settings without being a programmer) and the rest of the bidders can continue trying their luck on other top-level domains.

## **What's a lockup?**

Your lockup is made up of = your bid + blind.

Basically your funds are locked up so you can’t spend what you lock up until after the auction ends. This is to prevent people from bidding more than they can spend and to prevent people from bidding on more names than they’re willing to actually purchase.

It's important to note that the blind is optional, which means that the bid amount can be anywhere from 0 to the actual lockup amount. It's not necessarily the same as the lockup amount because if that was the case then everyone would know everyone else’s bids and it wouldn’t be a blind auction anymore.

Most importantly, the amount you actually bid can’t be updated after you submit it. You can submit additional bids but your previous bid will still be locked up (e.g. if you submit two bids of 1000 HNS and 10,000 HNS, 11,000 HNS will be locked up for the duration of the auction).

## **What happens when you win/lose?**

If you lose, your funds are returned in full (minus the Handshake [Mining Fee](blockchain-refresher.md#mining-fee)) after the reveal period ends. If you win, congrats! You're now one of the first owners of decentralized top-level domains on the internet. Companies regularly pay more than [$200k](about-handshake/endless-top-level-domains.md#artificially-restricted) to register top-level domains with the ICANN, so it's pretty cool that you [own](about-handshake/unstoppable-and-private.md) your personal top-level domain. 

You can now point your top-level domain to a personal webpage, set up subdomains for your top-level domain, or sell your top-level domain to someone else for a profit!

### What happens if there's a tie?

If it looks like you tied with someone else, but they won, there are two possibilities&#x20;

1. You may have **actually been outbid** by a tiny amount. Go to the auction page on a computer (not on mobile) and mouseover the bid amounts to show more decimals. Namebase shows 2 decimals by default, so if you bid 1HNS, and someone else bid 1.0001, they will win, but your bids will look identical unless you mouseover. This isn’t ideal, and we’re fixing this UI to display more decimal places. \

2. If you and the person who won really did bid exactly the same amount, though, (you can verify further by going to [shakescan.com](http://shakescan.com), searching for the name in question, and looking at the bids that had the same amount as yours)  it’s near random who will win. Specifically, in the case of a tie, whoever’s **reveal** transaction comes first wins. Namebase **reveals** all of the true bid amounts at basically the same time, so in most situations, they will all be in exactly the same block. However, miners get to choose the order of transactions within each block, and there are multiple distinct mining software packages for HNS; the upshot of this is that which one appears first is effectively random. Complicating things slightly more, if you as a Namebase user tie with someone who bid not using Namebase, they might reveal significantly before or after Namebase reveals (currently, Namebase reveals after 20 blocks) which would also affect who’s tied transaction is ordered first.&#x20;

Finally if you want to avoid ties, many of them are just caused by humans preferring round numbers. If you always bid 1.xx instead of 1, you will probably win much more of the time, and tie less frequently.
