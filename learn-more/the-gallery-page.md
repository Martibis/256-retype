# My collection

### Overview

[My collection](https://256.art/gallery) shows the 256ART tokens held by your connected wallet. Select a piece to open it large. From there you can:

- render an artwork live from its contract;
- view or download its high-resolution static preview; and
- request a new static preview if the current one did not render correctly.

The live artwork and static preview serve different purposes. **Live** runs the artist's on-chain code. The **High-res image** is a captured still image that is more convenient for downloads, thumbnails, and applications that cannot run the live code. See [Live Generative Artwork vs Preview Image](https://256.art/learn/live-artwork-vs-preview) for a detailed comparison.

### Opening My collection

1. Go to [256.art/gallery](https://256.art/gallery).
2. Select the option to connect your wallet.
3. Choose the wallet address that holds your 256ART pieces.
4. Approve the connection or sign-in message if your wallet asks.

A sign-in message proves that you control the wallet; it is not a blockchain transaction and should not require gas. Read the message before signing it.

If an expected piece is missing, confirm that the mint transaction succeeded and that you connected the receiving wallet rather than a different account. A newly confirmed mint may also take a short time to appear.

### Live

Choose **Live** under a piece, or open the piece and switch from **Still** to **Live**. 256ART reads the token's rendering data from its collection contract and runs the artist's code in the browser. **Full screen** shows it on its own.

This is the canonical live version of the piece. Animated, interactive, sound, or dynamic features may only be available in this view. Dynamic art can respond to current blockchain data, so its live appearance may change over time.

You can also retrieve the live HTML directly from a block explorer. See [How to get the art live from chain](/learn-more/collecting-art-on-256art/#how-to-get-the-art-live-from-chain).

### High-res image

Select a piece and choose **High-res image** to view or download its high-resolution static preview.

This preview is a captured image of the generative output. It is useful for saving or displaying the piece where live HTML is not supported, but it does not include animation, interaction, sound, or later changes to a dynamic artwork.

### Rerendering an image

Use **Rerender image** when a piece has no image yet, for example when it keeps showing "Currently rendering…":

1. Select the piece in My collection.
2. Choose **Rerender image**.
3. Allow up to fifteen minutes for the image to be made.
4. Reload My collection and check **High-res image** again.

If the piece already has an image, My collection says so and nothing changes. If an existing image looks wrong, ask in the 256ART Discord.

Rerendering only makes the static image. It does not mint a new token, change the token's seed or traits, or modify the on-chain artwork.

Next, return to [Collecting art on 256ART](/learn-more/collecting-art-on-256art/) or browse [all 256ART artworks](https://256.art/artworks).
