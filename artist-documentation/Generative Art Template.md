---
order: 90
---

# Generative Art Template

When creating a generative art project that you want to release on 256ART it’s recommended to use the below template as a starting point. With 256ART we simplify the development process compared to other platforms by requiring only one artwork.js file (for rendering your art) and a simple traits.json file for defining traits. Our template also emulates everything exactly the same ways as it would be if deployed live on the Ethereum mainnet.

### GitHub Repository
https://github.com/Martibis/256ART-generative-art-template 

### Using the Template Project
Clone or download the [256ART Generative Art Template repository](https://github.com/Martibis/256ART-generative-art-template) to begin. This template provides a starting point for creating generative art that can be released fully in-chain via 256ART. The main files you will be working with are:
- `artwork.js` or `artwork-p5.js`: Contains the code for generating your generative art.
- `traits.json`: Defines the traits that should be stored on-chain.

Follow the instructions in the [readme.md](https://github.com/Martibis/256ART-generative-art-template/blob/main/README.md) file to get started.

### Customizing the Template
Modify the `artwork.js` / `artwork-p5.js` file to implement your desired artwork. Make sure the output is dimension agnostic, meaning it scales seamlessly to any dimension. Define a default dimension and create a multiplier to scale coordinates or sizes relative to the canvas dimensions.

Modify the `traits.json` file for the traits for your generative artwork. Keep in mind that `traits.json` is only for the traits you would like to store on the Ethereum blockchain. These traits cannot depend on the values of other traits.

Access the traits defined in `traits.json` from `artwork.js` / `artwork-p5.js`  using the inputData object. For example, if you defined a trait for color in traits.json, you could access this trait in your code like this:
```javascript
function draw() {
  let color = inputData.color; // Access the color trait defined in traits.json
  // Add code for creating generative art using the color trait...
}
```
### Available Libraries
Only use libraries available on EthFS, as the libraries need to be available on chain. To use one of the available libraries during development, add a CDN to the library in the index.html file. We recommend using as few libraries as possible (getting large libraries from chain can significantly slow down getting your art from chain). Some of the libraries available on EthFS at the time of writing are:
- p5js v1.5.0
- Tone.js (version unknown)
- threejs v0.147.0