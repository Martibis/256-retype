---
order: 90
---

# Collecting Art on 256ART

### How to Purchase Art

Purchasing art on 256ART involves interacting with a smart contract, via the "Mint" button. Here's the general process:

1. Navigate to the art series you are interested in.
2. Click the "Mint" button.
3. Your wallet will then ask you to confirm the transaction.

Once the transaction is confirmed, congratulations! You've just purchased your artwork(s) and can immediately view them from the blockchain.

### How to Get the Art Live from Chain

If you're interested in viewing the live version of your artwork directly from the blockchain, you can do so using Etherscan / Basescan / Shapescan:

1. Go to the contract of the artwork on Etherscan / Basescan / Shapescan
2. Access the `tokenHtml` function.
3. Enter your `tokenId`.
4. The output will be the base64 encoded live HTML of your artwork as it exists on-chain.
5. Copy paste the result in the address bar of your browser (all modern browsers).

If you want to view the entire metadata, you can use the same steps with the `tokenURI` function.
