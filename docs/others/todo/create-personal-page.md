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
  - an education account: [How to create an education](./ask-github-edu.md)

## Create a domain name on CloudFlare

- Buy a domain name.

> If you need a `com`, `net`, `org` or `dev` go to [clouflare](https://www.infomaniak.com/en/domains), if you need a `fr` go to [infomaniak](https://www.infomaniak.com/en/domains)

Register your newly created domain to your github account:

- in [GitHub](https://github.com)
  - click on your **profile icon** (top right)
  - click on **settings***
  - go to **pages** in **Code, planning, and automation**
  - enter your domain name
  - copy the **TXT record**
- in [Cloudlfare](https://dash.cloudflare.com)
  - go to your dashboard / Websites
  - select your domain name
  - select DNS / DNS Records (right)
  - in **DNS management** click the blue button **+ Add record**  
  ![cloudlfare](/assets/img/create-personal-page-cloudflare-txt-records.png)
  - enter the name and the content as asked by GitHub
  - click save
  - wait a few hours
- in [GitHub](https://github.com/settings/pages)
  - create a new repository (usually choose your domain name)
  - 

- Go to your dash/interface CloudFlare
- 

## install HUGO

requirements:
  - git [install git](#)
  - go [install go](#)
  - dart SASS
    - homebrew [install Homebrew]()

```sh
  brew install sass/sass/sass
```

### install HUGO

[link](https://gohugo.io/installation/linux/)

search the them you want to use
  - https://themes.gohugo.io/ 

***

### install homebrew

```sh
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

  - add homebrew to your path

```sh
echo 'eval "$(/home/linuxbrew/.linuxbrew/bin/brew shellenv)"' >> $HOME/.bashrc
eval "$(/home/linuxbrew/.linuxbrew/bin/brew shellenv)"
```

## host your page direclty on Github

  - [link](https://pages.github.com/)

<!-- todo create a guide to host a page on GitHub -->
