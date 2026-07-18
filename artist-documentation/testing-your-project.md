# Testing Your Project

### Testing for Release

Every project must pass the Artist Portal test before it can be released on Ethereum, Base, or Shape. The test deploys and mints the project in a controlled Sepolia-based environment, allowing you to inspect the contract output without paying production-network gas.

Before starting:

- complete and save the [Artwork Details Form](/artist-documentation/artwork-details-form/);
- run the artwork locally across many seeds and dimensions;
- validate and minify `artwork.js` and `traits.json`;
- confirm every selected library and version;
- check `window.rendered` preview signaling; and
- review names, descriptions, license, tags, supply, sale, seed, allowlist, owner, payout, and royalty settings.

### How Does It Work Behind the Scenes?

256ART uses Hardhat, an Ethereum development environment, with blockchain state available to its backend test system. The process deploys the project's contracts, mints a token, and calls the same contract interfaces used to build metadata and live artwork.

This is a close functional test, not a guarantee of identical mainnet behavior. Production gas prices, block data, third-party marketplace behavior, browser performance, and future network conditions can differ. Treat the result as one required layer of testing rather than a substitute for reviewing your code and configuration.

### Initiating the Test

1. Open the [Artist Portal](https://256.art/artistportal).
2. Select the unreleased project.
3. Confirm that its [Artwork Details Form](/artist-documentation/artwork-details-form/) is complete and saved.
4. Open **Test Project**.
5. Select **Test Project** to begin.
6. Keep the testing terminal open and monitor each step.

Do not edit the project while a test is running. If you change the artwork file, traits, libraries, or contract configuration after a successful test, run the test again.

### Understanding the Testing Process

The test checks:

1. deployment of the project's smart contracts;
2. minting of a test token;
3. retrieval of the token's `tokenURI`;
4. construction of the metadata and on-chain live view; and
5. generation and display of static image previews.

It also provides deployment-cost information based on the tested contracts. Treat this as an estimate: the amount paid on release depends on the selected chain and gas conditions when each transaction is submitted.

### Monitoring the Test Progress

The terminal displays progress, successes, warnings, and errors. Read the first relevant error rather than relying only on the final status; later failures can be consequences of an earlier problem.

Common areas to inspect include invalid JSON, incorrect trait weights or value types, missing libraries, JavaScript errors, a render that never sets `window.rendered`, timeouts, blank previews, file-size limits, and insufficient contract-size headroom.

If a message is unclear, save the complete output before restarting and share it with the 256ART team through [Discord](https://discord.gg/wpzVRdcjns).

### Reviewing the Test Results

After a successful run, review the result as if you were a collector:

- confirm the name, artist, description, license, token ID, and traits;
- open the live view and check the intended rendering, animation, interaction, and sound;
- inspect the static preview for cropping, blank areas, and completion using the [live-versus-preview validation guide](https://256.art/learn/live-artwork-vs-preview);
- confirm through [deterministic testing](https://256.art/learn/deterministic-generative-art) that the same seed gives the same base output;
- for dynamic work, test the expected state changes and fallback behavior; and
- review the deployment-cost estimate and contract summary.

If anything is wrong, return to the source or form, correct it, and run a new test. When the output is correct, select **I declare results are as expected**. This declaration records your approval; it does not replace your responsibility to verify the release settings.

### Benefits of Using Our Testing Feature

The built-in test lets you:

- exercise the complete deployment and mint path without production gas;
- catch contract, metadata, rendering, and preview errors before release;
- estimate deployment cost; and
- review the collector-facing result in one workflow.

A successful test is required, but it does not make a deployed contract reversible. Continue with [Releasing Your Artwork](/artist-documentation/releasing-your-artwork/) and complete the final review before signing any production transaction.
