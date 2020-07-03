[![Greenkeeper badge](https://badges.greenkeeper.io/marianzburlea/pug-starter.svg)](https://greenkeeper.io/)

# Pug starter

## **baseUrl**

Note: `inline` attribute has been updated to `embed`

Old way:

```
if config.entry.css.embed
  link(rel="stylesheet" href=`${embedPath}` inline)
```

New way:

```
if config.entry.css.embed
  link(rel="stylesheet" href=`${embedPath}` embed)
```

add **_modularCss_** support. When enabled in the config of `package.json` it will convert all SCSS/SASS files to its correspondent CSS path.

add **_baseurl_** support which can be configured for GitHub.io and custom domain. Check _package.json_ config section for

- _deployToGithubIo_ - (true|false) by default it is set to _true_ and will affect the value of _baseUrl_ when you want to deploy to GitHub.io; You want to set it to _false_ if you want to use _customUrl_ as the value of _baseUrl_
- _customUrl_ - if you want baseUrl to have a value like http://my-project.codetap.io or any other one;
- _githubUrl_ - if you want baseUrl to have a value like http://github.com/marianzburlea/pug-starter.git or any other one;

In the end you can use _baseUrl_ to prefix your paths like:

```
link(rel="stylesheet", href=`${baseUrl}/style.css`)
```

or

```
a(
  title="Is it possible?"
  target="_blank"
  href=`${baseUrl}/article/nice-weather`
)
```

or

```
img(alt="Awesome dog" width="100" href=`${baseUrl}/image/cool-dog.jpg`)
```

## Prerequisites

The project requires NodeJS v.4+

To install NodeJS visit [nodejs download page](https://nodejs.org/en/download/) download the appropiate package for your operatin system, click on the downloaded file, open it and follow the installation procees. If you don't know much about it, just click ALL the NEXT and or INSTALL buttons and choose "I agree" when prompted and you should be fine.

## Installation

**BEFORE YOU INSTALL:** please read the [prerequisites](#prerequisites)

```bash
$ npm i
```

or

```bash
$ npm install
```

Note: if you run into an pngquant-bin error on Windows try running:

```
npm install imagemin-pngquant@5.0.1 -D
npm install pngquant-bin@3.1.1 -D
```

before you run `npm start`

## Usage

To run the project in development mode and open a local server that synchronizes across multiple devices use:

```bash
npm start
```

or

```bash
npm run dev
```

To build the project for production use:

```bash
npm run prod
```

To automatically deploy your project to GitHub pages and make it available at https://[your-username].github.io/[your-project-name] use:

```bash
npm run deploy
```

## Style

The project supports both **_embed_** and **_external_** style sheets. You can have none, one or the other, or both of them.

### Single page application style

When you're building a single page app or website, there is no point in having the style sheets loaded from an external file and I'll explain why: the point of loading external style sheets is to allow the browser to cache those files and once you visit another web page of the same website, instead of making another request(s) for the style sheet file(s) to the server and having to download them, if there is no change, the browser will load them from the local drive. In a single page, there is no other page to go to therefore the external file technique doesn't apply.

### Multi page application style

In this scenario you can have either both **_embed_** and external or just external. The most common scenario is to have only one external style sheet file to be loaded and most of the time that's just fine.

If you want to improve your SEO and user experience even further, I strongly recommend to use a combination of both **_embed_** and external. The **_embed_** style sheet should only contain the minimum amount of styles for the initial visible part of the page to render. The rest of the styles can be put in the external CSS file.

## Auto reset git

If you run `npm i`, the git history will get reset.

To avoid resetting the git history run `npm i --ignore-scripts`
