---
order: 85
---

# Project Details Form

### Project name*
The name of your project, it should be unique and descriptive.
### Short description for the project*
A short description of your project. This description is stored on-chain, so it is recommended to keep it brief to reduce costs. The maximum character limit for this field is 1500 characters.
### Reserve price*
The reserve price or minimum price for your project. In the case of open-edition and fixed-price sales mechanisms, the price is the same as the reserve price. For Dutch Auction, the reserve price is used in the `currentPrice()` function in the smart contract to calculate the current price of the project during the auction, ensuring that you don’t have to worry about halftime or other complexities. The starting mint price is roughly 25 times higher than the reserve price and lowers every 7.5 minutes (divided by roughly 1.5x each time) over a one hour duration.
### Sales mechanism*
The sales mechanism for your project. There are three options: Fair Dutch Auction, Fixed Price, and Open Edition.
### Seeding mechanism*
The seeding mechanism for your project. There are two options: Random at Time of Mint and Collector Chooses Seed.
### Collection size*
The total number of NFTs in the collection. Only applicable when the sales mechanism is not Open Edition.
### Allow list addresses
The addresses you wish to add to your allow list. Allow-listed addresses will be able to mint before the public mint opens at the reserve price. There is a limit of one mint per wallet.
### Artwork.js*
The JavaScript code that generates the artwork. [Generative Art Template](/artist-documentation/generative-art-template)  for more info. 
### Traits.json*
The Traits.json file that contains the metadata for your artwork. This should be formatted in valid JSON format and should not exceed 20kb in size. [Generative Art Template](/artist-documentation/generative-art-template) for more info. 
### Project libraries*
The external libraries used in your project. Multiple libraries can be selected from the provided list, but we recommend using as few as possible (getting large libraries from chain can significantly slow down getting your art from chain).
### License*
The license for your project. Selecting an appropriate license helps clarify how the artwork can be used and shared by others.
### Ethereum Address*
The Ethereum address that will be the owner of the contract and will receive ETH from primary and secondary sales. A cold wallet is recommended for this purpose.
### Secondary royalty percentage*
The secondary royalty percentage that you will receive from secondary sales of your work. Please note that some marketplaces might not honor this, we recommend only linking to marketplaces that do.
### Tags
Relevant tags for your project. These tags will help collectors find your project more easily when searching and provide them with quick information on what to expect.
### Detailed story behind your project
The detailed story behind your project. This is an opportunity for you to provide more context about your artwork, its inspiration, and any other relevant information that would help potential collectors and viewers understand and appreciate the project more deeply.