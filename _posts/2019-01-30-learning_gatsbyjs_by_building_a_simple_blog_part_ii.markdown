---
layout: post
title:      "Learning Gatsbyjs by Building a Simple Blog: Part II"
date:       2019-01-30 19:45:30 -0500
permalink:  learning_gatsbyjs_by_building_a_simple_blog_part_ii
---


This post is the second part of the tutorial! If you haven't read the first part you can do it [here](http://cmlugoce.com/learning_gatsbyjs_by_building_a_simple_blog_part_i)! 😊 For this part of the tutorial we will add images to the blog post, and the syntax highlighter.

Let's get started!

### Adding an image

Time to start the server by running `gatsby develop` on your terminal, and navigate to ` http://localhost:8000/`

![](https://imgur.com/oJ1VEAK.jpg)

Gatsby offers us a different type of plugins to lazy load the images by adding a blur effect and also crop the images for the different device sizes, which helps to load pages faster!

To add images, we need to install three plugins in your :

```



npm install --save gatsby-transformer-sharp gatsby-plugin-sharp
npm install --save gatsby-image

```

After the installation is done, we need to add them in the `gatsby-config.js` file and restart the server.


Let's add an image in the `firstpost` (add the image first to your folder):

```

---
title: "My first Blog post 🐶"
description: Practicing Gatsbyjs
date: '2019-01-23'
image: doggy.jpg
author: The coding dog
---

```

We need to add a query in `blog.js` to retrieve the image info:

```

import React from 'react';
import Layout from '../components/layout';
import Img from 'gatsby-image';
import Metatags from '../components/Metatags';
import { graphql } from 'gatsby'



const Blog =(props)=> {
    const post = props.data.markdownRemark;
    const { title, author, description } = post.frontmatter;
    
    
  
    
     
    return (
        <Layout>
            
            <div>
                <h1>{title}</h1>
                <p> Posted by: {author}</p>
                <Img fluid={post.frontmatter.image.childImageSharp.fluid} />
                <div dangerouslySetInnerHTML={{ __html: post.html }} />
               
  
            </div>

            
        </Layout>
    )
}
export default Blog
export const query = graphql`

 query PostQuery($slug: String!) {
     markdownRemark(fields: { slug: { eq: $slug } }) {
       html
       id
       frontmatter {
        title
        description
        author
        image {
            childImageSharp {
              resize(width: 1500, height: 1500) {
                src
              }
              fluid(maxWidth: 786) {
                ...GatsbyImageSharpFluid
              }
            }
         }
         }
     }
  }
  `
```
	
	```


Now restart the server and let's check that image!

![](https://imgur.com/XW6Tslm.gif)

Great!! Did you see the blur effect (lazy loading)? So cool!!


### Adding the syntax highlighter

We are done with adding an image, and now it's time to add the syntax highlighter feature!

For this to happen we need to install the `prismjs` plugin:

`npm install --save gatsby-remark-prismjs prismjs`

When the installation is done add the following configuration to the `gatsby-config.js`:

```

plugins: [
  {
    resolve: `gatsby-transformer-remark`,
    options: {
      plugins: [
        `gatsby-remark-prismjs`,
      ]
    }
  }
]

```

Next step would be to select a PrismJS theme and add it in the `gatsby-browser.js`. I chose the *solarized light* theme but you can check out more in [here](https://prismjs.com/) . 


`require("prismjs/themes/prism-solarizedlight.css")`


Let's try it in the `firstpost` file:

![](https://imgur.com/y8TJCsq.jpg)

![](https://imgur.com/j2yyEMq.gif)

Awesome! Now you have functional blog! You can add any styling, and deploy it on the web!! For deployment you can use Netlify!

🎊🎊🎊🎊❤
