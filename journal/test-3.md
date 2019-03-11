---
date: 2019-01-03 23:00:00 +0000
title: Gridsome with Forestry CMS and Netlify.
author: Loke Carlsson
excerpt: Gridsome is the Vue.js alternative to Gatsby.

---
#### Why Gridsome?

What Gatsby.js does for React.js is a game changer in how we build websites.  React.js is excellent, but I think Vue.js is more approachable for most web designers and devs getting started with JAMstack. Gridsome is the Vue.js alternative to Gatsby.

With **Gridsome** you get a **universal GraphQL layer** for all your connected data sources. It's like a single source of truth for your website data ready to be used in any page or components. Connect to any CMS or APIs like Google Spreadsheet, Airtable, Instagram Feed, local markdown files, etc.

Here is an example on how to query posts from the GraphQL layer in a page:

```html
<template>
  <Layout>
    <h2>Latest blog posts</h2>
    <ul>
      <li v-for="edge in $page.allWordPressPost.edges" :key="edge.node._id">
        {{ edge.node.title }}
      </li>
    </ul>
  </Layout>
</template>

<page-query>
query Blog {
  allWordPressPost (limit: 5) {
    edges {
      node {
        _id
        title
      }
    }
  }
}
</page-query>
```

The GraphQL layer and all the data can be explored in a local GraphQL playground. The playground is usually located at `https://localhost:8080/___explore` when a Gridsome development project is running.

#### Perfect scores on Google Lighthouse - automagically 💚

One of the main goals of Gridsome is to make a framework that let you build websites that are optimized "out-of-the-box." It follows the [PRPL-pattern by Google.](https://developers.google.com/web/fundamentals/performance/prpl-pattern/) You don't need to be a performance expert to make fast websites with Gridsome. Your site gets almost perfect scores on Google lighthouse out-of-the-box. These are some of the performance steps that Gridsome takes care of:

* Image compressing & lazy-loading ⚡️
* CSS & JS minification ⚡️
* Code-splitting ⚡️
* HTML compressing ⚡️
* Critical CSS (Plugin) ⚡️
* Full PWA & Offline-support (plugin) ⚡️

#### A better way to build websites

Gridsome is built for the JAMstack workflow - a new way to build websites that gives you better performance, higher security, cheaper hosting, and a better developer experience. Generate prerendered (static) pages at build time for SEO-purpose and add powerful dynamic functionality with APIs and Vue.js.

I believe the SSGs / JAMstack trend is just getting started. When you have first started to make websites this way there is no way back. You feel almost "dirty" when going back to a traditional WordPress / CMS setup.

Try running the new Chrome Lighthouse (Audit tab in Developer tools) on a WordPress site - It is impossible to get good scores even with the best caching plugins and hosting. With Gridsome you don't even need caching plugins. Website optimization is taken care of at build time.

It is the **perfect SPA & PWA front-end solution** for any headless CMS or content APIs.

#### Combined with Forestry

What makes Gridsome even more awesome is when combined with a great headless CMS like Forestry.

Forestry enables you to write markdown as your content and host the files on Amazon S3 or even commit to Github as part of the project itself.

![](https://i.imgur.com/9DKBVtH.png)

So, you get the power of a CMS with the performance and simplicity with local files! Awesome, right?

#### Netlify as host

To publish this awesome content power machine, Netlify does a fantastic job of automatically build, optimize and publish the files when a commit on Github is detected.

Everything is handled automatically, no need to worry about setting up a whole CI/CD pipeline, Netlify handles it for you!