---
# Documentation: https://sourcethemes.com/academic/docs/managing-content/

title: "How to Make a New Hugo Academic Post"
subtitle: "and other useful hugo notes"
summary: ""
authors: []
tags: []
categories: []
date: 2023-08-17T11:18:29-04:00
lastmod: 2023-08-17T11:18:29-04:00
featured: false
draft: false

# Featured image
# To use, add an image named `featured.jpg/png` to your page's folder.
# Focal points: Smart, Center, TopLeft, Top, TopRight, Left, Right, BottomLeft, Bottom, BottomRight.
image:
  caption: ""
  focal_point: ""
  preview_only: false

# Projects (optional).
#   Associate this post with one or more of your projects.
#   Simply enter your project's folder or file name without extension.
#   E.g. `projects = ["internal-project"]` references `content/project/deep-learning/index.md`.
#   Otherwise, set `projects = []`.
projects: []
---


This post details how to add a post to a hugo-academic website. 
There are also some notes add the end of the post related to updating a hugo-academic website, but unrelated to making a post.

## Make a new post

From root directory run:

```bash
hugo new post/my-post
```

This creates a directory in `content/post/` titled `my-post`. 
Edit the `index.md` markdown file inside this directory. 


## Build Site

To build the website locally, from the root directory run:

```bash
hugo
```

## Preview Site

To preview site, from root directory run 

```bash
hugo server
```

and then navigate to `http://localhost:1313` in your browser


## Push

Push to github (which is then automatically deployed with netflfy)

From root directory, 

```bash
git add -A
# etc...
```






## Other Notes

### Add new section (eg. posters) with links to pdfs

Create directorys and files: 

```bash
mkdir content/posters
touch content/posters/_index.md
mkdir layouts
mkdir layouts/posters
touch layouts/posters/list.html
mkdir data
touch data/posters.yml
mkdir static/files/posters
```
`content/posters/_index.md`:

```markdown
---
title: "Posters"
type: "posters"
---
```
`layouts/posters/list.html`:

```markdown
{{ define "main" }}
  <h1>{{ .Title }}</h1>
  <ul>
    {{ range .Site.Data.posters.posters }}
      <li>
        <a href="{{ .url }}" target="_blank">{{ .title }}</a>
      </li>
    {{ end }}
  </ul>
{{ end }}
```

Update `config/default/menus.toml` to include posters menu item: 

```toml
[[menu.main]]
  name = "Posters"
  url = "posters/"
  weight = 5
```

Finally, put the poster pdfs in `static/files/posters/` and update `data/posters.yml`:

```yaml
posters:
  - title: "Poster 1"
    url: "/static/files/poster1.pdf"
  - title: "Poster 2"
    url: "/static/files/poster2.pdf"
```



### Add new directory to top bar of home page

Uncomment relevent sections of `config/_default/menus.toml`

### Remove sharing buttons at bottom of a post

Set `sharing = false` in `config/_default/params.toml`

### Update CV

Update `static/files/cv/wyatt_madden_cv.tex` and render. 

### Add widget to home page

Add widgets to home page by setting `active = true` in corresponding widget markdown file in  `content/home/`

### Adjust post page settings

Update `content/post/_index.md`. Eg. `view = 1` corresponds with settings listed in `content/home/post.md`


