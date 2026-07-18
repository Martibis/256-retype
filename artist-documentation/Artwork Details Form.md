---

order: 85

---

# Artwork Details Form

The Artwork Details Form defines what collectors see and configures the contracts used for your release. Complete the [Generative Art Template](/artist-documentation/generative-art-template/) workflow first, then open an unreleased project in the [Artist Portal](https://256.art/artistportal).

Fields marked with `*` are required. Review addresses, percentages, files, prices, supply, and sale type especially carefully: some values are costly or impossible to change after deployment.

### Artwork Name*

Enter the public name of the series. Check spelling and capitalization, and search for confusingly similar names before release. This name appears in the artwork details and token metadata.

### License*

Choose the license that describes what token owners and other people may do with the artwork. A license can govern copying, display, modification, and commercial use; owning an NFT does not automatically transfer copyright.

The available choices are:

- **[NFT License 2.0](https://www.nftlicense.org/)**: grants rights to the current owner of the token-specific artwork, including limited commercial merchandise rights under the license's terms. Those token-holder-specific rights end when ownership is transferred.
- **[Creative Commons Attribution–NonCommercial 4.0 International / CC BY-NC 4.0](https://creativecommons.org/licenses/by-nc/4.0/)**: lets the public share and adapt the licensed material for noncommercial purposes with attribution. Token ownership is not required.
- **[CC0 1.0 Universal](https://creativecommons.org/publicdomain/zero/1.0/)**: dedicates the licensed material to the public domain to the fullest extent permitted by law, allowing public reuse, modification, and commercial use without requiring token ownership.

These choices create different relationships: NFT License 2.0 ties specified rights to the current token holder, while CC BY-NC 4.0 and CC0 are public instruments available to everyone. Read [The Three Artwork Licenses on 256ART](https://256.art/learn/256art-artwork-licenses) and the complete canonical text before selecting one.

This summary is general information, not legal advice. Define which material the license covers, confirm that all collaborators authorized the choice, and obtain appropriate legal advice when needed.

### Tags

Select only tags that describe the work's actual behavior, such as Dynamic, Animated, Interactive, or Sound. Collectors use these tags to filter and understand releases. See [Understanding the Tags](/learn-more/understanding-and-navigating-256art/#understanding-the-tags).

### Short Description for the Artwork*

Write a concise summary of the concept and experience. This description is stored on-chain, so length affects deployment size and cost. The maximum is **1,500 characters**.

Prefer plain text that will still make sense in a wallet or marketplace without the rest of the 256ART page.

### Detailed Story Behind Your Artwork

Use this optional section for the longer story: inspiration, process, visual system, intended interaction, and any viewing instructions. Clearly explain dynamic behavior or keyboard, pointer, touch, fullscreen, sound, and image-save controls.

### Sales Mechanism*

Choose how the public sale works:

- **Fair Dutch Auction**: the price starts high and decreases at set intervals until the series sells out or reaches its reserve price. Eligible minters who paid more than the final clearing price can claim a rebate.
- **Fixed Price**: each public mint uses the configured price.
- **Open Edition**: any number of tokens can be minted at a fixed price while the sale is open.

The choice affects the required fields and collector experience. It is not simply a display setting, so test the selected mechanism and dates before release.

### Seeding Mechanism*

Choose how each token receives the seed used by your algorithm:

- **Random Seed at Mint (Long form)**: the contract creates the seed during minting. Collectors can preview examples, but they do not choose the final output.
- **Collector Selected Seed (collector curated mint)**: collectors generate previews and mint a chosen seed, receiving the corresponding output.

Make sure the artwork page's description matches this experience. A selected seed should reproduce the preview consistently.

Read [Artist-Curated, Collector-Curated and Random Generative Art](https://256.art/learn/generative-art-curation) for the creative implications of this choice.

### Collection Size*

Set the maximum token supply for a Fixed Price or Fair Dutch Auction release. This field does not apply to an Open Edition, whose final supply is determined by how many tokens are minted before its end date.

Choose a size that fits the generative system's range and your release goals. Batch-test enough outputs to support that decision. See [What Is Long-Form Generative Art?](https://256.art/learn/long-form-generative-art) for how supply and direct minting change the design problem.

### Reserve Price*

Enter the amount in ETH:

- **Open Edition and Fixed Price**: this is the public mint price.
- **Fair Dutch Auction**: this is the minimum auction price used by the contract's `currentPrice()` calculation. The auction starts at approximately 25 times the reserve price and decreases roughly every 7.5 minutes over one hour.

Review the calculated start and reserve values shown by the portal. The collector also pays network gas, which is separate from this price.

### Allowlist Price*

Set the price available to approved wallet addresses during the allowlist period. The allowlist mint closes when the public sale begins. Confirm whether the intended value is lower than, equal to, or higher than the later public price.

### Max Mints per Allowlisted Address*

Set how many tokens each approved address may mint during the allowlist period. Consider the collection size and number of listed addresses; the limit does not guarantee that every address will receive a token.

### Allow List Addresses

Add addresses manually or upload a CSV using the format requested by the portal. Before submission:

- verify that every address is complete and uses the intended account;
- remove accidental duplicates and blank rows;
- keep a copy of the final list; and
- test the allowlist configuration before release.

The backend derives a **Merkle root**, a compact cryptographic summary used to prove that an address belongs to the allowlist. Changing the list after deployment may require an on-chain update and assistance from the 256ART team.

### Artwork Libraries*

Select every external library the uploaded artwork actually uses, with the same versions used during local testing. Only supported on-chain EthFS libraries can be included. Fewer and smaller libraries generally produce faster live loads. See [Available Libraries](/artist-documentation/generative-art-template/#available-libraries).

### Artwork.js*

Upload the completed, minified `artwork.js` or `artwork-p5.js` code produced from the [Generative Art Template](/artist-documentation/generative-art-template/). Keep an unminified source copy under your own version control.

After any code change, rerun local batch tests and the Artist Portal test. Even a small change can alter deterministic random-call order or preview generation.

### Traits.json*

Upload the minified `traits.json` file. It must be valid JSON, follow the template's cumulative-weight format, and not exceed **20 KB**.

The filename and documentation use lowercase `traits.json`. Validate that descriptions and values are strings, weights increase correctly, and the final threshold for each trait is `10000`.

### Primary & Secondary Revenue Split*

Configure the payout addresses and percentages for primary revenue and paid secondary royalties. The form includes:

- **Owner**: the remaining or automatically calculated share.
- **Platform (256ART)**: the locked platform share.
- **Additional receivers**: collaborators or other recipients you add with a label, address, and percentage.

Verify every address independently. Blockchain transfers cannot be reversed merely because a payout address was entered incorrectly. The complete split must equal the total expected by the portal and cannot exceed **100%**.

The configured owner address becomes the **smart contract owner** and participates in revenue according to the displayed split. Use an address you control and can use for future contract administration. Do not assume the connected login wallet is automatically the correct owner or receiver.

### Secondary Royalty Percentage*

Set the royalty requested when a token is sold on a secondary marketplace. Royalties apply only when a marketplace supports and pays the configured mechanism. The percentage is separate from primary mint revenue.

#### Enforceability of Secondary Royalties

256ART contracts support optional ERC721-C creator-earnings enforcement. Enabling it restricts transfers through marketplace protocols that do not comply with the contract's rules. This can improve royalty enforcement but may reduce where collectors can list or purchase tokens.

ERC721-C compatibility does not make every marketplace support the collection automatically. Read [OpenSea & Enforcing Royalties](/artist-documentation/opensea-enforcing-royalties/) before choosing enforcement.

### Additional Notes:

- **Validation and errors**: resolve every required-field, JSON, file-size, address, percentage, and compatibility error.
- **Warnings**: read warnings carefully. A file or configuration change can invalidate a previous test or require a contract to be redeployed.
- **Submission feedback**: wait for the portal to confirm that the form was saved; do not treat a button click alone as confirmation.
- **Final review**: compare the saved summary with your source files and release plan before testing.

---

Next, [test your project](/artist-documentation/testing-your-project/).
