# Create a personal website

<!-- for Joplin users -->
<!-- ${toc} -->

<!-- todo
- buy a domain name
 -->

## Requirement

- a [GitHub](https://github.com) account
- an account on [Cloudflare](https://www.cloudflare.com/)
- optional
    * an education account: [How to create an education](./ask-github-edu.md)

## Create a domain name on CloudFlare

- Buy a domain name.

> Note: If you need a `com`, `net`, `org` or `dev` go to [cloudflare](https://developers.cloudflare.com/registrar/get-started/register-domain/), if you need a `fr` go to [infomaniak](https://www.infomaniak.com/en/domains)

### Register your newly created domain to your github account:

- on [GitHub](https://github.com)
    1. click on your **profile icon** (top right)
    ![](/assets/img/create-personal-page-github-menu-top-right.png){ width="500" }  
    2. click on **settings***  
    3. go to **pages** in **Code, planning, and automation**  
    ![](/assets/img/create-personal-page-github-menu-page.png){ width="274" }  
    4. enter your domain name
    5. copy the **TXT record**
    ![github - add a verified domain](/assets/img/create-personal-page-github-add-verified-domain.png)
- on [Cloudlfare](https://dash.cloudflare.com)
    1. go to your dashboard / Websites
    2. select your domain name
    3. select DNS / DNS Records (right)
    4. in **DNS management** click the blue button **+ Add record**  
    ![cloudlfare](/assets/img/create-personal-page-cloudflare-txt-records.png){ width="500" }  
    5. enter the name and the content as asked by GitHub
    6. click save
    7. wait a few hours (it's sometimes shorter)
- go back to [GitHub](https://github.com/settings/pages)
    - create a new repository (usually choose your domain name)

- Go to your dash/interface CloudFlare

## Links

### Find inspiration

- [Dribbble](https://dribbble.com/tags/developer-portfolio)
- [One Page Love](https://onepagelove.com/inspiration/resume)
- [Brutalist Websites](https://brutalistwebsites.com/)
- also
    - [Awwwards](https://www.awwwards.com/websites/?tag=portfolio&category=technology)

### Find some code or components

- [timeline responsive - Codepen](https://codepen.io/search/pens?q=timeline+responsive)

## Use a framework

- [Static Site Generators](https://github.com/collections/static-site-generators)

### Links

- [Jekyll](https://github.com/jekyll/jekyll) 

> Hugo is one of the most popular open-source static site generators. With its amazing speed and flexibility, Hugo makes building websites fun again.

### Install HUGO

requirements:
  - git [install git](https://git-scm.com/download/linux)
  <!-- todo upgrade go (from apt version) -->
  - go [install go](#) 
  - dart SASS
    - homebrew [install Homebrew](https://docs.brew.sh/Homebrew-on-Linux)

```sh
  brew install sass/sass/sass
```

### install HUGO

[link](https://gohugo.io/installation/linux/)

search the them you want to use
  - https://themes.gohugo.io/ 

***

### install Homebrew

```sh
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

  - add homebrew to your path

```sh
echo 'eval "$(/home/linuxbrew/.linuxbrew/bin/brew shellenv)"' >> $HOME/.bashrc
eval "$(/home/linuxbrew/.linuxbrew/bin/brew shellenv)"
```

### host your page direclty on Github

  - [link](https://pages.github.com/)

### Host your page directly on Cloudflare
