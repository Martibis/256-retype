# OpenSea & Enforcing Royalties

After a 256ART release is deployed, OpenSea may discover its tokens from the chain automatically. OpenSea's collection page and creator-earnings settings are marketplace configuration; they do not replace the on-chain artwork metadata or the 256ART mint page.

OpenSea changes its interface over time. Use this page for the 256ART-specific decisions, and follow OpenSea's current official guides for button locations:

- [Edit collection details](https://support.opensea.io/en/articles/8867025-how-do-i-edit-my-collection-details)
- [Set creator earnings](https://support.opensea.io/en/articles/8867026-how-do-i-set-creator-earnings-on-opensea)

Connect the wallet that owns the 256ART collection contract. Verify the chain and full contract address before changing a collection with a similar name.

### Details

In [OpenSea Studio](https://opensea.io/studio), select the collection associated with the deployed 256ART contract and open **Collection Details**.

Review the fields currently offered by OpenSea, which can include:

- **Display name**: normally match the released artwork name so collectors can identify it.
- **Description**: summarize the series and link to the official 256ART artwork or artist page. OpenSea currently supports Markdown.
- **Custom OpenSea URL**: choose a clear collection slug if the option is available.
- **Collection images and presentation**: use artwork you have the right to publish and preview it at the sizes OpenSea requests.
- **Category, tags, and content classification**: describe the collection accurately, including explicit or sensitive content where applicable.
- **Collaborators**: add only trusted addresses. Collaborators can change important marketplace presentation settings, although OpenSea restricts earnings settings to the collection owner.

Publish the changes, then inspect the public collection page while signed out. Confirm the contract address, chain, external links, images, item count, traits, and live-media behavior.

If token images or metadata are stale, first verify the 256ART live view and `tokenURI`. A marketplace cache problem is different from an on-chain metadata problem. Use OpenSea's refresh tools or support guidance rather than redeploying or changing the artwork without diagnosing the source.

### Creator Earnings

Creator earnings are a percentage paid from a secondary sale when the marketplace and transfer path honor the setting. They are not the same as the primary mint split and are never guaranteed merely because a percentage appears on a marketplace page.

In OpenSea Studio:

1. Select the deployed collection.
2. Open **Creator Earnings**.
3. Enter the percentage and recipient that correspond to the released 256ART royalty configuration.
4. Verify the full recipient address. Depending on the release, it may be a Royalty Splitter contract rather than your personal wallet.
5. Save the optional earnings settings.

Only the collection owner can change OpenSea creator-earnings recipients and percentages. OpenSea currently caps creator earnings at **10%**. Keep the marketplace value aligned with the contract and [Artwork Details Form](/artist-documentation/artwork-details-form/#secondary-royalty-percentage). If you are unsure which recipient to use, confirm it in the deployment records or ask the 256ART team before publishing.

#### Enforceability of Creator Earnings

Current 256ART contracts can support optional [ERC721-C creator-earnings enforcement](https://docs.opensea.io/docs/creator-fee-enforcement). For a compatible custom contract, OpenSea shows an **Enforce earnings** action in the Creator Earnings settings. The owner must complete OpenSea's wallet-signature flow to configure it.

Enforcement has important trade-offs:

- it restricts sales to transfer paths and marketplaces that comply with the configured ERC721-C policy;
- marketplaces that do not support that policy may be unable to trade the tokens;
- existing listings or offers may become invalid and need to be recreated; and
- removing or changing enforcement later can require another configuration step.

If **Enforce earnings** is absent, do not try to make the collection compatible by calling unfamiliar contract functions. Confirm that you selected the correct owner wallet and contract, then contact OpenSea or the 256ART team.

Without enforcement, OpenSea treats creator earnings as optional, and the seller chooses whether to include them. Other marketplaces have their own rules. With enforcement, royalties are enforced only through compatible transfer policies; it is not a promise that every marketplace will support trading.

---

## Summary

Use OpenSea Studio to configure the marketplace presentation and creator earnings for the already deployed 256ART contract. Verify the contract, owner, royalty recipient, and percentage; understand the trading restrictions before enabling ERC721-C enforcement; and recheck the public collection after every update.

For release-contract management outside OpenSea, return to [Releasing Your Artwork](/artist-documentation/releasing-your-artwork/#post-release).
