# Releasing Your Artwork

Releasing deploys the production smart contracts and schedules the mint. Deployment creates permanent on-chain records and costs gas, so complete the [Artist Portal test](/artist-documentation/testing-your-project/) and review every setting before signing.

Use the wallet intended to submit the deployment transactions, switch it to the selected chain, and make sure it has enough ETH for the estimated cost plus a margin for gas changes. Ethereum, Base, and Shape are separate networks.

### Information Verification

The release step shows a summary of the saved artwork and contract configuration. Compare it with your source files and release plan.

Check at minimum:

- artwork name, artist, descriptions, license, and tags;
- target chain;
- `artwork.js`, `traits.json`, and selected libraries;
- sales and seeding mechanisms;
- collection size or Open Edition settings;
- reserve, public, and allowlist prices;
- allowlist and per-address limit;
- owner and every payout address;
- primary and secondary revenue percentages; and
- royalty percentage and enforcement choice.

Do not continue if an address is truncated and you have not verified the full value. If you change a tested file or setting, save it and rerun the required test before release.

### Deploying Your Smart Contracts

256ART separates release data across contracts. Depending on the release and script size, you may deploy:

- **Art Info Contract**: stores core information such as the artist, artwork name, license, and short description.
- **ArtScript Contract(s)**: stores the compressed artwork code. 256ART gzip-compresses and encodes the script, then reconstructs it for the live HTML. Because Ethereum, Base, and Shape limit the deployed code size of one contract, a larger script may require more than one ArtScript contract.
- **Royalty Splitter Contract**: distributes paid secondary royalties according to the configured secondary split.
- **Main collection contract**: creates and manages the ERC-721 tokens, sale, metadata, and live-render interfaces.

The portal may request multiple wallet transactions. For each one:

1. confirm that you are on the intended network;
2. verify that the request comes from `256.art`;
3. review the value and gas estimate;
4. submit it once; and
5. wait for confirmation before continuing.

Do not close the workflow or submit a duplicate transaction merely because confirmation is slow. Check the pending transaction in your wallet or block explorer.

### Selecting Your Release Dates

After the supporting contracts are deployed, configure the sale schedule:

- **Release Date**: when the public mint opens.
- **Allow List Date**: when approved addresses can begin minting. The allowlist phase ends when the public mint opens.
- **End Date**: when an Open Edition closes.

Check the timezone displayed by the portal and communicate dates with an explicit timezone. Make sure the allowlist date precedes the public release and that an Open Edition end date follows it.

Select **Release Artwork** only after this final check. The portal deploys the main collection contract and then redirects to the artwork page.

Save the collection address and transaction links. On the artwork page, verify the chain, status, schedule, prices, supply, and collector-facing text. If the public mint is scheduled for later, the contract is deployed even though minting is not yet open.

### Post-Release

The released contract may expose owner-only administrative functions. Available functions vary by contract generation and sale type.

- **Artist Mint**: mint without the public mint price to an address, where supported. This is unavailable while a Fair Dutch Auction is active and cannot exceed the maximum supply. The transaction still costs gas.
- **Withdraw primary funds**: distribute sale proceeds held by the main contract.
- **Withdraw secondary royalties**: distribute paid royalties held by the Royalty Splitter.
- **Reduce max supply**: lower an unsold collection's maximum where supported. It cannot be set below the number already minted.
- **Update image base URL**: change where static token preview images are loaded from. This affects the metadata's convenience image, not the on-chain live artwork or its seed.
- **Update royalty information**: change supported royalty settings. Marketplace listings and enforcement configuration may also need to be refreshed.
- **Update allowlist data**: a new address list requires a new Merkle tree and root.
- **Update ArtScripts or ArtLibraries**: these are high-impact changes to the code used for live rendering and require compression, storage, and compatibility checks.

Do not assume that every item can be changed directly or safely. In particular, allowlist, ArtScript, and ArtLibrary changes can depend on backend preparation and the exact contract. Contact the 256ART team through [Discord](https://discord.gg/wpzVRdcjns) before attempting them.

Owner-only changes are blockchain transactions: they cost gas, are publicly recorded, and may affect every token. Read the contract function and parameters, simulate or verify the action where possible, and never use a write function you do not understand.

### Withdrawing Funds

Primary funds and secondary royalties can be held in different contracts, so check and withdraw them separately.

1. Copy the relevant contract address from the Artist Portal or confirmed deployment transaction.
2. Open it on the explorer for its chain:
   - [Etherscan](https://etherscan.io/) for Ethereum
   - [BaseScan](https://basescan.org/) for Base
   - [Shapescan](https://shapescan.xyz/) for Shape
3. Verify the address and contract name before connecting a wallet.
4. On Etherscan or BaseScan, open **Contract** and then **Write Contract** or **Write as Proxy**. On Shapescan's Blockscout interface, open the verified **Contract** tab and use **Read/Write Contract** or **Read/Write Proxy**. If these controls are absent, stop rather than supplying a custom ABI.
5. Connect the owner wallet and make sure it is on the correct network.
6. Find `withdraw`, read its inputs, and submit it only on the intended main or Royalty Splitter contract.
7. Review and confirm the wallet transaction.
8. After confirmation, inspect the transaction's transfers and the receiving addresses.

A withdrawal executes the configured split; it is not necessarily a transfer of the full balance to the connected wallet. If the function, contract, or expected receivers are unclear, stop and contact the 256ART team through [Discord](https://discord.gg/wpzVRdcjns).

### Updating Artwork Settings

Use the same network-specific explorer and owner-wallet checks described above.

1. Open the verified collection contract.
2. Review current values through **Read Contract** on Etherscan or BaseScan, or the read controls in Shapescan's **Read/Write Contract** view.
3. Open the corresponding write interface described in the withdrawal steps above.
4. Locate the relevant owner-only function. Depending on the contract, image and royalty setters may appear as `setImageBase` and `setRoyalty`.
5. Confirm the expected parameter format from the verified contract source or 256ART guidance.
6. Submit the transaction and verify the new value after confirmation.

For an image base URL, confirm whether the contract appends a token ID and whether the URL requires a trailing slash or filename pattern. Test several resulting preview URLs before updating it. The on-chain `animation_url` and artwork code remain separate from this static image setting.

For royalty changes, review the Royalty Splitter and marketplace configuration as well as the collection contract. An on-chain percentage change does not guarantee that every marketplace will pay or immediately display the new value.

**Important considerations:**

- **Gas**: every write requires the network's native ETH.
- **Authorization**: only the configured owner can call owner-only functions.
- **Immutability**: many core release values cannot be changed after deployment.
- **Contract variation**: function names and available updates can differ between releases.
- **Security**: use the official explorer domain and verify the contract address; block-explorer write actions are real transactions.

For Merkle root, ArtScript, ArtLibrary, or any uncertain change, contact the 256ART team through [Discord](https://discord.gg/wpzVRdcjns) before submitting a transaction.

If you plan to list the collection on OpenSea, continue with [OpenSea & Enforcing Royalties](/artist-documentation/opensea-enforcing-royalties/).
