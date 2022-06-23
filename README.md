# Personal Website for Bahram Salehi

To compile the site, enter
```
hugo -D
```
and the output will be available in the public/ directory.

## How to deploy

If your running this on linux or a mac, then you can run the `deploy.sh` script,
and this will handle compiling your website and pushing it to GitHub. But first,
you'll need to run `chmod +x deploy.sh` which will then allow you to run the
script.

If you're deploying this site on Windows then it's a bit more work. You'll
have to perform the following steps from the bash script:
```sh
cd public
git add .
git commit -m "rebuilding site $(date)"
git push origin master
```
which will prompt you to authenticate.

## How to add a project

In my opinion, you should start by copying an existing file in `content/projects/`.
The files there can be organized however you like.

```md
---
layout: post
title: "project title"
startyear: 2017
endyear: 2019
img: img_file.png
categories: [projects]
draft: false
---

body
```

`title` is the display name of the project, `startyear` and `endyear` are self
explanatory, leave `draft` and `layout` as they are, you can leave `img`
blank or set it to a specific image in the directory `content/images/`. If
you want to reference an image such as `content/images/image1.jpg` then
you can leave out `content/images/` from the path, and so you would set
`img` to `image1.jpg1`.

## How to edit a page

To edit the pages, simply edit the contents of the particular page in
`content/pages/`. Adding a page is a bit more complicated and requires you
to edit the header in `themes/hugo-cards/layouts/partials/header.html`.

Suppose you're creating a page `new_page.md` in `content/pages/`. To
add a link to this new page, go to
`themes/hugo-cards/layouts/partials/header.html`, and look for this element
around line 17:
```html
<div class="collapse navbar-collapse " id="bs-example-navbar-collapse-1">
  <ul class="nav navbar-nav navbar-right">
    <li><a href="{{ .Site.BaseURL }}pages/about/">About</a></li>
```
Add the following code
```
<li><a href="{{ .Site.BaseURL }}pages/new_page/">New Page</a></li>
```
to the unordered list. Then a link to the new page will appear in
the header.
