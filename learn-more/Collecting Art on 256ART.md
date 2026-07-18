---
order: 90
---

# Collecting Art on 256ART

Minting creates a token from an artist's generative series and assigns it to your wallet. If terms such as wallet, gas, token, seed, or allowlist are unfamiliar, first read [Understanding and Navigating 256ART](/learn-more/understanding-and-navigating-256art/).

### Before You Mint

You will need:

- a wallet that can connect to 256ART;
- enough ETH on the artwork's chain for the mint price and network gas; and
- the official artwork page on [256ART](https://256.art/artworks).

Ethereum, Base, and Shape are separate networks even though each uses ETH. Check the **Chain** field on the artwork page before funding or connecting your wallet.

Also review:

- **Mint status and dates**: the sale may be upcoming, in an allowlist phase, open to the public, completed, or sold out.
- **Sales mechanism**: Fixed Price, Fair Dutch Auction, or Open Edition.
- **Seeding**: most releases use random-seed **Long form** minting; a collector-selected or **collector curated** release lets you choose a seed.
- **Supply and mint limit**: some releases restrict the number of pieces a wallet can mint.
- **[License](https://256.art/learn/256art-artwork-licenses)**: this explains the rights associated with the artwork.

The preview shown before a random-seed mint is an example, not the piece you will necessarily receive. When this applies, the artwork page displays: **“Preview only. The final mint is generated with a random hash.”**

### How to Purchase Art

The **Mint** button asks the collection's smart contract to create your token:

1. Open the series you want on the [256ART artworks page](https://256.art/artworks).
2. Connect the wallet that should receive the artwork.
3. If prompted, switch the wallet to the chain shown on the artwork page.
4. Choose the number of pieces to mint. For a collector-selected release, generate previews and select your seed first.
5. Select **Mint**.
6. Review the wallet request. Check the site, network, receiving account, mint value, and estimated gas before confirming.
7. Confirm the transaction and wait for the network to include it in a block.

Do not submit the mint again only because confirmation is taking longer than expected. Check your wallet's activity or open the transaction in the chain's block explorer first. A failed transaction does not create a token, although the network may still charge gas for the attempted transaction.

If you mint during a Fair Dutch Auction above its final clearing price, the rebate is not automatic. Current contracts make it claimable after the one-hour auction period through a separate transaction. Return to the official artwork page with the minting wallet and follow its rebate flow. If no claim control appears, contact 256ART before calling `claimRebate` directly because the contract function includes a payout-address parameter.

After confirmation, open [The Gallery Page](/learn-more/the-gallery-page/) to see pieces held by your connected wallet. You can also view recent mints on the series page.

### How to Get the Art Live from Chain

The easiest way to view the canonical live artwork is to select **Render live from chain** on a minted piece or use **Live View** in your gallery. 256ART retrieves the rendering data from the collection contract.

You can also read the contract yourself. This is an advanced option and the exact function name differs between contract generations. Use only the verified contract address linked from the official 256ART artwork page. `tokenHTML` returns executable artist-supplied HTML and JavaScript; on-chain availability does not mean the code has been security-audited. For a deeper audit procedure, see [How to Verify Whether an Artwork Is Actually On-Chain](https://256.art/learn/verify-on-chain-art).

1. Find the collection's contract address and your token ID on the artwork page, marketplace, or transaction.
2. Open the contract on [Etherscan](https://etherscan.io/) for Ethereum, [BaseScan](https://basescan.org/) for Base, or [Shapescan](https://shapescan.xyz/) for Shape.
3. On Etherscan or BaseScan, open **Contract** and then **Read Contract** or **Read as Proxy**. On Shapescan, open the verified **Contract** tab and use **Read/Write Contract** or **Read/Write Proxy**.
4. If those controls are absent, stop rather than supplying a custom ABI.
5. For a modern release, look for `tokenHTML` and enter the token ID. If it is absent, try the legacy `getTokenHtml` function, then the older `getArtFromChain` function.
6. Copy the complete returned value. Current contracts return a data URL beginning with `data:text/html;base64,`.
7. Paste that complete data URL into a new browser tab to render the HTML.

To inspect the ERC-721 metadata, call `tokenURI` with the token ID. Current contracts return a data URL beginning with `data:application/json;base64,`. Opening that complete value in a browser displays the metadata, including the traits and the on-chain live `animation_url`.

Only use read functions for inspection. They do not require a wallet transaction or gas. A block explorer's **Write Contract** functions can change contract state and may require payment, so do not use them unless you understand the operation.

For independent recovery without the 256ART interface, read [What Happens to the Artwork If 256ART Disappears?](https://256.art/learn/if-256art-disappears).
