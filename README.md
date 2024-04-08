## Astro Multi-Gallery Photography Portfolio

[![Built with Astro](https://astro.badg.es/v2/built-with-astro/tiny.svg)](https://astro.build)

![The best way to show off your pictures](/public/og-image.jpg)

> You can see a live demo at [moeyyad.com/photos](https://moeyyad.com/photos)

## Features 

Expanded the [Astro Multiverse](https://github.com/AREA44/astro-multiverse) theme to:

- Easily organize your photos between multiple galleries
- Straight forward navigation flow between galleries
- Image optimization using Astro's built-in `<Image />` component results in faster loading, better Lighthouse scores, and up to 90% less bandwidth usage
- New `<Layout />` and `<GalleryItem />` Astro components for high-level abstraction

It's very easy to make your own gallery. This is what an entire page looks like: 
```astro
---
import imageA from '@/assets/imageA.jpg';
import imageB from '@/assets/imageB.jpg';
import imageC from '@/assets/imageC.jpg';
import imageD from '@/assets/imageD.jpg';

import Layout from '../layouts/Layout.astro';
import GalleryItem from '../components/GalleryItem.astro';
---

<Layout gallery="My First Gallery">
  <GalleryItem source={imageA} title="A" description="hello world" />
  <GalleryItem source={imageB} title="B" description="howdy world" />
  <GalleryItem source={imageC} title="C" description="hey ya world" />
  <GalleryItem source={imageD} title="D" description="hi there world" />
</Layout>
```

## Getting Started

Just run 4 lines of code in your terminal and you can get it running on `localhost`

###### npm

```bash
git clone https://github.com/moeyyad/photos.git
cd photos
npm install
npm run dev
```

###### pnpm

```bash
git clone https://github.com/moeyyad/photos.git
cd photos
pnpm install
pnpm dev
```


## Personalization
#### Adding Photos
To customize this project you can add your photos to the `/src/assets/` directory. Then import each photo on the page you wish they appear and pass them to the `<GalleryItem />` component.

```astro
---
import example_image from '@/assets/example_image.jpg';
---
<Layout gallery="Example Gallery">
    <GalleryItem source={imageA} title="A" description="hello world" />
</Layout>
```
In the example above, `<GalleryItem />` takes in two *necessary* props, `source`  and `title`, which are needed to display the image. The `description` prop is *optional* to show a caption when the image is clicked.

#### Multiple Galleries
Use Astro's built-in routing system to create multiple galleries. Simply create an `.astro` file with the name of what you want the route to be called, and add it to the `/src/pages` directory. 

Each page uses the `<Layout />` component with a `gallery` prop that lets you name the gallery. While the prop is *technically optional*, it is highly recommended to make navigating between galleries easier for end users.

To add a gallery to the navigation flow, you will have to modify `/src/components/Footer.astro` by adding an `<a>` tag that points to your new gallery as such

```astro
<section>
    <h2>Photo Galleries</h2>
    <a href="/">My First Gallery</a>
    <a href="/new">My New Gallery</a>
</section>
```

#### Personal Links
The `/src/components/Footer.astro` file contains a section that lets you redirect users to other websites such as your Instagram profile or personal website using `FontAwesome` icons that are already provided in this project.

#### Metadata
The `/src/layouts/Layout.astro` file contains the following variables that can be easily changed to personalize the metadata of the project.

```astro
const title = 'Moeyyad Photography'
const description = 'Ultra runner from Ontario, Canada. Sometimes I take pictures'
const author = 'Moeyyad Qureshi'
const ogImage = '/photos/og-image.jpg'
```

The `/public/` directory contains a `favicon.svg` and `og-image.jpg` that can be replaced with your own assets.

## Deployment

Astro has detailed [deployment docs](https://docs.astro.build/en/guides/deploy/) to guide you on how to deploy to the hosting service of your choice.

My personal recommendation is to deploy using [Surge](https://surge.sh) or [GitHub Pages](https://pages.github.com/) as both of these options allow for unlimited bandwidth and usage of a custom domain name **for free**.




