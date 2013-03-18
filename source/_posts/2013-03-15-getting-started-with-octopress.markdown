---
layout: custom_post
title: Getting Started with Octopress
date: 2013-03-15 08:45
comments: true
categories:

author: Nathan Hopkins
gravatar: 254ec240c9143768df8ec27182764cad
github: hopsoft
twitter: natehop
linkedin: 2951631
---

### The good

[Octopress](http://octopress.org/) is an **out of the box** blogging solution that sits atop [Jekyll](https://github.com/mojombo/jekyll)
*a static site generator*.
It's great for folks who want to quickly get a blog up and running on [Github](https://github.com/).

### The bad

Octopress is ripe with inconsistent and varied ways to customize the CSS, templates, partials, and conditional logic.
This is anathema for anyone who wants a sensible way to truly control things.

Luckily, I've customized this blog till it's "good enough"
so my teammates shouldn't have to experience the pain that I went through.

### The future

I highly recommend considering a vanilla Jekyll solution over Octopress...
even if you are already running Octopress.

Having said all of that, here are some tips to help you get up to speed quickly with Octopress.

## Quick Start

Here's how to get setup as a writer for this blog.
Run the following commands in your shell.

```
git clone git@github.com:one-on-one/one-on-one.github.com.git
cd one-on-one.github.com
bundle
rake -T
```

The last command lists the rake tasks that Octopress makes available to you.

<!-- more -->

## Writing

You can write blog articles using your favorite text editor.
To get started simply run the following command in a shell.

```
rake new_post['The title of the post']
```

**zsh users**: You will want to run `noglob rake new_post['The title of the post']`

The above command produces output like this.

```
Creating new post: source/_posts/2013-03-18-the-title-of-the-post.markdown
```

Now open the newly created file in your favorite editor.

### Front Matter

The first thing you will notice is the [YAML front matter](https://github.com/mojombo/jekyll/wiki/YAML-Front-Matter).
Something that looks like this.

```
---
layout: custom_post
title: Getting Started with Octopress
date: 2013-03-15 08:45
comments: true
categories:

author: Nathan Hopkins
gravatar: 254ec240c9143768df8ec27182764cad
github: hopsoft
twitter: natehop
linkedin: 2951631
---
```

The following entries are included by default.

- **layout** be sure to change this to `custom_post`
- **title** the title of your post
- **date** the date the post was written
- **comments** indicates you allow comments on the post
- **categories** a [YAML list](http://en.wikipedia.org/wiki/YAML#Lists) or space separated string of meta tags for this post

These entries must be manually added.

- **author** the name of the author
- **gravatar** the author's [Gravatar MD5 hash](https://en.gravatar.com/site/implement/hash/)
- **github** the author's Github username
- **twitter** the author's Twitter handle
- **linkedin** the author's Linked In id

After you have taken care of the YAML front matter, simply write your article using [Markdown](http://daringfireball.net/projects/markdown/) syntax.

If you don't want the entire article to show on the index page, simply add a `more` flag to break the content apart.

```
Show on the home page.

<!-- more -->

Only shows on the article page.
```

### Previewing

To preview your post, run the following command from a shell.

```
rake preview
```

Then navigate to [http://localhost:4000](http://localhost:4000) to view your article.
Simply refresh the browser window as you make changes.

### Publishing

Once you have finished writing, commit your article to the git repo. Then publish with rake.

```
git commit -am "Wrote an article."
git push origin source
rake generate
rake deploy
```

That's it! Now get to writing.

## Customizing Octopress

You can ignore this section unless you have a need to customize the markup or CSS.
If you plan to customize things, please read on.

### CSS

There is a `custom` directory under the `sass` directory.

```
|- blog
  |- sass
    |- custom
      |- _colors.scss
      |- _fonts.scss
      |- _layout.scss
      |- _styles.scss
```

This custom directory is the intended home for all of your css customizations.

- `_colors.scss` where color overrides should be defined
- `_fonts.scss` where font overrides should be defined
- `_layout.scss` where layout overrides should be defined
- `_styles.scss` where all other overrides should be defined

You can also add additional stylesheets under the custom directory.
For example, I've added Font Awesome's stylesheet.

### Markup

There is a `custom` directory under the `source/_includes` directory.

```
|- blog
  |- source
    |- _includes
      |- custom
        |- asides
        |- post
        |- after_footer.html
        |- etc...
```

The intent is to isolate markup overrides to things that live in the custom directory.

At first glance it seems possible to override the important files defined in the includes directory.
The problem is that not all files are mirrored in the custom directory.
Also, the naming convention and file intent varies between the two directories.

This leads to confusion. I've found it too restrictive.

In order to get around the limitations, I've started adding new layouts to the `source/_layouts` directory.
I use the convention, `custom_ORIGINAL_NAME.html` for the new layouts.

The custom layout can then be specified in the YAML front matter of individual posts.

```
---
layout: custom_post
---
```

These pain points are why I recommend moving to a vanilla Jekyll solution.

Enjoy!
