---

order: 85

---

# Artwork Details Form

### Artwork Name*
The name of your artwork. It should be unique and descriptive to effectively represent your artwork.

### License*
Specify the license for your artwork. Choosing an appropriate license clarifies how others can use and share your artwork.

### Tags
Add relevant tags to your artwork. These tags assist collectors in discovering your artwork more easily during searches and provide quick insights into your artwork's themes and features.

### Short Description for the Artwork*
A concise description of your artwork. Since this description is stored on-chain, it's advisable to keep it brief to minimize costs. The maximum character limit for this field is **1500 characters**.

### Detailed Story Behind Your Artwork
Share the detailed story behind your artwork. This section allows you to provide context about your artwork, its inspiration, and any other pertinent information to help potential collectors and viewers better understand and appreciate your artwork.

### Sales Mechanism*
Choose the sales mechanism for your release. The available options are:

- **Fair Dutch Auction**: A descending price auction where the price starts high and decreases at set intervals until all NFTs are sold or a minimum price is reached. Any minter that paid more than the minimum price can claim a rebate.
- **Fixed Price**: Each NFT is sold at a predetermined price, and all transactions occur at this rate.
- **Open Edition**: An unlimited number of NFTs can be minted during the sale period, allowing for continuous minting until the sale ends.

### Seeding Mechanism*
Select the seeding mechanism for your release. The available options are:

- **Random Seed at Mint**: Each NFT's traits are randomly assigned when it is minted, ensuring unpredictability.
- **Collector Selected Seed**: Collectors can input a seed value during minting to influence the generation of their NFT's traits, allowing for a degree of customization.

### Collection Size*
Specify the total number of NFTs in the collection. This field is **only applicable** when the sales mechanism is **not** set to **Open Edition**.

### Reserve Price*
The reserve price or minimum price for your release. Depending on the sales mechanism:
- **Open Edition** and **Fixed Price**: The reserve price is the sale price.
- **Dutch Auction**: The reserve price is utilized in the `currentPrice()` function within the smart contract to determine the current auction price. The starting mint price is approximately 25 times higher than the reserve price and decreases every 7.5 minutes (by roughly 1.5x each interval) over a one-hour duration.

### Allowlist Price*
Set a special price for allow-listed addresses. Allow-listed participants can mint NFTs at this price before the public mint opens at the reserve price. This ensures early access for selected addresses.

### Max Mints per Allowlisted Address*
Define the maximum number of NFTs each allow-listed address can mint. This helps control the distribution and ensures fairness among allow-listed participants.

### Allow List Addresses
Provide the Ethereum addresses you wish to add to your allow list. Allow-listed addresses will mint at the **allowlist price** before the public sale begins at the reserve price. You can add addresses manually or upload a CSV file containing multiple addresses.

### Artwork Libraries*
List any external libraries used in your artwork. While multiple libraries can be selected from the provided list, it's recommended to use as few as possible. Large libraries can significantly slow down the retrieval of your art from the blockchain.

### Artwork.js*
Include the JavaScript code that generates your artwork. Ensure it follows the [Generative Art Template](/artist-documentation/generative-art-template).

### Traits.json*
Provide the `Traits.json` file containing metadata for your artwork. It should be in valid JSON format and **must not exceed 20KB** in size. Refer to the [Generative Art Template](/artist-documentation/generative-art-template) for formatting guidelines.

### Primary & Secondary Revenue Split*
Define the revenue distribution among primary and secondary receivers. The form includes pre-set rows for:
- **Owner**: Automatically calculated percentage.
- **Platform (256ART)**: Locked percentage.

You can add additional receivers with custom names, addresses, and percentage splits. Ensure that the total percentage does not exceed **100%**.

You can update the owner address here. This address is the **smart contract owner** and will receive ETH from both primary and secondary sales.

### Secondary Royalty Percentage*
Set the percentage of royalties you'll receive from secondary sales of your work.

#### Enforceability of Secondary Royalties
Secondary royalties are now **optionally enforceable**. This means you can choose to make the royalty percentage mandatory for participating marketplaces or leave it flexible based on marketplace compliance.

### Additional Notes:
- **Validation & Errors**: The form includes validation for essential fields. Ensure all required fields are correctly filled to avoid submission errors.
- **Warnings**: After submission, you may receive warnings indicating actions needed if changes are made, such as redeploying contracts or re-testing your release.
- **Submission Feedback**: Upon submitting the form, feedback will be provided to indicate the status of your submission.

---
