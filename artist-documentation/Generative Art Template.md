---
order: 90
---

# Generative Art Template

When creating a generative artwork that you want to release on 256ART it’s recommended to use the below template as a starting point. With 256ART we simplify the development process compared to other platforms by requiring only one artwork.js file (for rendering your art) and a simple traits.json file for defining traits. Our template also emulates everything exactly the same ways as it would be if deployed live on the Ethereum, Base or Shape mainnet.

### Random class

We very strongly recommend using our Random class, which is an improved version of the Random class provided by ArtBlocks. You can remove functionality you don't need.

```javascript
class Random {
  constructor() {
    let offset = 0;
    for (let i = 2; i < 66; i += 8)
      offset += parseInt(inputData.hash.substr(i, 8), 16);
    offset %= 7;

    const p = (pos) => parseInt(inputData.hash.substr(pos + offset, 8), 16);
    let a = p(2) ^ p(34),
      b = p(10) ^ p(42),
      c = p(18) ^ p(50),
      d = p(26) ^ p(58) ^ p(2 + (8 - offset));

    this.r = () => {
      a |= 0;
      b |= 0;
      c |= 0;
      d |= 0;
      let t = (((a + b) | 0) + d) | 0;
      d = (d + 1) | 0;
      a = b ^ (b >>> 9);
      b = (c + (c << 3)) | 0;
      c = (c << 21) | (c >>> 11);
      c = (c + t) | 0;
      return (t >>> 0) / 4294967296;
    };
    // 256 warmup cycles
    for (let i = 0; i < 256; i++) this.r();
  }
  // Random decimal [0, 1)
  random_dec = () => this.r();
  // Random number [a, b)
  random_num = (a, b) => a + (b - a) * this.random_dec();
  // Random integer [a, b] (a < b required)
  random_int = (a, b) => Math.floor(this.random_num(a, b + 1));
  // Random boolean (p = true probability)
  random_bool = (p) => this.random_dec() < p;
  // Choose random item from array
  random_choice = (list) => list[this.random_int(0, list.length - 1)];
}
```

Shoutout to [Piter Pasma](https://twitter.com/piterpasma) for providing feedback on the PRNG.

### Dimension Agnostic Coding

Your artwork should scale seamlessly to any dimension, regardless of the viewer's browser size or resolution. We will also render a still image of the output at 2048x2048. Here's an example of how to achieve dimension agnostic coding:

```javascript
let c = document.createElement("canvas"); // Create canvas
function setup() {
  let dp = window.devicePixelRatio; // Get device pixel ratio; not needed in p5js
  let ih = window.innerHeight * dp; // Get window innerHeight
  let iw = window.innerWidth * dp; // Get window innerWidth

  // Scale correctly
  if (ih / iw < aspectRatio) {
    c.height = ih;
    c.width = ih / aspectRatio;
  } else {
    c.width = iw;
    c.height = iw * aspectRatio;
  }

  document.body.appendChild(c); // Add canvas to body
}

function draw() {
  let w = c.width; // Width of canvas
  let h = c.height; // Height of canvas

  let strokeWidth = w * 0.001; // Scale using the canvas width
}
```

### GitHub Repository

https://github.com/Martibis/256ART-generative-art-template

### Using the Template Artwork

Clone or download the [256ART Generative Art Template repository](https://github.com/Martibis/256ART-generative-art-template) to begin. This template provides a starting point for creating generative art that can be released fully in-chain via 256ART. The main files you will be working with are:

- `artwork.js` or `artwork-p5.js`: Contains the code for generating your generative art.
- `traits.json`: Defines the traits that should be stored on-chain.

Follow the instructions in the [readme.md](https://github.com/Martibis/256ART-generative-art-template/blob/main/README.md) file to get started.

### Customizing the Template

Modify the `artwork.js` / `artwork-p5.js` file to implement your desired artwork. Make sure the output is dimension agnostic, meaning it scales seamlessly to any dimension. Define a default dimension and create a multiplier to scale coordinates or sizes relative to the canvas dimensions.

Modify the `traits.json` file for the traits for your generative artwork. Keep in mind that `traits.json` is only for the traits you would like to store on the blockchain. These traits cannot depend on the values of other traits.

Access the traits defined in `traits.json` from `artwork.js` / `artwork-p5.js` using the inputData object. For example, if you defined a trait for "Paint Color" in traits.json, you could access this trait value in your code like this:

```javascript
function draw() {
  let color = inputData["Paint Color"].value; // Access the Paint Color trait value defined in traits.json

  // Example usage: Set the background color using the Paint Color value
  background(color);
}
```

### Available Libraries

Only use libraries available on EthFS, as the libraries need to be available on chain. To use one of the available libraries during development, add a CDN to the library in the index.html file. We recommend using as few libraries as possible (getting large libraries from chain can significantly slow down getting your art from chain). Some of the libraries available on EthFS at the time of writing are:

- p5js v1.5.0
- Tone.js (version unknown)
- threejs v0.147.0

### Image Preview Generation for 256ART

To allow 256ART to generate image previews of your generative artwork for marketplaces, digital galleries, and other front-ends, you need to set the `window.rendered` property equal to the `canvas` object when the work is fully rendered. This way, 256ART can capture the generated canvas, create an image preview, and store it as part of the tokenURI in the ERC721 smart contract under the "image" property.

Make sure to add the following line of code in your `artwork.js` / `artwork-p5.js` file once the artwork is completely rendered:

```
window.rendered = canvas;
```

For example, in a p5js sketch, you could add the `window.rendered = c.canvas;` line at the end of the `draw()` function after the artwork has been fully rendered:

```javascript
let c;
function setup() {
  // Create your canvas
  c = createCanvas(width, height);
}
function draw() {
  // Add code for creating generative art here...

  // Set window.rendered to the canvas object when artwork is fully rendered
  window.rendered = c.canvas;
}
```

By setting the `window.rendered` property, you are providing 256ART with a signal to capture the rendered canvas and generate an image preview. Providing image previews is needed for front-ends as they may not be able to render multiple "live rendering" of the art script, especially when the artworks are resource-intensive. The image previews make it easier for front-ends to display your generative art without the performance overhead of rendering the artwork live.

### Batch Artwork Generator

When your `artwork-p5.js` or `artwork.js` and your `traits.json` are completed, you can use the batch artwork generator for testing purposes. The **Batch Artwork Generator** tool streamlines the creation of multiple previews. It allows you to specify the number of previews and their dimensions, generates them efficiently, and provides an option to download all images as a ZIP file.

#### Features

- **Batch Generation:** Create multiple artworks in one go.
- **Customizable Image Size:** Define the width and height for each image.
- **Progress Monitoring:** Visual progress bar to track generation.
- **Download as ZIP:** Easily download all generated images together.

#### How to Use

1. **Open the Generator:**

   - Navigate to `batch-generator.html` in your browser. Ensure it's served from a local server.

2. **Configure Parameters:**

   - **Batch Size:** Enter the number of artworks you wish to generate.
   - **Image Size:** Specify the desired size in pixels.

3. **Start Generation:**

   - Click the **Start Batch** button. The progress bar will indicate the generation status.

4. **Download Images:**
   - Once completed, click the **Download All as ZIP** button to download all generated artworks.

### Creating Dynamic Artworks

With 256ART exposing a variety of blockchain parameters through the `inputData` object, you can create generative artworks that respond to on-chain events and states. This allows your artwork to evolve based on actions such as transfers, sales, or changes in an owner's ETH balance. Below, we'll explore how to utilize these parameters to add dynamic behavior to your generative art.

#### Available Blockchain Parameters

The following blockchain parameters are available in `inputData`:

- `ownerOfPiece`: The hexadecimal address of the current owner of the token.
- `blockHash`: The hash of the previous block.
- `blockNumber`: The current block number.
- `blockTimestamp`: The timestamp of the current block.
- `blockBaseFee`: The base fee of the current block.
- `blockCoinbase`: The hexadecimal address of the block miner.
- `prevrandao`: The previous randomness value from the block.
- `totalSupply`: The total number of tokens minted.
- `balanceOfOwner`: The number of tokens owned by the current owner.
- `ethBalanceOfOwner`: The ETH balance of the current owner.

These parameters can be accessed in your `artwork.js` or `artwork-p5.js` file via the `inputData` object. Below are examples of how to incorporate these parameters into your artwork.

#### Accessing Blockchain Parameters

Here's how you can access and utilize the blockchain parameters within your artwork code:

```javascript
function draw() {
  // Accessing blockchain parameters from inputData
  const ownerAddress = inputData["ownerOfPiece"];
  const blockHash = inputData["blockHash"];
  const blockNumber = parseInt(inputData["blockNumber"]);
  const blockTimestamp = parseInt(inputData["blockTimestamp"]);
  const blockBaseFee = parseFloat(inputData["blockBaseFee"]);
  const blockCoinbase = inputData["blockCoinbase"];
  const prevrandao = parseInt(inputData["prevrandao"]);
  const totalSupply = parseInt(inputData["totalSupply"]);
  const balanceOfOwner = parseInt(inputData["balanceOfOwner"]);
  const ethBalanceOfOwner = parseFloat(inputData["ethBalanceOfOwner"]);

  // Example usage: Change background color based on ETH balance
  const colorIntensity = map(ethBalanceOfOwner, 0, 100, 0, 255);
  background(colorIntensity, 100, 150);

  // Example usage: Display owner address as part of the artwork
  fill(255);
  textSize(w * 0.02);
  text(`Owner: ${ownerAddress}`, 10, h - 20);

  // Example usage: Animate elements based on block number
  let angle = (blockNumber % 360) * (PI / 180);
  push();
  translate(w / 2, h / 2);
  rotate(angle);
  // Draw a rotating shape
  ellipse(0, 0, w * 0.3, h * 0.3);
  pop();

  // Additional dynamic elements can be added using other parameters
}
```
