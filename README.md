# EditVala

EditVala is a privacy-first browser image resizer and editor. Images are processed locally in the browser and are never uploaded to a server.

## Features

- Upload, replace, and preview images
- Resize by pixel dimensions
- Maintain or unlock the aspect ratio
- Rotate left and right
- Flip horizontally and vertically
- Adjust brightness, contrast, saturation, and grayscale
- Export PNG, JPEG, and WebP when supported by the browser
- Increase an encoded image's file size using measured KB/MB targets
- Choose between reaching a minimum target or matching a target as closely as possible
- Optional limited upscaling with explicit user consent
- EXIF-aware image normalization for supported browser decoders
- Responsive layout with a developer contact footer

## File-size mode

The **Increase File Size** workflow measures the actual encoded `Blob.size`; it does not rename files or append fake bytes.

- `1 KB = 1,024 bytes`
- `1 MB = 1,048,576 bytes`
- JPEG and WebP use measured quality candidates.
- PNG is encoded losslessly through the browser canvas API; its quality parameter is not controllable.
- Browser encoders cannot guarantee an exact arbitrary file size.
- If a target cannot be reached at the current dimensions and quality, the UI reports the actual result.
- Upscaling is optional, capped, and never performed without consent.

## Running locally

This is a standalone static project with no package manager, build step, backend, or external runtime dependency.

Open `index.html` directly in a browser, or serve the directory with any static web server:

```text
editvala_image_editor/
├── index.html
├── README.md
└── vercel.json
```

## Deployment

The project is ready for static hosting, including Vercel. The minimal `vercel.json` declares the Vercel configuration version; no framework, build command, rewrite, or backend is required.

For a Vercel preview:

1. Import the GitHub repository.
2. Select the `main` branch.
3. Keep the default static project settings.
4. Deploy a preview before promoting to production.

## Verification

The application has been verified in Chromium for:

- Image preview, replacement, resizing, rotation, flipping, filters, and downloads
- JPEG, PNG, WebP, and transparent PNG workflows
- Measured file-size targets and unreachable-target messaging
- Optional upscaling safeguards
- Synthetic EXIF orientations 1–8, including mirrored orientations
- Responsive mobile layout and the clickable email footer link
- Embedded JavaScript syntax and `vercel.json` JSON validity

Firefox, Safari, and real mobile-camera JPEG samples were not available in the verification environment. Exact file-size matching and browser-specific WebP/EXIF behavior therefore remain dependent on the target browser.

## Privacy

Image processing happens locally in the browser. EditVala does not upload images or require a backend, database, account, or API key.

## Developer

**Piyush Mishra**  
Student, Vishwakarma Institute of Technology (VIT), Pune

Contact: [piyushjwalaprasadmishra@gmail.com](mailto:piyushjwalaprasadmishra@gmail.com)
