# DFD Hugo metadata image module

A Hugo module for handling metadata images (gathering from or adding to metadata).

## ARCHIVED

This module is no longer maintained (archived for historical purposes), and will not receive updates, even security updates.

## Status

[![build-and-verify](https://github.com/danielfdickinson/metadata-image-mod-hugo-dfd/actions/workflows/build-and-verify.yml/badge.svg)](https://github.com/danielfdickinson/metadata-image-mod-hugo-dfd/actions/workflows/build-and-verify.yml)

## GitHub repository

<https://github.com/danielfdickinson/metadata-image-mod-hugo-dfd>

## Site with examples

<https://metadata-image-mod.wildtechgarden.ca>

## Features

* Page-level microformats (e.g. Open Graph/Twitter) support (not to be confused with
  mf2 / microformats.org in-body microformats)

## Basic usage of the module

### Prerequisites

1. You must have in directory containing a hugo site (e.g. such as created by `hugo new site <directory>`).
2. You must have a recent version of Go installed (see section [Prerequisite in 'Use Hugo Modules' in the Hugo documentation](https://gohugo.io/hugo-modules/use-modules/#prerequisite)).
3. The site must be initialized as a Hugo module (see ['Initialize a New Module' in the Hugo documentation](https://gohugo.io/hugo-modules/use-modules/#initialize-a-new-module), or the output of `hugo mod init`).
4. Before the site will build correctly, [you will also need a theme installed](https://gohugo.io/getting-started/quick-start/#step-3-add-a-theme).

### Importing the module

1. The first step to making use of this module is to add it to your site or theme. In your configuration file:

   ``config.toml``

   ```toml
   [module]
   [[module.imports]]
   path = "github.com/danielfdickinson/metadata-image-mod-hugo-dfd"
   ```

   OR

   ``config.yaml``

   ```yaml
   module:
       imports:
         - path: github.com/danielfdickinson/metadata-image-mod-hugo-dfd
   ```

2. Execute

   ```bash
   hugo mod get github.com/danielfdickinson/metadata-image-mod-hugo-dfd
   hugo mod tidy
   ```

### Add the image

1. Place your image in a [page bundle](https://gohugo.io/content-management/page-bundles/) (e.g. `cover-screenshot.png`)
2. OR under `assets` in your project root

If you don't use a page bundle or ``assets``, the image can still be used, but cannot be made responsive

### Image handling partials

See [DFD Hugo image handling module](https://github.com/danielfdickinson/image-handling-mod-hugo-dfd) for more information.

### Metadata gathering

See [DFD Hugo metadata module](https://github.com/danielfdickinson/metadata-mod-hugo-dfd) for more information.

Metadata types that can be gathered are:

* ``media-images`` A slice of maps (dictionaries) with image information for use in microformats and other metadata; images matched are the same as [featured images in the image handling module, above](#image-handling-partials) above.
* ``media-image`` A map (dictionary) with image information for the first image from ``media-images`` which corresponds to [featured images in the image handling module, above](#image-handling-partials) above.

Gathering image metadata may also create an image for specifically for use with microformats (see [for microformats](#for-microformats) , below).

### `.Site` or `.Page` params

#### For featured images used by the microformats

'alt' text from one of:

* imageFeaturedAlt
* imageCoverAlt
* imageThumbnailAlt
* featuredImageAlt
* featuredAlt

'title' from one of:

* imageFeaturedTitle
* imageCoverTitle
* imageThumbnailTitle
* featuredImageTitle
* featuredTitle

#### For microformats

| Param | Default | Description |
|-------|---------|-------------|
| microformatWidth | 1200 | Default width for microformat image (e.g. Open Graph) |
| microformatHeight | 630 | Default height for microformat image (.e.g Open Graph) |
| microformatSizingMethod | Fill | Default method for resize/crop of microformat image [ Fit \| GrowFit \| Fill \| Resize ] |
| microformatImageOverlay | _(none)_ | Dict with src, x, and y for image, and x, y position to overlay 'src' on the main image |
| microformatTextOverlay | _(none)_ | Slice of dicts with text, opts (which is a dict, see [Hugo docs](https://gohugo.io/functions/images/#text)) which specifies text to overlay over an image and the options (color, size, etc). Overrides use of title and/or description as overlay text (below). |
| microformatTitleAsOverlayText | _false_ | Use page .Title as overlay text |
| microformatDescriptionAsOverlayText | _false_ | Use page .Description as overlay text |
| microformatOverlayTitleColor | _#fff_ | Colour for title as overlay text |
| microformatOverlayTitleSize | _96_ | Size in pixels for title as overlay text |
| microformatOverlayTitleSpacing | _2_ | Line spacing for title as overlay text |
| microformatOverlayTitleStartX | _0_ | Start X position for title as overlay text |
| microformatOverlayTitleStartY | _0_ | StartY position for title as overlay text |
| microformatOverlayTextColor | _#fff_ | Colour for description as overlay text |
| microformatOverlayTextSize | _96_ | Size in pixels for description as overlay text |
| microformatOverlayTextSpacing | _2_ | Line spacing for description as overlay text |
| microformatOverlayTextStartX | _0_ | Start X position for description as overlay text |
| microformatOverlayTextStartY | _0_ | Start Y position for description as overlay text |

## Auto-generating 'social cards'

``` yaml
description: "Example of an auto-generated social card. Obviously can be much prettier."
imageFeatured: "/light-blue-gradient-social-card.png"
microformatTitleAsOverlayText: true
microformatOverlayTitleStartX: 64
microformatOverlayTitleStartY: 64
microformatOverlayTitleColor: "#111"
microformatDescriptionAsOverlayText: true
microformatOverlayTextStartX: 24
microformatOverlayTextStartY: 290
microformatOverlayTextColor: "#222"
imageFeaturedCardOnly: true
headerTextOmit: false
summaryTextOnly: true
imageFeaturedGenAltPrefix: "Metadata image module"
```

![Light blue gradient with the title 'Social Card' and the text 'Example of an auto-generated social card. Obviously can be much prettier'](README-assets/light-blue-gradient-social-card_with_text.png)

## Contributions welcome

If [your issue can't be found when searching both open and closed issues](https://github.com/danielfdickinson/metadata-image-mod-hugo-dfd/issues?q=is%3Aissue), please add it!

Please [check open issues on danielfdickinson/metadata-image-mod-hugo-dfd](https://github.com/danielfdickinson/metadata-image-mod-hugo-dfd/issues)
for enhancements and bugs that you would like resolved, write the fix, and submit a pull request!

As well, documentation improvements are always handy.

Thank you, and I hope you find this repository useful.

## Support and general questions

Please use [GitHub Discussions](https://github.com/danielfdickinson/metadata-image-mod-hugo-dfd/discussions) for support and general questions.
