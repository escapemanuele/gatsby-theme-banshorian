# gatsby-theme-byfolio

[![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)](https://github.com/christiandavid/gatsby-theme-byfolio/@christiandavid/gatsby-theme-byfolio/LICENSE)
[![CircleCI](https://circleci.com/gh/christiandavid/gatsby-theme-byfolio.svg?style=svg)](https://circleci.com/gh/christiandavid/gatsby-theme-byfolio)
![Twitter Follow](https://img.shields.io/twitter/follow/iChristianDavid?style=social)

Initially this was a personal portfolio made in GatsbyJs, now it's a Gatsby theme available to anyone who wants to tell their work history focusing only on the content.

![Gatsby Portfolio](https://raw.githubusercontent.com/christiandavid/gatsby-theme-byfolio/dev/%40christiandavid/gatsby-theme-byfolio/readme-files/Byfolio.jpg)

- [Installation](#installation)
- [Configuration](#configuration)
- [Adding experience and skills](#adding-experience-and-skills)
- [Skills](#skills)
- [Component shadowing](#component-shadowing)
- [Examples](#examples)
- [Deploy](#deploy)
- [Authors](#authors)
- [Credits](#credits)

## Installation

```sh
npm install --save @christiandavid/gatsby-theme-byfolio
```

### With `git clone`

You can also clone this repository which contains the information of my portfolio

```sh
git clone git@github.com:christiandavid/gatsby-theme-byfolio.git my-best-portfolio

cd my-best-portfolio

yarn workspaces run

# Run localhost
yarn workspace www develop

# Build your Gatsby site
yarn workspace www build
```

## Configuration

After each modification in gatsby-config.js it is necessary to restart the site from the terminal.

```js
// gatsby-config.js
module.exports = {
  plugins: [
    {
      resolve: `@christiandavid/gatsby-theme-byfolio`,
      options: {
        basePath: ``,
        path: `src/`,
        imagesPath: `src/images/`,
        siteTitle: `Portfolio`,
        siteUrl: `https://www.christianibarguen.com`,
        siteName: `Christian David Ibarguen`,
        siteShortName: `CD`,
        siteDescription: `This cool App contains information about my work experience as a software developer.`,
        siteKeywords: `Software developer, Full Stack Developer`,
        useMozJpeg: true,
        menuLinks: [
          // title = Link text
          // color = Animation background color on click
          { name: `home`, title: `Home`, color: `#000`, link: `` },
          {
            name: `experience`,
            title: `Experience`,
            color: `#3a3d98`,
            link: ``
          },
          { name: `skills`, title: `Skills`, color: `#d52d43`, link: `` },
          { name: `aboutMe`, title: `About Me`, color: `#fff`, link: `` }
        ],
        email: `christian@davidibarguen.com`,
        social: {
          // Usernames
          twitter: `ichristiandavid`,
          gitHub: `christiandavid`,
          stackOverflow: `967956/christian-david`,
          linkedIn: `in/christianibarguen/`,
          resumeInPdf: `/CV-19.pdf` // url or local link
        },
        homePage: {
          availableToHire: true,
          dotColors: ["#0e3e1e", "#6CC551"],
          h1Text: `Hi!, I'm Christian David Ibarguen`,
          h2Text: `I'm a Full Stack Developer who loves working in Backend, I have
              worked as a software developer since 2006.`,
          typewriter: [
            `Coding is my passion 😎`,
            `I'm a 🍕 lover`,
            `I'm a pretty fast learner and always interested in learning new technologies 🤓`,
            `I think one of my values is the <strong>ability to resolve problems<strong>`,
            `I like to share what I know 👨‍🏫`,
            `In my non-coding hours, I'm at the 🏋‍`,
            `I also do design and UX work <span style='color: #27ae60;'>occasionally</span>`
          ]
        },
        // Color for menu background
        shapeColor: {
          link: { color: "#171616", hover: "#fff" },
          shape1: {
            color: `#413f46`,
            opacity: `0.7`
          },
          shape2: {
            color: `#e6e5ea`,
            opacity: `0.7`
          },
          shape3: {
            color: `#fff`,
            opacity: `0.7`
          }
        },
        footer: `heart`
      }
    },
    {
      resolve: `gatsby-plugin-google-gtag`,
      options: {
        trackingIds: [
          `UA-151335375-1` // Google Analytics / GA
        ],
        // This object gets passed directly to the gtag config command
        // This config will be shared across all trackingIds
        gtagConfig: {
          anonymize_ip: true,
          cookie_expires: 0,
          send_page_view: true,
          cookie_name: `christianibarguen.com`
        },
        // This object is used for configuration specific to this plugin
        pluginConfig: {
          // Puts tracking script in the head instead of the body
          head: false,
          // Setting this parameter is also optional
          respectDNT: false
        }
      }
    }
  ]
};
```

| Option name     | Type    | Description                                                                                                                           |
| --------------- | ------- | ------------------------------------------------------------------------------------------------------------------------------------- |
| basePath        | string  | Where should the site be served from? /porfolio will change all paths to start with /porfolio                                         |
| path            | string  | Place where the files are stored, for example: `src/`                                                                                 |
| imagesPath      | string  | Place where the images files are stored, for example: `src/images/`                                                                   |
| typographyPath  | string  | Place where the file that defines your website’s typography configuration is located                                                  |
| siteTitle       | string  | The main title for the website, used in the `<title>` element                                                                         |
| siteUrl         | string  | The portfolio url, example: `https://christianibarguen.com`                                                                           |
| siteName        | string  | Represents the name of the web application as it is usually displayed to the user                                                     |
| siteShortName   | string  | Represents a short version of the name of the web application                                                                         |
| siteDescription | string  | Allows you to describe the purpose of the web application                                                                             |
| siteKeywords    | string  | Keywords for the page                                                                                                                 |
| useMozJpeg      | boolean | MozJPEG provides better image compression than the default encoder used in gatsby-plugin-sharp.                                       |
| menuLinks       | array   | An array of objects for the menu, each item represents a link, color represents the color that the animation shows when it is pressed |
| email           | string  | Email for contact, this is displayed when the Contact Me button is pressed                                                            |
| social          | object  | An Object with the user accounts of: twitter, gitHub, stackOverflow, linkedIn and `resumeInPdf` resume link                           |
| homePage        | object  | An object with information of titles, texts with animated description, and animation to show if you are available to be hired         |
| shapeColor      | object  | Represents the colors used in the menu animation, in total there are 3 in which you can specify the color and the opacity             |
| footer          | string  | Text to show in the footer only has 2 options: `heart`or `hand`                                                                       |

## Adding experience and skills

This theme generates pages based on Markdown files in the `path`/experience directory. Your Markdown files should contain some frontmatter defining their company, logo, etc.
All company logos must be relative to `imagesPath`/companies directory.
All Skills logos must be relative to `imagesPath`/skills directory.
All layout images must be relative to company directory, for example: `imagesPath`/companies/acef

### Important

For each Skill you must add the logo of the Framework, library or program, with a resolution of **width: 500px, height: 500px**, in the src/images/skills/ directory I leave several logos, **only Skills logos that I own are present, if the logo you need does not appear you must create it**.

Layout number is for image animation you can select from 1 to 5

```yaml
---
title: ""
company: "ACEF (Colombian Association of Finance Executives)"
logo: ../images/companies/acef.png
jobTitle: "Frontend - Backend Developer"
skills:
  [
    { title: "HTML 4", image: ../images/skills/html4.png },
    { title: "CSS 2", image: ../images/skills/css2.png },
    { title: "Apache", image: ../images/skills/apache.png },
  ]
images:
  [
    {
      title: "Achievements",
      description: "In Acef I had some interesting challenges, one of them was to get the emails with event information reached the inbox and not the SPAM folder.",
      layout: "4",
      files:
        [
          { image: ../images/companies/common/codescreen2.jpg },
          { image: ../images/companies/common/codescreen1.jpg },
          { image: ../images/companies/acef.png },
        ],
    },
    {
      title: "Emails and CMS",
      description: "I got the messages to have a good reputation in SPAM filters by following the standards and rules allowing the messages to reach the inbox, I also developed a CMS.",
      layout: "1",
      files:
        [
          { image: ../images/companies/acef/evaluacion.jpg },
          { image: ../images/companies/acef/database.jpg },
          { image: ../images/companies/acef/outlook.png },
        ],
    },
  ]
dateFrom: "2006-03-01"
dateTo: "2007-06-01"
---
- Direction of the marketing and communications area oriented to the promotion of events and training through mass emails
- Design of the graphic interface and creation of CMS for the corporate website
- Implementation of email receptions in more than 100,000 emails per day
- DBA role and in charge of the administration of the servers
- Preparation of user manuals for the system
```

### Skills

The Skills are automatically selected from experience, in case some skill you acquired does not correspond to a company you can add it in `path`/experience/\_additionalSkills.md

```yaml
---
title: ""
company: ""
jobTitle: ""
logo:
skills:
  [
    { title: "React", image: ../images/skills/react.png },
    { title: "React Native", image: ../images/skills/react-native.png },
    { title: "Gatsby", image: ../images/skills/gatsby.png },
    { title: "GraphQL", image: ../images/skills/graphql.png },
    { title: "Redux", image: ../images/skills/redux.png },
    { title: "Apollo GraphQL", image: ../images/skills/apollo.png },
    { title: "Socket.io", image: ../images/skills/socket-io.png },
  ]
images: []
dateFrom: "2019-09-01"
dateTo: "2019-09-01"
---

```

## Component shadowing

You can customize elements like the css style or about-me content by taking advantage of [component shadowing](https://www.gatsbyjs.org/blog/2019-04-29-component-shadowing/).

I recommend using [Coolors.co](https://coolors.co/) to select a color palette and adapt it to your new portfolio.

You can change the color of the text and the background of each page, for example:

```js
// src/gatsby-theme-byfolio/layout/layoutColors.css.js
import { css } from "@emotion/core";
import lineSvg from "../../../static/assets/line.svg";

const styles = css`
  .e404.layout-wrapper .layout-inner {
    background: #fff;
  }
  .e404 .data-section {
    color: #000;
  }
  .aboutme.layout-wrapper .layout-inner {
    background: #fff;
  }
  .aboutme .data-section {
    color: #000;
  }
  .aboutme .hamburgercolr::before,
  .aboutme .hamburgercolr::after,
  .e404 .hamburgercolr::before,
  .e404 .hamburgercolr::after {
    background-color: #000;
  }
  .home.layout-wrapper .layout-inner {
    background: #0e0f11;
    background: #0e0f11 url(${lineSvg}) center center fixed;
    background-size: contain;
  }
  .home.layout-wrapper h1,
  .home.layout-wrapper h2 {
    color: #fff;
  }
  .skill.layout-wrapper .layout-inner {
    color: #fff;
    background: #9d316e;
    background: url(${lineSvg}) center center fixed, linear-gradient(
        45deg,
        #9d316e,
        #de2d3e
      );
    background-size: cover;
  }
  .experience.layout-wrapper .layout-inner {
    background: #3a3d98;
    background: url(${lineSvg}) center center fixed, linear-gradient(
        45deg,
        #6f22b9,
        #3a3d98
      );
    background-size: cover;
  }
  .home .hamburgercolr::before,
  .home .hamburgercolr::after,
  .skill .hamburgercolr::before,
  .skill .hamburgercolr::after,
  .experience .hamburgercolr::before,
  .experience .hamburgercolr::after {
    background-color: #fff;
  }
  .home .btn-contact-color,
  .experience .btn-contact-color {
    color: #fff;
  }
  .aboutme .btn-contact-color,
  .e404 .btn-contact-color {
    color: #000;
  }
`;

export default styles;
```

You can change the about-me text in the "src/gatsby-theme-byfolio/contentJSON/about-me.json" file, for example:

```json
[
  {
    "subtitle": "About Me!",
    "content": "I'm a <strong>Software Developer</strong>"
  },
  {
    "subtitle": "Experience!",
    "content": "I started developing software from <strong>2004</strong> working in several companies"
  }
]
```

## Examples

- [My Portfolio](https://christianibarguen.com)

Are you using this theme in your own project? Submit a PR with your website added to this list!

## Deploy

[![Deploy to Netlify](https://www.netlify.com/img/deploy/button.svg)](https://app.netlify.com/start/deploy?repository=https://github.com/christiandavid/gatsby-theme-byfolio)

## Authors

- **Christian David Ibarguen R**

## Credits

Special thanks to:

[GatsbyJs](https://www.gatsbyjs.org/)

[Codrops](https://tympanus.net/codrops/)

[Fontawesome](https://fontawesome.com/license)
