---
order: 100
---

# Why Choose 256ART

### Fully In-Chain

256ART stores and serves the artwork's rendering code, traits, and core ERC-721 metadata through smart contracts. A collector can retrieve that code and metadata from the collection contract without relying on the 256ART website. This [standards-native delivery path](https://256.art/learn/standards-native-on-chain-art) begins with the collection's `tokenURI`. Your script can still create an external runtime dependency if it fetches media or data from another storage network or web service, so disclose and make that choice resilient where applicable.

256ART now generally calls this **fully on-chain**. Read [Understanding and Navigating 256ART](/learn-more/understanding-and-navigating-256art/#what-does-fully-in-chain-mean) for a plain-language explanation, including how live artwork differs from static marketplace previews.

### A Platform for Artists

256ART is an open platform: any artist can create an account in the [Artist Portal](https://256.art/artistportal), prepare a compatible project, test it, and release it. You do not need to apply to a curated release program.

### Cost Efficient On-Chain Storage

Blockchain deployment cost is strongly affected by the amount of data stored. Before deployment, 256ART compresses the artwork script with gzip and encodes it for storage. This reduces the script's stored size and therefore usually lowers deployment gas compared with storing the uncompressed source.

The final cost still depends on the script and library sizes, the number of contracts required, the selected chain, and gas conditions at deployment. The platform's pre-release test provides an estimate before you release. Learn more about [how 256ART compresses JavaScript for on-chain storage](https://256.art/learn/256art-compression).

### Fully Automated Testing

The Artist Portal can deploy and mint a test version of your project in a Sepolia-based test environment. It checks contract deployment, token metadata, live rendering, and image-preview generation without requiring you to configure a local blockchain toolchain or spend mainnet gas.

Testing catches many release problems, but it cannot guarantee that every browser, marketplace, or future network condition will behave identically. You are responsible for reviewing the generated output before approving a release. See [Testing Your Project](/artist-documentation/testing-your-project/).

### Multi Chain

You can release on Ethereum, Base, or Shape. These are separate mainnet networks with different gas conditions and audiences. Sepolia is used for testing and is not a production release network.

### Low fees

256ART's published platform fees are:

- **Primary sales**: 10% of primary mint revenue.
- **Secondary sales**: 10% of the royalty amount you set, when that royalty is paid.

Network gas and third-party marketplace fees are separate. Review the revenue split in the Artist Portal before deploying.

### Two Seeding Mechanisms

- **Random Seed at Mint (Long form)**: the contract assigns the seed when a collector mints. Pre-mint outputs are examples rather than a guarantee of the final piece.
- **Collector Selected Seed (collector curated mint)**: collectors generate previews and choose the seed they want to mint.

Choose the mechanism that matches the intended collecting experience. The choice affects the mint interface and cannot be treated as a cosmetic setting.

### Three Sales Mechanisms

- **Fair Dutch Auction**: starts above the reserve price and decreases over time; eligible minters who paid above the clearing price can claim a rebate.
- **Fixed Price**: each public mint uses the same configured price.
- **Open Edition**: any number of pieces can be minted at a fixed price before the sale ends.

The [Artwork Details Form](/artist-documentation/artwork-details-form/#sales-mechanism) documents the settings for each mechanism.

### Ownership Over Your Smart Contracts

The owner address selected in the Artwork Details Form becomes the owner of the released collection contract. That address can use the contract's available administrative functions and receives funds according to the configured split.

Contract ownership also carries responsibility: verify the address carefully, protect its keys, keep enough ETH for future administrative transactions, and understand which settings are editable after deployment. Read [What an Artist-Owned Collection Contract Really Means](https://256.art/learn/artist-owned-contracts), then see [Releasing Your Artwork](/artist-documentation/releasing-your-artwork/#post-release).

Continue with [Getting Started](/artist-documentation/getting-started/).
