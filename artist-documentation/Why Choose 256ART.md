---
order: 100
---

# Why Choose 256ART

### Fully In-Chain
Traditionally, in the world of generative art, the art script is (often) stored on-chain. This means that you can technically recreate the artwork from that script if you have the developer skills to do so. However, other elements, such as the metadata, live HTML, and static image, are usually linked to a centralized or IPFS URL.

With 256ART both the metadata and live view of your art are entirely built and stored fully in-chain. This approach provides the best perseverance of your art as the artwork and the details related to it are permanently stored on the blockchain, ensuring they will always be accessible and immune to any potential data loss issues associated with centralized storage. 

On front-ends and marketplaces, if a centralized URL goes down, an NFT relying on this URL would no longer be visible. This problem is non-existent with 256ART's fully in-chain approach. 

Multiple JavaScript libraries are also available on-chain (most notably p5js and threejs).

### A Platform for Artists
256ART is an open platform, allowing any artist to release their work. We want to empower artists to freely create and share their work on the Ethereum blockchain, with as few hurdles as possible.
### Cost Efficient On-Chain Storage
We utilize gzip compression on your art script before putting it on-chain, significantly reducing the size and the cost of storing it on-chain. On average it's three times cheaper to store on-chain compared to a none gzipped version. 
When rendering your art from chain the DecompressionStream web API is used to gunzip your art script after which it's injected it into the HTML. This is currently supported by all modern browsers.
### Fully Automated Testing
We offer fully automated, one-button-click, testing. Eliminating the hassle of deploying to an Ethereum testnet and dealing with the associated complexities / nuisances. Behind the scenes we spin up an Ethereum node on our back-end and run all of the tests (deploying, minting, building your art, etc.) on that node, so it emulates near exactly how it would be on the Ethereum mainnet.  
### Low fees
7.5% on primary sales and 7.5% of the royalty percentage you choose on secondary sales (e.g.: if you set your secondary royalty to 10%, 256ART would get 0.75%).
### Two Seeding Mechanisms
Random seed generated at mint or collector selected seed at mint.
### Three Sales Mechanisms
Fair Dutch Auction, Fixed Price or Open Edition. 
### Ownership Over Your Smart Contracts
Most of the contract is immutable and you are the owner of the contract. From the contract you can:
- **Artist Mint**: mint tokens to yourself or friends for free (only when no dutch auction is in progress).
- **Withdraw Funds**: withdraw your funds from the contract.
- **Withdraw from Royalty Splitter**: withdraw your share of the royalties.
- **Update Image Base URL**: update the image base URL for your project, allowing you to host the preview images of your art yourself or use alternatives like IPFS.
- **Update Maximum Token Supply**: update the maximum number of tokens that can be minted for your project, mainly to cap the supply at a lower amount if a series doesn't mint out.
- **Update Art Scripts**: update the art scripts associated with your project, mainly to improve preservation, allowing you to make changes to your art script as browser technology evolves.
- **Update Library Scripts**: update the library scripts used in your projects, mainly to improve preservation, ensuring compatibility with any changes made to underlying libraries or browser technology.