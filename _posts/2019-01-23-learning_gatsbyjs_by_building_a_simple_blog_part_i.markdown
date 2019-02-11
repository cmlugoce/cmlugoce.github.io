---
layout: post
title:      "Learning Gatsbyjs by Building a Simple Blog: Part I"
date:       2019-01-23 22:35:54 -0500
permalink:  learning_gatsbyjs_by_building_a_simple_blog_part_i
---


Warning: it's gonna be a looooong post!!

Last week I attended a meetup about Gatsbyjs! I found Gatsbyjs very interesting and decided to share a quick tutorial to get started on Gatsby!!

Gatsby.js is a static site generator for the react by using Gatsby we can build any type of modern web apps the sites built with Gatsby are high performant and blazing speed.It follows the "no build configurations" principle, This means that if you are a  developer who wants to learn React.js or GraphQL you can go for it and do it without losing your time and motivation into learning build tools.

Gatsby.js does the code splitting so that user can only download the required number of files which needed to the particular page instead of over fetching the data.


### Let's get started

*Note: Make you sure you have installed Node.js*

Let's start by installing the gatsby-cli:

`npm install --global gatsby-cli` 

Once the installation is done, let's create our project:

`gatsby new 'your-project-name-here'`

![](https://imgur.com/5EQMf5p.jpg)

Awesome!!  Let's `cd` into our project folder and open the code editor to check the structure.

```
├── node_modules
├── src
├── .gitignore
├── .prettierrc
├── gatsby-browser.js
├── gatsby-config.js
├── gatsby-node.js
├── gatsby-ssr.js
├── LICENSE
├── package-lock.json
├── package.json
├── README.md
```

**node_modules**: The packages  installed using npm will live in a node_modules folder.

**src**: The heart of the app lives on this folder!  Inside this folder is where you are going to find the components, images and the pages to be render in the browser.

**gatsby-browser.js**: This file is related to the usage of any browser-related APIs provided by the gatsbyjs.

**gatsby-node.js** This file is related to the usage of any node related APIs provided by the gatsbyjs.

Now is time to open our browser!

`gatsby develop` (similar to npm start in React!) and visit `localhost:8000`

![](https://imgur.com/3wvRTjd.jpg)


As you can see, Gatsbyjs provides you with a starter, so you can get creative pretty fast! To create new pages and components, we need to go back to the editor and open the `src` folder. There are three main folders in it: `components`, `images` and `pages`. 

##### Components

This folder is where we can put other general components we create. Our starter code includes a header, and a layout component.


##### Pages 

This is where your routing takes place!!  Each file becomes one page and the name is based on the file name. So you might have an index page, which you will by convention name `index.js`. 



#### Query the data

Gatsby uses the graphql for querying the data from the different data resources,
> GraphQL is a query language for APIs and a runtime for fulfilling those queries with your existing data. GraphQL provides a complete and understandable description of the data in your API, gives clients the power to ask for exactly what they need and nothing more, makes it easier to evolve APIs over time, and enables powerful developer tools.
> 

We will learn some GraphQL as we go!. Also you can read [this article](https://medium.freecodecamp.org/so-whats-this-graphql-thing-i-keep-hearing-about-baf4d36c20cf)

Now open your `gatsby-config.js` file and just change the title of the blog!

![](https://imgur.com/DgPXFnk.jpg)

![](https://imgur.com/mLLFngd.jpg)

How cool is GraphQL! Gatsby also has included a tool to work test GraphQL queries: graphiQL. We can access this by navigating to `localhost:8000/___graphql`.

![](https://imgur.com/j10luKc.jpg)

With graphiql we can test queries useful to 'extract' data from our site. Let's try some queries:

![](https://imgur.com/3Hj4u5i.jpg)

![](https://imgur.com/4w5n51O.jpg)

We just got the same information from the `gatsby-config.js` file!  

But, how our site is getting this data?🤔

If we go back to the editor and click on the `/components` folder we can see the `layout.js` . You will see that `StaticQuery` is querying for the `site title`  data,  which comes back from the query  stored inside the `data` property.

```
//layout.js

import React from 'react'
import PropTypes from 'prop-types'
import { StaticQuery, graphql } from 'gatsby'

import Header from './header'
import './layout.css'

const Layout = ({ children }) => (
  <StaticQuery
    query={graphql`
      query SiteTitleQuery {
        site {
          siteMetadata {
            title
          }
        }
      }
    `}
    render={data => (
      <>
        <Header siteTitle={data.site.siteMetadata.title} />
        <div
          style={{
            margin: `0 auto`,
            maxWidth: 960,
            padding: `0px 1.0875rem 1.45rem`,
            paddingTop: 0,
          }}
        >
          {children}
          <footer>
            © {new Date().getFullYear()}, Built with
            {` `}
            <a href="https://www.gatsbyjs.org">Gatsby</a>
          </footer>
        </div>
      </>
    )}
  />
)

Layout.propTypes = {
  children: PropTypes.node.isRequired,
}

export default Layout



```


### Create some content: Add some blog posts


We are going to create a few blog post in markdown format. In the `/pages` folder, create a folder for the first post. e.g. `firstpost` Inside it, create an `index.md` and put some content: 

```

---
title: "My first Blog post 🐶"
description: Practicing Gatsbyjs
date: '2019-01-23'
image: ' '
author: The coding dog
---


Awesome Blog!

```

The next step will be to install 2 additional plugins. They will help in transforming the Markdown data into html format.

```
npm install  gatsby-transformer-remark
npm install  gatsby-source-filesystem
```

After installed, we need to add them in `gatsby-config.js`

```

module.exports = {
  siteMetadata: {
    title: 'Code and Dogs',
  },
  plugins: [
    'gatsby-plugin-react-helmet',
    {
      resolve: `gatsby-plugin-manifest`,
      options: {
        name: 'gatsby-starter-default',
        short_name: 'starter',
        start_url: '/',
        background_color: '#663399',
        theme_color: '#663399',
        display: 'minimal-ui',
        icon: 'src/images/gatsby-icon.png', // This path is relative to the root of the site.
      },
    },
    `gatsby-transformer-remark`,
    'gatsby-plugin-offline',
    {
      resolve: `gatsby-source-filesystem`,
      options: {
        path: `${__dirname}/src/pages`,
        name: "pages",
      },
    },
  ],
}

```

Restart the server with `gatsby develop` and let's make some queries on graphiql. You will see the same data from the first post!

```
{
  allMarkdownRemark {
    edges {
      node {
        frontmatter {
          title
          description
          date
        }
        html
      }
    }
  }
}

```

### createPages API

Go back to the editor and open the `gatsby-node.js` file. 

>Gatsby exposes a powerful Node API, which allows for functionality such as creating dynamic pages, extending the babel or webpack configs, modifying the created nodes or pages, etc. This API is exposed in the gatsby-node.js file in the root directory of your project–e.g. at the same level as `gatsby-config.js`. Each export found in this file will be parsed by gatsby, as detailed in its Node API specification. However, we only care about one particular API in this instance, createPages.
>

First, we need to add a new field to our query : `slug` field. `.onCreateNode` API is used to create the new node fields. The `slug` will create a path to the blog post.  

```
const path = require("path")
const { createFilePath, createFileNode } = require(`gatsby-source-filesystem`);
exports.onCreateNode = ({ node, getNode, actions }) => {
    const { createNodeField } = actions
    if (node.internal.type === `MarkdownRemark`) {
        const slug = createFilePath({ node, getNode, basePath: `pages` })
        createNodeField({
            node,
            name: `slug`,
            value: slug,
        })
    }
}
```

The next step is to create pages using the newly created API:

```
gatsby-node.js

const path = require("path")
const { createFilePath, createFileNode } = require(`gatsby-source-filesystem`)
exports.createPages = ({ actions, graphql }) => {
    const { createPage } = actions
    const blogPostTemplate = path.resolve(`src/templates/blog-post.js`)
    return new Promise((resolve, reject) => {
        resolve(graphql(`
    {
      allMarkdownRemark(
        sort: { order: DESC, fields: [frontmatter___date] }
        limit: 1000
      ) {
        edges {
          node {
              fields{
                  slug
              }
            frontmatter {
              title
            }
          }
        }
      }
    }
  `).then(result => {
                if (result.errors) {
                    console.log(result.errors)
                    return reject(result.errors)
                }
                const blogTemplate = path.resolve('./src/templates/blog-post.js');
                result.data.allMarkdownRemark.edges.forEach(({ node }) => {
                    createPage({
                        path: node.fields.slug,
                        component: blogTemplate,
                        context: {
                            slug: node.fields.slug,
                        }, // additional data can be passed via context
                    })
                })
                return
            })
        )
    })
}

exports.onCreateNode = ({ node, getNode, actions }) => {
    const { createNodeField } = actions
    if (node.internal.type === `MarkdownRemark`) {
        const slug = createFilePath({ node, getNode, basePath: `pages` })
        createNodeField({
            node,
            name: `slug`,
            value: slug,
        })
    }
}


```

We’re using GraphQL to get all Markdown nodes and making them available under the allMarkdownRemark GraphQL property. Each exposed property (on node) is made available for querying against. We’re effectively seeding a GraphQL “database” that we can then query against via page-level GraphQL queries. One note here is that the exports.createPages API expects a Promise to be returned, so it works seamlessly with the graphql function, which returns a Promise.

The createPage API accepts an object which requires path and component properties to be defined. Additionally, an optional property context can be used to inject data and make it available to the blog post template component via injected props. Each time we build with Gatsby, createPage will be called, and Gatsby will create a static HTML file of the path we specified in the post’s frontmatter–the result of which will be our stringified and parsed React template injected with the data from our GraphQL query.

### Creating the Blog post template


A blog post template is needed to give shape to the posts. Create a `template` folder in the root of the project, and make a file, `blog-post.js`. 

```
import React from 'react';
import Layout from '../components/layout';

const BlogPost= () => {
    return (
        <Layout>
            <div>
                My first post
        </div>
        </Layout>
    )
}
export default BlogPost
```

Now delete `.cache `folder and run the` gatsby develop`

If you navigate over to the `localhost:8000/firstpost` you will see the template rendered on the screen.

Time to write the blog-post query:

```
import React from 'react';
import Layout from '../components/layout';
import { graphql } from 'gatsby'
const BlogPost=()=> {
    return (
        <Layout>
            <div>
                My first post
        </div>
        </Layout>
    )
}
export default BlogPost
const query = graphql`
 query PostQuery($slug: String!) {
     markdownRemark(fields: { slug: { eq: $slug } }) {
       html
       frontmatter {
        title
        description
       }
   }
`
```

The underlying query name PostQuery (note: these query names need to be unique!) will be injected with the current path, e.g. the specific blog post we are viewing. This path will be available as $slug in our query. For instance, if we were viewing our previously created blog post, the path of the file that data will be pulled from will be /firstpost.

markdownRemark is the main data pull, and each item we pull from the underlying data store will be available to our  component as data.markdownRemark.someValue, e.g. data.markdownRemark.html will be the injected HTML content transformed from the original Markdown source.

frontmatter, is  our data structure we provided at the beginning of our Markdown file. Each key we define there will be available to be injected into the query. We can also access this data via `props.data`

```
import React from 'react';
import Layout from '../components/layout';
import { graphql } from 'gatsby'

const BlogPost=(props)=> {
    const post = props.data.markdownRemark;
    const { title } = post.frontmatter;
    return (
        <Layout>
            <div>
                <h1>{title}</h1>
                <div dangerouslySetInnerHTML={{ __html: post.html }} />
            </div>
        </Layout>
    )
}

export default BlogPost;
export const query = graphql`
 query PostQuery($slug: String!) {
     markdownRemark(fields: { slug: { eq: $slug } }) {
       html
       frontmatter {
        title
        description
       }
   }
}`
```


Restart your server again and navigate to the post!

### Getting the posts list

It's time to render the posts list on the site! 

```
index.js

import React from 'react'
import { Link, graphql } from 'gatsby'
import './post.css';
import Layout from '../components/layout'

const IndexPage = (props) => {
  const postList = props.data.allMarkdownRemark;
  return (
    <Layout>
      {postList.edges.map(({ node }, i) => (
        <Link to={node.fields.slug} className="link" >
          <div className="post-list">
            <h1>{node.frontmatter.title}</h1>
            <span>{node.frontmatter.date}</span>
            <p>{node.excerpt}</p>
          </div>
        </Link>
      ))}
    </Layout>
  )
}
export default IndexPage;
export const listQuery = graphql`
  query ListQuery {
    allMarkdownRemark(sort: { order: DESC, fields: [frontmatter___date] }) {
      edges {
        node {
          fields{
            slug
          }
          excerpt(pruneLength: 250)
          frontmatter {
            date(formatString: "MMMM Do YYYY")
            title
          }
        }
      }
    }
  }
`

```

Create a second post, restart the server and navigate to `localhost:8000`

![](https://imgur.com/oJ1VEAK.jpg)

Yay!! Now we can see our posts!!!


Awesome!! Now you have a simple blog app!! In the next post we will add images, the syntax highlighter, and some basic styling!

