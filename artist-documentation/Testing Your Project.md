---
order: 80
---

# Testing Your Project

### Testing for Release

Before you release your project, it has to be tested, this is to ensure that everything works as intended before deploying to the Ethereum, Base or Shape mainnet. We have built a testing feature that simplifies this process, allowing you to run tests on an emulation of the Sepolia network without incurring gas fees. This section will guide you through the testing process, explains how it works behind the scenes and will go into the benefits of using it.

### How Does It Work Behind the Scenes?

We use Hardhat, an Ethereum development environment, to run tests on top of an archival node on our back-end. This approach enables us to simulate how your project would function on the Ethereum, Base or Shape mainnet without paying gas fees. As a result, we can perform tests at no cost while still simulating the actual network conditions.

### Initiating the Test

To initiate the testing process, go to the [artist portal](https://256.art/artistportal) and click on one of your unreleased projects. Make sure the project details form is filled out [Project Details Form](/artist-documentation/project-details-form). Once you have completed the form, navigate to "Test Project" and click the "Test Project" button. This will start the test, and show the testing terminal that displays the test progress, results, and any errors that may occur.

### Understanding the Testing Process

The following is tested:

1. Deployment of your project's smart contract.
2. Minting of one artwork.
3. Retrieving the tokenURI for the minted artwork.
4. Displaying the metadata, live view, and image previews of the minted artwork.

### Monitoring the Test Progress

As the test progresses, you will receive real-time updates through the testing interface. The interface will display terminal messages, success messages, error messages, and other relevant information as the test proceeds. Keep an eye on these messages to monitor the progress and identify any issues that may arise.

### Reviewing the Test Results

Once the test is complete, you can review the results to ensure that the metadata and visual elements of the minted artwork are correct and match your expectations. If the test identifies any issues, you can address them before releasing your project. If the test is successful and you are satisfied with the results, you can proceed to release your project by clicking the "I declare results are as expected" button.

### Benefits of Using Our Testing Feature

By using our built-in testing feature, you can:

- Test your project in a real-world environment without incurring gas fees.
- Easily identify potential issues or improvements.
- Obtain accurate cost estimates for deploying the project
- Verify that the metadata, live view, and image previews of a minted artwork are correct.
