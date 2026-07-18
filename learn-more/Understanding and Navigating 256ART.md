---
order: 100
---

# Understanding and Navigating 256ART

### What is 256ART?

256ART is an open platform for creating and collecting [fully on-chain generative art](https://256.art/learn/what-is-on-chain-art).

**[Generative art](https://256.art/learn/generative-art)** is created with an algorithm: the artist designs a system of rules, and that system can produce many related but distinct outputs. When a collector mints on 256ART, the artist's code combines with a unique seed to create that collector's piece. For deterministic decisions, the same code and seed reproduce the same base composition. Dynamic blockchain state, interaction, animation timing, and viewport conditions can change a render.

On 256ART, the code needed to render the artwork, its traits, and its ERC-721 metadata are served from smart contracts on the blockchain. This lets collectors retrieve the live artwork without depending on the 256ART website.

### Key Terms for New Collectors

- **Blockchain or chain**: a shared network that records transactions and runs smart contracts. Ethereum, Base, and Shape are separate networks.
- **Wallet**: an app used to control a blockchain account. You use it to sign in, approve a mint, and hold the resulting token.
- **NFT or token**: the blockchain record representing ownership of one unique piece. Each piece has a **token ID** within its collection.
- **ERC-721**: the common smart-contract standard that defines how unique tokens expose ownership, transfers, and metadata to wallets and marketplaces.
- **Smart contract**: code deployed to a blockchain. It defines how a collection is minted and how its tokens and metadata can be read.
- **Mint**: the transaction that creates a token and assigns it to a wallet.
- **Gas**: the network fee paid to process a blockchain transaction. Gas is separate from the artwork's mint price and changes with network activity.
- **Seed or hash**: the value used by an artist's algorithm to generate one repeatable base variation.
- **Traits**: named characteristics of an output, such as its palette or composition.
- **Metadata**: structured information that wallets and marketplaces read, including the piece's name, description, traits, and links or data used to display it.
- **Block explorer**: a website for inspecting public blockchain transactions, addresses, and verified smart-contract functions.

### What Does "Fully In-Chain" Mean?

256ART now generally uses the term **fully on-chain**; some earlier 256ART material calls the same approach **fully in-chain**.

An NFT can be on a blockchain while some of its content is stored elsewhere. For example, a contract's `tokenURI` may point to metadata on a project server or a separate storage network. If that external location becomes unavailable, an owner can still prove ownership of the token, but applications may no longer be able to load its metadata or artwork. See [On-Chain vs IPFS vs Arweave vs Centralized Storage](https://256.art/learn/on-chain-vs-ipfs) for the differences.

For current 256ART releases:

- the artist's rendering code is stored on-chain;
- traits and core artwork information are generated and served on-chain;
- `tokenURI` returns the token's metadata through the standard ERC-721 interface; and
- the metadata's live `animation_url` is assembled from the on-chain artwork through the collection contract.

This guarantees that the code and core metadata stored by 256ART can be retrieved from the contract for as long as the underlying chain and its on-chain dependencies remain available. An artist's script can still introduce an external runtime dependency by fetching media or data from another storage network or web service. Review the artwork details when that distinction matters to you.

256ART also creates static image previews so galleries and marketplaces do not need to run many live artworks at once. A static preview may be regenerated or served separately from the canonical live artwork. It is a convenience image, not the source of the fully on-chain piece. See [The Gallery Page](/learn-more/the-gallery-page/) for the difference between Live View and a high-resolution preview.

The first eight series carry the **OG** tag and use an earlier 256ART architecture. They are on-chain releases, but they do not provide the same fully on-chain interfaces as newer series.

### How a Generative Mint Works

The exact controls depend on the release, but the underlying process is:

1. The artist uploads the artwork algorithm and defines its possible traits.
2. The artist chooses the collection size, sale type, and how seeds are assigned.
3. A collector confirms a mint transaction in their wallet.
4. The collection contract creates a token and associates it with a seed.
5. The artwork algorithm uses that seed and the token's traits to render the collector's output.

Most releases assign a random seed at mint; artwork pages may label this traditional generative format **[Long form](https://256.art/learn/long-form-generative-art)**. A **collector-selected seed** release, also called a **collector curated mint**, lets you generate previews and choose the seed you want before minting. The artwork page tells you whether a preview is only illustrative or can be selected for the final mint.

Artists can choose from three sales mechanisms:

- **Fixed Price**: every public mint has the same set price.
- **Fair Dutch Auction**: the price begins above the reserve price and decreases over time. Eligible minters who paid above the final clearing price can claim a rebate.
- **Open Edition**: any number of pieces can be minted at a fixed price while the sale is open.

A release may also have an **allowlist** period. During this earlier period, only approved wallet addresses can mint, usually with a separate price and mint limit.

### What Chains are Supported?

256ART releases are live on:

- **Ethereum**
- **Base**
- **Shape**

Each is a separate network. Before minting, check the **Chain** field on the artwork page and make sure your wallet has enough of that network's native currency to cover both the mint price and gas.

**Sepolia** is an Ethereum test network used during artist testing. Sepolia tokens do not have real monetary value, and Sepolia test releases are not part of the main collector experience.

### Benefits of an Open Platform

256ART is open to artists rather than limited to a platform-curated list. Any artist can create an account in the Artist Portal and prepare a release.

For collectors, this provides access to a broad range of artists, styles, release sizes, and prices. Openness is not the same as platform endorsement, however. Before minting, review the artist, artwork details, [license](https://256.art/learn/256art-artwork-licenses), chain, price, supply, and sale terms shown on the artwork page.

### Understanding the Tags

Tags describe how an artwork behaves and help you filter the [artworks page](https://256.art/artworks):

- **OG**: one of the first eight series released before 256ART became an open platform. These releases use the earlier on-chain architecture described above.

- **Dynamic**: the live output can respond to current blockchain data, such as its owner, the current block, or the number of pieces minted. Because that data can change, a dynamic artwork may look different when rendered later even though its original seed remains the same.

- **Animated**: the artwork includes motion.

- **Interactive**: the live artwork responds to input such as pointer, keyboard, touch, or other actions chosen by the artist.

- **Sound**: the artwork includes audio. Your browser may require an interaction before it allows sound to play.

An artwork can have more than one tag. Tags describe features; they are not rarity rankings or quality ratings.

### Next Steps

- Learn how to prepare for a mint in [Collecting Art on 256ART](/learn-more/collecting-art-on-256art/).
- Learn how to access collected pieces in [The Gallery Page](/learn-more/the-gallery-page/).
- If you are an artist, continue with the [Artist Documentation](/artist-documentation/).
