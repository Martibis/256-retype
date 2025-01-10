---

order: 70

---

# Opensea & Enforcing Royalties

We strongly recommend artists to set up and update various aspects of their NFT collections directly on OpenSea. Below are the key sections available under the **Edit Project** area in OpenSea:

### Details

Manage the foundational aspects of your NFT collection to enhance its visibility and appeal.

- **Name**
  - **Description:** The title of your NFT collection. It should be unique and reflective of the artwork or theme.
  - **Example:** "Test Project"

- **Description**
  - **Description:** Provide a detailed explanation of your collection. Markdown syntax is supported, allowing for formatted text. This description helps potential buyers understand the inspiration and story behind your NFTs.
  - **Character Limit:** 1000 characters
  - **Example:** "A collection of generative art pieces exploring the intersection of technology and nature."

- **URL**
  - **Description:** Customize the URL of your collection on OpenSea. It must contain only lowercase letters, numbers, and hyphens.
  - **Format:** `https://opensea.io/collection/your-custom-url`
  - **Example:** `https://opensea.io/collection/test-project`

- **Category and Tags**
  - **Description:** Enhance discoverability by selecting an appropriate category and adding relevant tags. Categories help classify your collection, while tags act as keywords for search optimization.
  - **Options:** Various categories such as Art, Music, Photography, etc.
  - **Example Tags:** "Generative Art", "Abstract", "Digital"

- **Payment Tokens**
  - **Description:** Specify which tokens can be used to buy and sell your items. By default, ETH and WETH are available, but you can add more tokens as needed.
  - **Options:** ETH, WETH, and others via "Add token"

- **Featured Image**
  - **Description:** Upload an image that will be used to feature your collection on the OpenSea homepage, category pages, or other prominent display areas.
  - **Recommended Size:** 600 x 400 pixels
  - **Example:** A high-quality logo or representative artwork from your collection.

- **Display Theme**
  - **Description:** Choose how your items are visually presented on OpenSea.
  - **Options:**
    - **Padded:** Adds padding around your items.
    - **Contained:** Items are contained within a fixed area.
    - **Covered:** Items cover the entire display area without padding.

- **Explicit & Sensitive Content**
  - **Description:** Mark your collection as containing explicit or sensitive content if applicable.
  - **Options:** Toggle to set the flag.

- **Trait-Based Collection Offers**
  - **Description:** Enable trait-based offers, allowing collectors to make offers based on specific traits of your NFTs.

- **Show OpenRarity Ranking**
  - **Description:** Display OpenRarity rankings after all items have been minted. This provides collectors with information on the rarity of each NFT in your collection.

- **Collaborators**
  - **Description:** Add collaborators who can edit the appearance of your collection or drop pages on OpenSea. Collaborators can make cosmetic changes but cannot alter payout addresses or creator earnings percentages.
  - **Capabilities:**
    - Edit collection or drop appearance
    - Cannot change payout addresses
    - Cannot modify creator earnings percentages
  - **Example:** Adding a co-artist or marketing manager as a collaborator.

### Creator Earnings

- **Enforceability of Creator Earnings**
  - **Description:** As 256ART contracts now adhere to the [ERC721-C](https://opensea.io/blog/articles/creator-earnings-erc721-c-compatibility-on-opensea) standard, artists can optionally enforce creator earnings on-chain, ensuring that royalties are automatically applied across all marketplaces that support this feature.
  - **Benefits:**
    - **Full Enforcement:** Guarantees that royalties are honored by restricting sales to compliant marketplaces.
    - **Control:** Artists maintain consistent royalty earnings without relying on third-party marketplace compliance.
  - **Implications:**
    - **Marketplace Limitations:** Enforcing royalties may limit your NFTs to only certain marketplaces that honor these settings.
    - **Invalidation of Existing Listings:** Enforcing earnings will invalidate any existing listings and offers on OpenSea that do not comply with the enforced royalty structure.
  - **Action:** Toggle to "Turn on enforced earnings" to activate this feature.
  - **Note:** By enabling enforced earnings, artists can fully ensure that their secondary royalties are consistently applied, providing ongoing revenue from future sales.

---

## Summary

By leveraging the **Details** and **Creator Earnings** sections within OpenSea's **Edit Project** feature, artists can comprehensively manage their NFT collections. These settings not only enhance the discoverability and presentation of your collection but also ensure that you maintain control over your revenue streams through enforced secondary royalties.

For more detailed guidance, refer to OpenSea's official [documentation](https://docs.opensea.io/).