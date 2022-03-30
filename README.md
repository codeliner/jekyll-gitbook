# Gitbook clone for jekyll

Based on [https://sighingnow.github.io/jekyll-gitbook](https://sighingnow.github.io/jekyll-gitbook)

## Run Locally with docker

`docker run — rm -v $(pwd):/srv/jekyll -p 4000:4000 -it jekyll/jekyll:builder jekyll serve`

## Additions

Compared to org jekyll-gitbook

### Bootstrap alert messages

#### Info

```markdown
Some text with a [link](https://example.com/some/link){: .alert-link} that should be displayed as alert info
{: .alert .alert-info}
```

#### Success

```markdown
Some text with a [link](https://example.com/some/link){: .alert-link} that should be displayed as alert success message
{: .alert .alert-success}
```


#### Warning

```markdown
Some text with a [link](https://example.com/some/link){: .alert-link} that should be displayed as alert warning
{: .alert .alert-warning}
```

#### Danger

```markdown
Some text with a [link](https://example.com/some/link){: .alert-link} that should be displayed as alert danger message
{: .alert .alert-danger}
```
### Copy link to paragraph

The template includes a little JavaScript to add link icons in front of all `h1, h2, h3` **if they have a non empty id attribute**.
The icon becomes visible when hovering over a headline. On click a deep link to the headline is stored in the clipboard for easy linking.

The script is located in `/assets/js/paragraph-link.js`

### Accordion Navigation

`/assets/js/paragraph-link.js` also includes an accordion logic for the sidebar navigation. See `_includes/toc-date.html` for an example
how to create a category (overview of posts in the example) that is collapsed by default and can be shown on click.
The active paragraph is also highlighted in the sidebar while scrolling.

### Lightbox

To enable lightbox include images as HTML like shown in this example:

```html
<a href="{{site.baseurl}}/assets/images/node_cody_tutorial_succeeding_exercise_3.png" data-lightbox="Succeeding-Ex-3" data-title="Succeeding Exercise 3">
    <span class="lightbox-indicator"></span>
    <img src="{{site.baseurl}}/assets/images/node_cody_tutorial_succeeding_exercise_3.png" />
</a>
```

### Youtube Video

Responsive youtube videos can be included as well:

```
<div class="video-container">
    <iframe class="video" src="https://www.youtube-nocookie.com/embed/0FAgsPNqUV4" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
</div>
```

*Note that the video iframe has no width or height defined! It's controlled by the `.video-container` wrapper div.*

## Demo

Live demo on Github Pages: [https://sighingnow.github.io/jekyll-gitbook](https://sighingnow.github.io/jekyll-gitbook)

[![Jekyll Themes](https://img.shields.io/badge/featured%20on-JekyllThemes-red.svg)](https://jekyll-themes.com/jekyll-gitbook/)

## Why Jekyll with GitBook

GitBook is an amazing frontend style to present and organize contents (such as book chapters
and blogs) on Web. The typical to deploy GitBook at [Github Pages][1]
is building HTML files locally and then push to Github repository, usually to the `gh-pages`
branch. It's quite annoying to repeat such workload and make it hard for people do version
control via git for when there are generated HTML files to be staged in and out.

This theme takes style definition out of generated GitBook site and provided the template
for Jekyll to rendering markdown documents to HTML, thus the whole site can be deployed
to [Github Pages][1] without generating and uploading HTML bundle every time when there are
changes to the original repo.

## How to Get Started

This theme can be used just as other [Jekyll themes][1].

[Fork][3] this repository and add your markdown posts to the `_posts` folder.

### Deploy Locally with Jekyll Serve

This theme can be ran locally using Ruby and Gemfiles.

[Testing your GitHub Pages site locally with Jekyll](https://docs.github.com/en/pages/setting-up-a-github-pages-site-with-jekyll/testing-your-github-pages-site-locally-with-jekyll) - GitHub

## Full-text search

The search functionality in jekyll-gitbook theme is powered by the [gitbook-plugin-search-pro][5] plugin and is enabled by default.

[https://sighingnow.github.io/jekyll-gitbook/?q=generated](https://sighingnow.github.io/jekyll-gitbook/?q=generated)

## Code highlight

The code highlight style is configurable the following entry in `_config.yaml`:

```yaml
syntax_highlighter_style: colorful
```

The default code highlight style is `colorful`, the full supported styles can be found from [the rouge repository][6]. Customized
style can be added to [./gitbook/rouge/](./gitbook/rouge/).

## How to generate TOC

The jekyll-gitbook theme leverages [jekyll-toc][4] to generate the *Contents* for the page.
The TOC feature is not enabled by default. To use the TOC feature, modify the TOC
configuration in `_config.yml`:

```yaml
toc:
    enabled: true
    h_min: 1
    h_max: 3
```

## License

This work is open sourced under the Apache License, Version 2.0.

Copyright 2022 Alexander Miertsch

[1]: https://pages.github.com
[2]: https://pages.github.com/themes
[3]: https://github.com/sighingnow/jekyll-gitbook/fork
[4]: https://github.com/allejo/jekyll-toc
[5]: https://github.com/gitbook-plugins/gitbook-plugin-search-pro
[6]: https://github.com/rouge-ruby/rouge/tree/master/lib/rouge/themes
