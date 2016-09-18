# web2web

### This fork:

I changed webpage.html and tried it myself, it works! Webtorrent is awesome! But I found no instructions on how to host my

#### How I did it:

- download this repo
- edit `webpage.html` and make at least a modification
- download Webtorrent: <https://webtorrent.io> (or another client that supports websocket)
- create a new torrent (on webtorrent drag the file onto it) containing just `webpage.html`
- get the torrent hash (on webtorrent you can right click on the entry in the list and select copy magnet link or copy instant.io link, on the magnet link the hash will be `magnet:?xt=urn:btih:HERE&dn=...`, this is valid for any magnet link, on the instant.io link you can find the hash after the `#` sign.)
- go onto <http://blockchainpen.com>, note your bitcoin address in the top-right corner
- deposit a very tiny amount of bitcoins to it (more than `0.1mbtc`, less than a `1mbtc` suggested, millibits, 0.001 BTC, see extra info to get the private key to be able to sweep your wallet afterwards) and refresh the page
- paste your torrent hash into your funded blockchainpen.com page and write the message to the blockchain
- copy your blockchainpen bitcoin address
- edit `index.html` and change the `btcAddress` value from the existing one to yours
- drop the `index.html` page onto your browser or host it somewhere like on github pages
- call some friends so they will seed your file or put it on <joystream.co> (incentivized seeding w/ bitcoin)
- enjoy!


### Original readme

Server-less & domain-less websites updatable via torrents and bitcoin blockchain.

[live demo](https://elendirx.github.io/web2web)


### Why

Websites get seized by losing control over a webserver or a domain.
If we replace both the webserver and the domain with [torrents](https://webtorrent.io) and [blockchain](https://bitcoin.org/en) then there's nothing left to seize.


## How It Works
This repo contains two HTML files:

+ `index.html` is responsible for loading the webpage from torrent,
+ `webpage.html` is the actual webpage.


When you open `index.html` in the browser ([live demo](https://elendirx.github.io/web2web)), here's what happens:


1. Bitcoin address `1DhDyqB4xgDWjZzfbYGeutqdqBhSF7tGt4` is searched for the latest outgoing transaction containing `OP_RETURN` [script](https://en.bitcoin.it/wiki/OP_RETURN). Inside the script there is a torrent infohash of `webpage.html`.
2. `webpage.html` is downloaded from torrent via [webtorrent](https://webtorrent.io) and displayed.


### How Is It Updated
To perform serverless updates, torrent of the updated `webpage.html` is created and its infohash is inserted into new bitcoin transaction sent from `1DhDyqB4xgDWjZzfbYGeutqdqBhSF7tGt4` address.


### How Is It Domainless
Save the `index.html` to your PC and open it from `localhost`. It will still work and receive updates.


## What Next
### User Accounts
Users will be able to sign up by sending small amount of bitcoin to the `1DhDyqB4xgDWjZzfbYGeutqdqBhSF7tGt4` bitcoin address.
Then they can update their content by inserting torrent infohashes into transactions sent from their addresses.

### E-commerce
It will be possible to build complex serverless anonymous e-commerce websites using bitcoin for payments.


## Project Status
Proof of concept, just for fun. Works in chrome, firefox and opera.
