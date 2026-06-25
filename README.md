# smv_time

Responsive time + weather banner for Smartvote Limited digital signage.

## Responsive version
- `index.html` — uses viewport scaling for flexible containers (design: 1920×270).
- Good for full-screen or variable-size embeds.

## Fixed version (recommended for client layout software)
- `fixed/index.html` — hardcoded pixel size: **1080×190**.
- All sizes in `px`. No `vw`/`vh` scaling or responsive calculations.
- Compact horizontal layout designed to fit tight banner/widget slots.
- Self-contained logo (CSS blocks), live HKT time, weather + warnings.

### Why use fixed/ ?
Client layout software (the "New program" tool) places HTML components into fixed rectangles (e.g. 0,0 1080,190).
Responsive designs often:
- Assume full viewport or use scale factors that don't match the iframe/WebView size.
- Produce tall content that gets cropped, scaled to 30%, or overflows.
- Pull in full-site navigation or unrelated pages (see broken physical screen result).

Fixed version tells the embed exactly how big it is and renders a clean, predictable result.

### How to use with client's software
1. Host the `fixed/` folder (or the whole repo) so it's publicly reachable, e.g.:
   - https://smartvote-limited.github.io/smv_time/fixed/
   - or your own server / local file path if the software supports it.
2. In the layout program, add an **HTML** (or **Web**) component.
3. Set the URL to the fixed version (include `index.html` if required).
4. Set the component size in the editor to exactly **1080 × 190** (or adjust both the HTML and the slot to match).
5. Prefer "kiosk", "no chrome", "embedded webview", or "fullscreen" mode for the HTML layer if the option exists.
6. Do **not** point it at the repo root or marketing pages — that causes the wrong layout you saw on the physical screen.

### Adjusting the fixed size
If your slot is a different size:
- Edit `fixed/index.html`:
  - Change `width: 1080px; height: 190px;` on `html, body, .banner`.
  - Update the viewport meta: `width=1080, height=190`.
  - Tweak paddings, font sizes, logo size, and gaps to look good.
- Keep the same URL pattern under `fixed/`.

### Tips
- Test the fixed file by opening it directly in a browser and resizing the window to 1080×190, or embed it in an `<iframe width="1080" height="190">`.
- Weather data comes from HKO (may be slow or blocked on some closed signage networks).
- The CSS logo mimics the SMV block style used in your client previews.

## Deployment
Push both `index.html` and `fixed/` to the branch that serves GitHub Pages (or your hosting).
