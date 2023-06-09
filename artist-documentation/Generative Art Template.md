---
order: 90
---

# Generative Art Template

When creating a generative art project that you want to release on 256ART it’s recommended to use the below template as a starting point. With 256ART we simplify the development process compared to other platforms by requiring only one artwork.js file (for rendering your art) and a simple traits.json file for defining traits. Our template also emulates everything exactly the same ways as it would be if deployed live on the Ethereum mainnet.

### Random class

We very strongly recommend using our Random class, which is an improved version of the Random class provided by ArtBlocks. You can remove functionality you don't need.

```javascript
class Random {
    constructor() {
        let offset = 0;
        for (let i = 2; i < 66; i += 8) offset += parseInt(inputData.hash.substr(i, 8), 16);
        offset %= 7;

        const p = pos => parseInt(inputData.hash.substr((pos + offset), 8), 16);
        let a = p(2) ^ p(34), b = p(10) ^ p(42), c = p(18) ^ p(50), d = p(26) ^ p(58) ^ p(2 + (8 - offset));

        this.r = () => {
            a |= 0; b |= 0; c |= 0; d |= 0;
            let t = (((a + b) | 0) + d) | 0;
            d = (d + 1) | 0; a = b ^ (b >>> 9);
            b = (c + (c << 3)) | 0; c = (c << 21) | (c >>> 11);
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

function draw(){
    let w = c.width; // Width of canvas
    let h = c.height; // Height of canvas
    
    let strokeWidth = w * 0.001; // Scale using the canvas width
}
```

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