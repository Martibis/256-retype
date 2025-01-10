---
order: 75
---
# Releasing Your Artwork
Releasing your artwork is the final step before going live with your artwork. It involves deploying your smart contracts and setting up the details for your artwork launch.

### Information Verification
In the release step, you will see a brief overview of your artwork details. Please carefully verify this information, if all is correct continue.

### Deploying Your Smart Contracts
The next step is to deploy your smart contracts. Depending on the size of your ArtScript, there could be one or more smart contracts for it:
- **Art Info Contract**: This contract holds crucial information about your artwork, such as your name, the license of your work, and a brief description of your artwork.
- **ArtScript Contract(s)**: These contracts contain your ArtScript. To significantly reduce the cost of deployment, we gzip and base64 encode your ArtScript before deploying it on the blockchain. During the live view from the chain, we gunzip the ArtScript and inject it into the HTML page. Due to a size limit of 24KB of bytecode per smart contract, your ArtScript may be split across multiple contracts.
- **Royalty Splitter Contract**: This contract ensures that you receive your fair share from secondary sales royalties.

### Selecting Your Release Dates
With these smart contracts successfully deployed, the next step is setting up your release dates.
- **Release Date**: This is the date your artwork will be publicly available for minting.
- **Allow List Date**: If you've created an allow list of addresses that can mint your artwork before the general public, you'll need to specify the allowlist minting date. Remember, the allow list mint closes as soon as the public mint begins.
- **End Date**: If your art release is an open edition, you can also set an end date.

Once you've confirmed these dates, you can click on 'Release Artwork'. If all goes as planned, your final contract will be deployed, marking the official launch of your artwork. You will then be redirected to your artwork's page.

### Post-Release
After releasing your artwork, there are several post-release functions that you can perform. These include:
- **Artist Mint**: mint tokens to yourself or friends for free (only when no dutch auction is in progress and the max supply has not been reached).

- **Withdrawing Funds from the Main Contract**: After your work is minted and sold, the funds are stored in the main contract. You can withdraw these funds.
  
- **Withdrawing Funds from the Royalty Splitter Contract**: If secondary sales occur and royalties are paid, these royalties are sent to the royalty splitter contract. You can withdraw these funds.

- **Updating the Max Supply**: In the event that a series doesn't mint out, you can adjust the max supply to a lower value (though it can't be less than the current token supply).

- **Updating the Image Base URL**: You can modify the base URL for the images associated with your tokens to update or correct the artwork display. This is particularly useful if you wish to self-host your images or use IPFS hosting, ensuring that your previews remain accessible even if the platform encounters issues.

- **Updating Royalty Information**:
  - **Royalty Percentage**: Adjust the royalty percentage for secondary sales to reflect any changes in your revenue model.

- **Requesting Updates to Merkle Root, ArtScripts, and ArtLibraries**:
  - **Merkle Root**: Modifying the allowlist's Merkle Root requires backend processing to generate and verify the new Merkle Tree. 
  - **ArtScripts and ArtLibraries**: Updating ArtScripts or ArtLibraries involves compressing, encoding, and ensuring compatibility with EthFS and other dependencies.

  **_Warning:_** *These updates can be performed directly by artists through the smart contract interface, but we recommend reaching out to us for assistance.*

- **Future Tools**:
  - We are actively working on integrating tools into our platform to make managing these settings more accessible and user-friendly. Stay tuned for updates!

Currently, all of these actions are performed directly through the smart contracts themselves. We're working on integrating this functionality into our front-end to make it more accessible. For the time being, we'll provide guidance on withdrawing funds from contracts and updating artwork details.

**Note**: If you're unfamiliar with interacting with smart contracts or have any questions, please contact a member of the 256ART team via our [Discord](https://discord.gg/wpzVRdcjns) channel.

### Withdrawing Funds

To withdraw funds from the main contract or the royalty splitter contract, you will need to interact directly with the smart contract on Etherscan. Here's a step-by-step guide:

1. **Navigate to Your Contract on Etherscan**:
   - Go to [Etherscan](https://etherscan.io/) and enter your contract's address in the search bar.

2. **Connect Your Wallet**:
   - Ensure that the wallet connected is the one set as the owner of the contract.
   - Click on the "Connect to Web3" button, usually found in the top right corner of the Etherscan interface.

3. **Access the 'Write Contract' Tab**:
   - Once connected, navigate to the 'Write Contract' tab to access the contract's functions.

4. **Locate the 'withdraw' Function**:
   - Scroll through the list of functions until you find the `withdraw` function.

5. **Execute the Withdrawal**:
   - Click on the `withdraw` function.
   - Enter any required parameters if prompted (usually none for a simple withdrawal).
   - Click the 'Write' button to initiate the transaction. This will trigger a transaction request in your connected wallet.

6. **Confirm the Transaction**:
   - Review the transaction details in your wallet.
   - Confirm and authorize the transaction to withdraw the funds to your wallet.

7. **Verify the Withdrawal**:
   - After the transaction is confirmed on the blockchain, verify that the funds have been transferred to your wallet.

Please reach out to our team via [Discord](https://discord.gg/wpzVRdcjns) if you need any assistance with this process. We're here to help!

### Updating Artwork Settings

To update artwork settings such as the image base URL and royalty percentage, follow these steps:

1. **Navigate to Your Contract on Etherscan**:
   - Go to [Etherscan](https://etherscan.io/) and enter your contract's address in the search bar.

2. **Connect Your Wallet**:
   - Ensure that the wallet connected is the one set as the owner of the contract.
   - Click on the "Connect to Web3" button.

3. **Access the 'Write Contract' Tab**:
   - Navigate to the 'Write Contract' tab to access the contract's functions.

4. **Locate the Relevant Setter Functions**:
   - **Set Image Base URL**: Find the `setImageBase` function to update the image base URL.
   - **Set Royalty Percentage**: Use the `setRoyalty` function to adjust the royalty percentage.

   **_Important:_** 
   - **Merkle Root, ArtScripts, and ArtLibraries**: These settings cannot be updated directly by artists. To request changes, please contact the 256ART team via our [Discord](https://discord.gg/wpzVRdcjns) channel.

5. **Execute the Desired Function**:
   - Click on the function you wish to execute.
   - Enter the necessary parameters as prompted.
   - Click the 'Write' button to initiate the transaction.

6. **Confirm the Transaction**:
   - Review the transaction details in your wallet.
   - Confirm and authorize the transaction.

**Important Considerations**:
- **Gas Fees**: Updating contract settings requires gas. Ensure you have sufficient ETH in your wallet to cover transaction fees.
- **Immutability**: While many settings are adjustable, most core artwork and smartcontract parameters remain immutable post-deployment.

For detailed assistance or if you encounter any issues, please contact the 256ART team via our [Discord](https://discord.gg/wpzVRdcjns) channel.
