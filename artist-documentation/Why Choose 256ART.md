---
order: 100
---

# Why Choose 256ART

### Fully in-chain
Your art is stored and constructed entirely in-chain, with no off-chain dependencies, ensuring that it will exist as long as the Ethereum blockchain does. Multiple JavaScript libraries are also available on-chain (most notably p5js and threejs).
### Artist empowerment
We are an an open platform, allowing any artist to release their work. We want to empower artists to freely create and share their work on the Ethereum blockchain, with as few hurdles as possible.
### Cost efficient on-chain storage
We utilize gzip compression on your art script before putting it on-chain, significantly reducing the size and the cost of storing it on-chain. On average it's three times cheaper to store on-chain compared to a none gzipped version. 
When rendering your art from chain the DecompressionStream web API is used to gunzip your art script after which it's injected it into the HTML. This is currently supported by all modern browsers except for Firefox (and they have it on their roadmap).
### Fully automated testing
We offer fully automated, one-button-click, testing. Eliminating the hassle of deploying to an Ethereum testnet and dealing with the associated complexities / nuisances. Behind the scenes we spin up an Ethereum node on our back-end and run all of the tests (deploying, minting, building your art, etc.) on that node, so it emulates near exactly how it would be on the Ethereum mainnet.  
### Low fees
7.5% on primary sales and 7.5% of the royalty percentage you choose on secondary sales (e.g.: if you set your secondary royalty to 10%, 256ART would get 0.75%).
### Two seeding mechanisms
Random seed generated at mint or collector selected seed at mint.
### Three sales mechanisms
Fair Dutch Auction, Fixed Price or Open Edition. 
### Ownership over your smart contracts
Most of the contract is immutable and you are the owner of the contract. From the contract you can:
- **Artist Mint**: mint tokens to yourself or friends for free (only when no dutch auction is in progress).
- **Withdraw Funds**: withdraw your funds from the contract.
- **Withdraw from Royalty Splitter**: withdraw your share of the royalties.
- **Update Image Base URL**: update the image base URL for your project, allowing you to host the preview images of your art yourself or use alternatives like IPFS.
- **Update Maximum Token Supply**: update the maximum number of tokens that can be minted for your project, mainly to cap the supply at a lower amount if a series doesn't mint out.
- **Update Art Scripts**: update the art scripts associated with your project, mainly to improve preservation, allowing you to make changes to your art script as browser technology evolves.
- **Update Library Scripts**: update the library scripts used in your projects, mainly to improve preservation, ensuring compatibility with any changes made to underlying libraries or browser technology.