# DLME Stories

## Image sizes:

- **Cover**: 1200x800
- **Landing Thumb**: 480x360
- **Exhibit Large Square**: 480x480
- **Exhibit Long**: 965x350
- **Exhibit Images**: 845x

For more on sizes, `_component.scss` in the `// Background image` section.  


## Processing Images

Place images in the `originals` directory and run `rake`. This will generate derivative images for each image in the above size and copy them in to the `images` directory.


## Image Placement

- In the exhibit file (e.g. `waraksa.md`), set the `background_url:` key to the `cover-1200x800` image (e.g. `/images/katherine-hanlon-24210-cover-1200x800.jpg`)
- On `index.md`, set the link to the exhibit the `landing-480x360` image (e.g. `katherine-hanlon-24210-landing-480x360.jpg`)
- In `_sass/_component.scss`, set the `background-image` for the appropriate child to the `large_square-480x480`, or the `landing-480x360` image for long items.
