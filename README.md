# gasby-starter-netify-cms
Note: This starter uses Gatsby v4.  This repo contains an example business website that is built with Gatsby, and Netlify CMS: Demo Link.  It follows the JAMstack architecture by using Git as a single source of truth, and Netlify for continuous deployment, and CDN distribution.
Features
A simple landing page with blog functionality built with Netlify CMS
Editable Pages: Landing, About, Product, Blog-Collection and Contact page with Netlify Form support
Create Blog posts from Netlify CMS
Tags: Separate page for posts under each tag
Basic directory organization
Uses Bulma for styling, but size is reduced by gatsy-plugin-purgecss
Blazing fast loading times thanks to pre-rendered HTML and automatic chunk loading of JS files
Uses gatsby-plugin-image with Netlify-CMS preview support
Separate components for everything
Netlify deploy configuration
Netlify function support, see netlify/functions folder
Perfect score on Lighthouse for SEO, Accessibility and Performance (wip:PWA)
..and more
Prerequisites
Minimal Node.js version 14.15.0
Gatsby CLI
Netlify CLI
Getting Started (Recommended)
Netlify CMS can run in any frontend web environment, but the quickest way to try it out is by running it on a pre-configured starter site with Netlify. The example here is the Kaldi coffee company template (adapted from One Click Hugo CMS). Use the button below to build and deploy your own copy of the repository:

Deploy to Netlify

After clicking that button, you’ll authenticate with GitHub and choose a repository name. Netlify will then automatically create a repository in your GitHub account with a copy of the files from the template. Next, it will build and deploy the new site on Netlify, bringing you to the site dashboard when the build is complete. Next, you’ll need to set up Netlify’s Identity service to authorize users to log in to the CMS.

Access Locally
Pulldown a local copy of the Github repository Netlify created for you, with the name you specified in the previous step

$ git clone https://github.com/[GITHUB_USERNAME]/[REPO_NAME].git
$ cd [REPO_NAME]
$ yarn
$ netlify dev # or ntl dev
This uses Netlify Dev CLI feature to serve any functions you have in the netlify/functions folder.

To test the CMS locally, you'll need to run a production build of the site:

$ npm run build
$ netlify dev # or ntl dev
Media Libraries (installed, but optional)
Media Libraries have been included in this starter as a default. If you are not planning to use Uploadcare or Cloudinary in your project, you can remove them from module import and registration in src/cms/cms.js. Here is an example of the lines to comment or remove them your project.

import CMS from "netlify-cms-app";
// import uploadcare from 'netlify-cms-media-library-uploadcare'
// import cloudinary from 'netlify-cms-media-library-cloudinary'

import AboutPagePreview from "./preview-templates/AboutPagePreview";
import BlogPostPreview from "./preview-templates/BlogPostPreview";
import ProductPagePreview from "./preview-templates/ProductPagePreview";
import IndexPagePreview from "./preview-templates/IndexPagePreview";

// CMS.registerMediaLibrary(uploadcare);
// CMS.registerMediaLibrary(cloudinary);

CMS.registerPreviewTemplate("index", IndexPagePreview);
CMS.registerPreviewTemplate("about", AboutPagePreview);
CMS.registerPreviewTemplate("products", ProductPagePreview);
CMS.registerPreviewTemplate("blog", BlogPostPreview);
Note: Don't forget to also remove them from package.json and yarn.lock / package-lock.json using yarn or npm. During the build netlify-cms-app will bundle the media libraries as well, having them removed will save you build time. Example:

yarn remove netlify-cms-media-library-uploadcare
OR

yarn remove netlify-cms-media-library-cloudinary
Getting Started (Without Netlify)
$ gatsby new [SITE_DIRECTORY_NAME] https://github.com/netlify-templates/gatsby-starter-netlify-cms/
$ cd [SITE_DIRECTORY_NAME]
$ npm run build
$ npm run start
Setting up the CMS
Follow the Netlify CMS Quick Start Guide to set up authentication, and hosting for production.

If you want use Netlify CMS locally, run the site in one terminal with npm run start and in another Terminal you can use npx netlify-cms-proxy-server which proxy requests so you'll be automatically logged in as a user on http:localhost:3000/admin.

Debugging
Windows users, who aren't using WSL, might encounter node-gyp errors when trying to npm install. To resolve, make sure that you have both Python 2.7 and the Visual C++ build environment installed.

npm config set python python2.7
npm install --global --production windows-build-tools
Full details here.

MacOS and WSL users who might also encounter some errors, check node-gyp for more info. We recommend using the latest stable node version.

Purgecss
This plugin uses gatsby-plugin-purgecss and bulma. The bulma builds are usually ~170K but reduced 90% by purgecss.

CONTRIBUTING
Contributions are always welcome, no matter how large or small. Before contributing, please read the code of conduct.
