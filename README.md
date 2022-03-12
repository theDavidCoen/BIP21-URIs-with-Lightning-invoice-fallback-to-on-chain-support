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

#### The goal of this repo is to have a list of wallets, exchanges, payment processors, ATM providers and other Bitcoin-related services able to SCAN the unique QRcode and correctly decode BIP21 URIs with Lightning invoice fallback to on-chain. Also, track the services that can ENCODE this kind of URIs and CREATE the unique QRcode.

### Wallets

 Name | Can decode BIP21 URIs LN invoice + onchain fallback | Priority to onchain or LN? | Can create BIP21 URIs with LN invoice QRcode | Notes |
 ------------ | ------------- | ------------- | ------------ | ------------- | 
[Edge](https://edge.app) | YES | onchain | NO | n.a. |
