---
order: 90
---

# Generative Art Template

Use the official template as the starting point for a 256ART release. The two files you prepare for upload are:

- `artwork.js` or `artwork-p5.js`: the JavaScript that renders the artwork; and
- `traits.json`: the trait definitions stored and assigned on-chain.

The template supplies local test data through `inputData`, loads your traits, and runs the artwork in a browser. It approximates the data provided by a deployed 256ART contract, but local testing does not replace the Artist Portal's [pre-release test](/artist-documentation/testing-your-project/).

Before you begin, you should be comfortable editing JavaScript and running a local web server. You do not need a bundler. If you use p5.js or another library, read [Available Libraries](#available-libraries) before building around it.

A practical workflow is:

1. Download or clone the template.
2. Run it through a local web server.
3. Build the artwork and traits.
4. Test many seeds, trait combinations, screen sizes, and browser conditions.
5. Signal when each render is complete with `window.rendered`.
6. Minify the final artwork and trait files.
7. Upload them in the [Artwork Details Form](/artist-documentation/artwork-details-form/).
8. Run the Artist Portal test before deployment.

### Random class

Use [deterministic randomness](https://256.art/learn/deterministic-generative-art) so the same token hash always reconstructs the same base output. The template's `Random` class seeds its pseudo-random number generator from `inputData.hash`. Do not use `Math.random()` for decisions that must remain consistent between renders.

Create one generator in a predictable place and call its methods in a consistent order. Adding or removing an early random call later can change every value that follows, so lock the algorithm before release and retest after any code change. You may remove helper methods you do not use.

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

Thanks to [Piter Pasma](https://twitter.com/piterpasma) for feedback on this pseudo-random number generator (PRNG).

### Dimension Agnostic Coding

Collectors may render the work on a phone, desktop monitor, projection, or high-resolution export. Keep a fixed aspect ratio if the composition requires one, but calculate the actual canvas dimensions from the available viewport.

Scale positions, line widths, type sizes, and other measurements from the canvas width or height rather than fixed pixels. In vanilla canvas code, account for `window.devicePixelRatio` so the output remains sharp:

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

Test very small and very large viewports, portrait and landscape windows, and the intended aspect ratio. Make sure resizing does not accidentally choose a new random sequence or change a token's base composition.

### GitHub Repository

[github.com/Martibis/256ART-generative-art-template](https://github.com/Martibis/256ART-generative-art-template)

### Using the Template Artwork

Clone or download the [256ART Generative Art Template repository](https://github.com/Martibis/256ART-generative-art-template), then follow its current [README](https://github.com/Martibis/256ART-generative-art-template/blob/main/README.md).

The repository includes:

- `scripts/artwork.js`: the vanilla JavaScript example.
- `scripts/artwork-p5.js`: the p5.js example.
- `scripts/traits.json`: example trait definitions.
- `dependencies/inputData.js`: the local emulator that creates `inputData` and loads the artwork. Do not modify this file.
- `index.html`: the local artwork viewer.
- `batch-generator.html`: a tool for rendering many test outputs.

Serve the repository through a local HTTP server; opening `index.html` directly with a `file://` URL can prevent the browser from loading `traits.json`. For example, you can use a local-server extension in your editor.

The final upload uses the completed and minified artwork file plus `traits.json`, not the template's HTML or local emulator.

### Customizing the Template

Implement the artwork in either `artwork.js` or `artwork-p5.js`. Remove unused example code, keep the output dimension agnostic, and use the deterministic `Random` class for repeatable variation.

Define only the traits that should appear in the token metadata in `traits.json`. For each trait:

- `trait_description` and `trait_value` must be strings;
- `weight` is a cumulative threshold on a 0–10,000 scale;
- thresholds must increase, and the final option should end at `10000`; and
- one on-chain trait cannot depend on the selected value of another trait.

For example, thresholds of `2000`, `7000`, and `10000` produce approximate probabilities of 20%, 50%, and 30%.

The template adds each selected trait to `inputData`. Access the value from your artwork code and explicitly parse it when you need a number or boolean:

```javascript
function draw() {
  let color = inputData["Paint Color"].value; // Access the Paint Color trait value defined in traits.json

  // Example usage: Set the background color using the Paint Color value
  background(color);
}
```

### Available Libraries

Only use a library that 256ART can retrieve from [EthFS](https://ethfs.xyz/) and that is available for selection in the Artist Portal. EthFS stores reusable web files on-chain. An arbitrary npm package or CDN URL used during development will not automatically become part of the on-chain release.

During local development, load the matching library version in `index.html`. In the Artwork Details Form, select that same library and version so the live contract render receives compatible code.

Use as few libraries as practical. Large libraries increase retrieval and rendering time, and version differences can change the output. Check the current EthFS/Artist Portal list rather than relying on an old version list in documentation. If a required library is missing, contact the 256ART team before completing the project; storing a new library on-chain can be expensive.

### Image Preview Generation for 256ART

256ART needs to know when the canvas is ready to capture. Assign the completed canvas element to `window.rendered` only after the intended preview frame has finished rendering:

```
window.rendered = canvas;
```

For p5.js, `createCanvas` returns a renderer. Assign its underlying canvas:

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

If the work loads assets or builds its composition asynchronously, do not set `window.rendered` until those steps are complete. Setting it too early can create blank or partial previews; never setting it can cause preview generation to time out.

The resulting static image is used by 256ART, galleries, and marketplaces that cannot efficiently run every live artwork. It does not replace the fully on-chain live render, which is exposed separately in the token metadata. See [Live Generative Artwork vs Preview Image](https://256.art/learn/live-artwork-vs-preview).

### Batch Artwork Generator

Use `batch-generator.html` to inspect many seeds before upload. A single successful output is not enough to validate a generative system: uncommon traits, edge combinations, and rendering-time problems may appear only in a larger sample.

#### Features

- **Batch generation**: create multiple test outputs in one run.
- **Custom image size**: test the width and height used for each output.
- **Progress monitoring**: follow generation and identify timeouts.
- **ZIP download**: save the generated previews for review.

#### How to Use

1. Start the template with a local web server.
2. Open `batch-generator.html` from that server.
3. Enter the batch size and image dimensions.
4. Select **Start Batch** and watch for errors or unusually slow renders.
5. Select **Download All as ZIP** if you want to review the outputs outside the browser.

Review the batch for visual errors, unexpectedly common or missing traits, duplicate-looking compositions, clipping, blank frames, and inconsistent aspect ratios. Repeat at different dimensions. The batch generator improves coverage but does not prove the probabilities or code are correct; inspect the console and validate `traits.json` separately.

### Creating Dynamic Artworks

An artwork is **[dynamic](https://256.art/learn/256art-dynamic-art)** when its live output responds to blockchain state that can change after minting. For example, it can react to a transfer, the current block, total minted supply, or the owner's balance.

`inputData.tokenId` and `inputData.hash` identify the token and its original seed. They remain the foundation for a repeatable base composition. The dynamic parameters below describe state at the time the live HTML is requested, so using them can intentionally change later renders.

#### Available Blockchain Parameters

The current template emulates these values in `inputData`:

- `tokenId`: the token's numeric ID.
- `hash`: the token's fixed seed as a hexadecimal string.
- `ownerOfPiece`: the current owner's hexadecimal address.
- `blockHash`: the previous block's hash.
- `blockNumber`: the current block number.
- `blockTimestamp`: the current block timestamp in seconds.
- `blockBaseFee`: the current block's base fee in wei, the smallest ETH unit (`1 ETH = 10^18 wei`).
- `blockCoinbase`: the current block's fee-recipient address.
- `prevrandao`: the current block's randomness value.
- `totalSupply`: the number of tokens currently minted in the series.
- `balanceOfOwner`: the number of tokens from this series held by the current owner.
- `ethBalanceOfOwner`: the current owner's native ETH balance in wei.

Contract generations can expose different subsets of dynamic values. Treat the Artist Portal's deployment test as the final compatibility check for your release, and do not make the artwork fail completely when an optional value is unavailable.

In the local template, URL overrides are strings while generated defaults are numbers; deployed contract generations can also differ. Inspect each value and its type in the Artist Portal test. A JavaScript `Number` above `Number.MAX_SAFE_INTEGER` may already have lost precision, and converting it to `BigInt` cannot recover the lost bits. Do not rely on exact full-width values unless the tested live interface supplies a decimal or hexadecimal string. The example below keeps full-width values as `BigInt`, clamps the wei balance, and reduces it to a safely sized visual value before converting to `Number`.

#### Accessing Blockchain Parameters

Here's how you can access and utilize these parameters within your artwork code:

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
  const ethBalanceWei = BigInt(inputData["ethBalanceOfOwner"].toString());

  // Example usage: Convert wei to ETH before mapping a 0–100 ETH visual range
  const weiPerEth = 10n ** 18n;
  const maxMappedWei = 100n * weiPerEth;
  const clampedWei = ethBalanceWei > maxMappedWei ? maxMappedWei : ethBalanceWei;
  const ethBalanceOfOwner = Number(clampedWei / 10n ** 15n) / 1000;
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

Test dynamic work with explicit URL parameters supported by the local template, for example `?blockNumber=123&totalSupply=64`. Test owner changes, zero values, large values, and missing optional values.

Remember that static marketplace previews show one captured state. Make the live behavior understandable and ensure the piece still has a useful preview. Explain important dynamic behavior in the artwork description so collectors know what can change.

When the files are complete, continue with the [Artwork Details Form](/artist-documentation/artwork-details-form/).
