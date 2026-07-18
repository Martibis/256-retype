---
order: 80
---

# The Gallery Page

### Overview of the Gallery Page

The [Gallery Page](https://256.art/gallery) shows the 256ART tokens held by your connected wallet. From the gallery, you can:

- render an artwork live from its contract;
- view or download its high-resolution static preview; and
- request a new static preview if the current one did not render correctly.

The live artwork and static preview serve different purposes. **Live View** runs the artist's on-chain code. The **High Resolution Image** is a captured still image that is more convenient for downloads, thumbnails, and applications that cannot run the live code.

### Accessing Your Gallery Page

1. Go to [256.art/gallery](https://256.art/gallery).
2. Select the option to connect your wallet.
3. Choose the wallet address that holds your 256ART pieces.
4. Approve the connection or sign-in message if your wallet asks.

A sign-in message proves that you control the wallet; it is not a blockchain transaction and should not require gas. Read the message before signing it.

If an expected piece is missing, confirm that the mint transaction succeeded and that you connected the receiving wallet rather than a different account. A newly confirmed mint may also take a short time to appear.

### Live View

Select a piece to open its details, then choose **Live View**. 256ART reads the token's rendering data from its collection contract and runs the artist's code in the browser.

This is the canonical live version of the piece. Animated, interactive, sound, or dynamic features may only be available in this view. Dynamic art can respond to current blockchain data, so its live appearance may change over time.

You can also retrieve the live HTML directly from a block explorer. See [How to Get the Art Live from Chain](/learn-more/collecting-art-on-256art/#how-to-get-the-art-live-from-chain).

### High Resolution Image

Select a piece and choose **High Res Image** to view or download its high-resolution static preview.

This preview is a captured image of the generative output. It is useful for saving or displaying the piece where live HTML is not supported, but it does not include animation, interaction, sound, or later changes to a dynamic artwork.

### Triggering a Re-render of Your Artworks

Use **Rerender** when the high-resolution preview is blank, incomplete, or otherwise does not match a correct live render:

1. Select the affected piece in your gallery.
2. Choose **Rerender**.
3. Allow up to fifteen minutes for the request to be processed.
4. Reload the gallery and check **High Res Image** again.

Rerendering replaces the static preview only. It does not mint a new token, change the token's seed or traits, or modify the on-chain artwork.

Next, return to [Collecting Art on 256ART](/learn-more/collecting-art-on-256art/) or browse [all 256ART artworks](https://256.art/artworks).
