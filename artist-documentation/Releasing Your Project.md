---
order: 75
---
# Releasing Your Project
Releasing your project is the final step before going live with your project. It involves deploying your smart contracts and setting up the details for your project launch.
### Project Verification and Acceptance of Terms
In the release step, you will see a brief overview of your project. To proceed, two checkboxes need to be marked in order to release:
- Information Verification: Review the project information displayed and ensure it's accurate. If everything is as it should be, check this box to confirm that your project information is correct.
- Terms of Service Acceptance: Read and understand our terms of service. If you agree to them, check this box to accept.
### Deploying Your Smart Contracts
The next step is to deploy your smart contracts. Depending on the size of your ArtScript, there could be one or more smart contracts for it:
- **Art Info Contract**: This contract holds crucial information about your project, such as your name, the license of your work, and a brief description of your project.
- **ArtScript Contract(s)**: These contracts contain your ArtScript. To significantly reduce the cost of deployment, we gzip and base64 encode your ArtScript before deploying it on the blockchain. During the live view from the chain, we gunzip the ArtScript and inject it into the HTML page. Due to a size limit of 24KB of bytecode per smart contract, your ArtScript may be split across multiple contracts.
- **Royalty Splitter Contract**: This contract ensures that you receive your fair share from secondary sales royalties.
### Selecting Your Release Dates
With these smart contracts successfully deployed, the next step is setting up your release dates.
- **Release Date**: This is the date your project will be publicly available for minting.
- **Allow List Date**: If you've created an allow list of addresses that can mint your project before the general public, you'll need to specify the date this list will take effect. Remember, the allow list mint closes as soon as the public mint begins.
- **End Date**: If your project is an open edition, you can also set an end date.

Once you've confirmed these dates, you can click on 'Release Project'. If all goes as planned, your final ERC721 contract will be deployed, marking the official launch of your project. You will then be redirected to your project page. Keep in mind we only show projects that are within a week of release to prevent spam.
### Post-Release
After releasing your project, there are several post-release functions that you can perform. These include:
- **Withdrawing funds from the main contract**: After your work is minted and sold, the funds are stored in the main contract. You can withdraw these funds.
- **Withdrawing funds from the royalty splitter contract**: If secondary sales happen and royalties are paid, these royalties are send to the royalty splitter contract. You can withdraw these funds.
- **Updating the max supply**: In the event that a series doesn't mint out, you can adjust the max supply to a lower value (though it can't be less than the current token supply). 
- **Updating ArtScripts and libraries**: Over time, certain functionalities may no longer be supported by libraries, browsers, etc. In these cases, you'll be able to update your ArtScripts and libraries to maintain compatibility.

Currently, all of these actions are performed directly through the smart contracts themselves. We're working on integrating this functionality into our front-end to make it more accessible. For the time being, we'll provide guidance on withdrawing funds from contracts.

**Note**: If you're unfamiliar with interacting with smart contracts or have any questions, please contact a member of the 256ART team via our Discord channel.

**Withdrawing Funds** 

To withdraw funds from the main contract or the royalty splitter contract, you will need to interact directly with the smart contract on Etherscan. Here's a step-by-step guide:
1. Navigate to your contract on Etherscan.
2. Connect your wallet (the one set as the owner of the contract) to Etherscan.
3. Go to the 'Write Contract' tab.
4. Click on the 'Connect to Web3' button.
5. Once connected, find the 'withdraw' function in the list of functions.
6. Click 'Write'. This will trigger a transaction request in your wallet.
7. Confirm the transaction to withdraw the funds to your wallet.

Please reach out to our team via Discord if you need any assistance with this process. We're here to help!

