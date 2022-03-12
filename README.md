# BIP21 URIs with Lightning invoice fallback to on-chain support
## List of wallets, exchanges, payment processors, ATMs and other services that can encode/decode BIP21 URIs with Lightning invoice fallback to on-chain.

Bolt11 invoices can include onchain fallback in their metadata, however the majority of the wallets and service today (2022) cannot read Lightning Invoice, so it's important to have another compatible string for the onchain fallback, just in case something with our LN payment goes wrong.

Luckly, we already have a solution: BIP21 URIs can encode both an onchain address and a Bolt11 invoice (and possibly Bolt12 in the future)!
This can be presented as a unique QRcode with all the info inside.

We can have two protocol handlers - 'bitcoin:' and 'lightning' - encoded into the same URI (and so, into a unique QRcode) this way:
<br> `bitcoin:address?amount=value&label=text&lightning:invoice`

In this image from https://github.com/peakshift, you can see the main QRcode solutions we have today:
![bitcoin-qr-codes](https://user-images.githubusercontent.com/38695835/158013267-5486f8ae-3674-4dfe-a629-bbe1dcad72ec.svg)

For more info about these URI schemes, please refer to https://github.com/peakshift/bitcoin-ux/blob/master/payments/qr-codes.md#user-content-fn-2-8df82013099d376db7fb75c896a383be

## What's the goal?
The goal of this repo is to have a list of wallets, exchanges, payment processors, ATM providers and other Bitcoin-related services <b>able to SCAN the unique QRcode and correctly decode</b> BIP21 URIs with Lightning invoice fallback to on-chain. Also, <b>to track the services that can ENCODE this kind of URIs and CREATE the unique QRcode.</b>
<br>Can this be defined a standard? Let's find out!

## How to test compatibility?
The onchain-only wallet/service should be able to read the QRcode, decode the URI and set the payment screen for the onchain transaction (basically it keeps the 'bitcoin:' part of the URI and drops the 'lightning' part).
<br>The Lightning Wallet should be able to read the QRcode, decode the URI and set the screen for the offchain payment. <br>It COULD give however a different priority and go for the onchain fallback as a standard behavior or due to routing error / no path. In this case it's important to specify what's the reason of this fallback in the notes, if possible.

<b>To test the decoding compatibility</b> you can go to https://donations.davidcoen.it, enter a >15 euro amount and scan with your wallet/service (DON'T pay). <br>
 <b>To test the encoding (QRcode creation) compatibility</b>, you can generate an invoice/payment request with your wallet/service and look at the URI.

## Wallets

 Name | Can decode BIP21 URIs LN invoice + onchain fallback | Priority to onchain or LN? | Can create BIP21 URIs with LN invoice QRcode | Notes |
 ------------ | ------------- | ------------- | ------------ | ------------- | 
[Edge Wallet](https://edge.app) | YES | onchain | NO | NO Lightning Network support
[Enjin Wallet](https://enjin.io/products/wallet) | YES | onchain | NO | NO Lightning Network support
[Math Wallet](https://mathwallet.org/en-us/) | YES | onchain | NO | NO Lightning Network support
[Token Pocket](https://www.tokenpocket.pro/en/developer) | YES | onchain | NO | NO Lightning Network support. Bad UI for tiny amounts



## Exchanges/Custodial services

 Name | Can decode BIP21 URIs LN invoice + onchain fallback | Priority to onchain or LN? | Can create BIP21 URIs with LN invoice QRcode | Notes |
 ------------ | ------------- | ------------- | ------------ | ------------- | 
[Binance](https://www.binance.com/it) | NO | n.a. | NO | NO basic support for BIP21 URIs


## Payment Processors

 Name | Can decode BIP21 URIs LN invoice + onchain fallback | Priority to onchain or LN? | Can create BIP21 URIs with LN invoice QRcode | Notes |
 ------------ | ------------- | ------------- | ------------ | ------------- | 
[BTCpay Server](https://btcpayserver.org/) | YES | onchain | YES | BTCpay can handle onchain payments if a hot wallet is active


## ATM providers

 Name | Can decode BIP21 URIs LN invoice + onchain fallback | Priority to onchain or LN? | Can create BIP21 URIs with LN invoice QRcode | Notes |
 ------------ | ------------- | ------------- | ------------ | ------------- | 
[n.a.](https://#) | n.a. | n.a. | n.a. | n.a.


## Other services

 Name | Can decode BIP21 URIs LN invoice + onchain fallback | Priority to onchain or LN? | Can create BIP21 URIs with LN invoice QRcode | Notes |
 ------------ | ------------- | ------------- | ------------ | ------------- | 
[n.a.](https://#) | n.a. | n.a. | n.a. | n.a.
