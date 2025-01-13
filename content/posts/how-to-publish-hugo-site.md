+++
date = '2025-01-12T18:38:00+01:00'
draft = false
title = 'How to Build and Publish a Personal Website'
description = "Step by step introduction to establish a personal website with low/no cost."
tags = ["website","blog","cv","github","hugo"]
categories = ["blog"]
image = "/images/how-to-publish-personal-site.jpg" 
+++

![How to Build and Publish a Personal Website](/images/how-to-publish-personal-site.jpg)

## Introduction

In today’s digital world, having a personal professional website is a valuable asset for showcasing your expertise, experiences, and achievements. A personal website not only provides a centralized platform to highlight your skills but also helps you build a strong online presence. For professionals, it serves as a modern-day business card—an easily accessible portfolio that reflects your personality and expertise.

I decided to create my own website, **Masood's Digital Space**, to:
- Showcase my blog and share insights about cloud architecture, DevOps, and technology.
- Host an online CV that’s always up-to-date and easy to scan.
- Establish professional credibility by integrating a custom domain and a branded email address.

In this blog post, I’ll guide you through how I built and deployed my site using **Hugo**, customized it with the **Paper theme**, and published it via **GitHub Pages**. I also incorporated useful features like a contact page, a custom domain, and a Markdown-based CV.

---

## 1. The Tools I Used

### Hugo: The Framework
Hugo is a static site generator that simplifies website creation by focusing on content management. It’s fast, flexible, and ideal for creating professional, lightweight websites. Using Hugo allowed me to quickly build my site without dealing with complex server setups.

#### The Paper Theme
I chose the minimalist **Paper theme** for its clean design and responsive layout. It’s well-suited for personal blogs and professional sites, making my content visually appealing and accessible on all devices.

### GitHub

#### GitHub Repository

I hosted my website’s source code on GitHub in a public repository, which allowed me to manage version control efficiently. This repository not only acts as the source for my GitHub Pages site but also enables others to explore, clone, or adapt my website’s structure. You can view the source code [here](https://github.com/masoodazizi/my-hugo-site/).

#### GitHub Actions

GitHub Actions provided an automated workflow to build and deploy my website. By setting up a simple workflow file, I ensured that every change pushed to my repository triggers Hugo to build the site and publish it to GitHub Pages. This automation saves time and eliminates manual steps in the deployment process.

#### GitHub Pages

GitHub Pages is a free and reliable platform for hosting static websites. It integrates seamlessly with GitHub repositories, making deployment straightforward. With features like custom domains and HTTPS, it provides a professional-grade hosting solution for personal and project websites.

### Custom Domain and Email
To make my website more professional, I registered a custom domain and configured a branded email address:
- **[Namecheap](https://www.namecheap.com/):** Offers affordable domain registrations.
- **[IONOS](https://www.ionos.de/):** Provides domain + email packages, allowing me to set up a professional email address like `contact@mydomain.com`.

#### Configuring the Custom Domain
I configured the DNS settings for my custom domain by adding the **[GitHub Pages IP addresses](https://docs.github.com/en/pages/configuring-a-custom-domain-for-your-github-pages-site/managing-a-custom-domain-for-your-github-pages-site)** as `A` records to ensure the domain points correctly to my site.

---

## 2. Setting Up Hugo

### Installation
I installed Hugo locally to start building my site:

```
# For macOS
brew install hugo

# Verify installation
hugo version
```

### Initializing the Site
I initialized my Hugo project and added the Paper theme:

```
hugo new site my-hugo-site
cd my-hugo-site
git init
git submodule add https://github.com/nanxiaobei/hugo-paper themes/paper
```

I configured the theme in `hugo.toml`:

```
theme = "paper"
```

You can find all the config items of hugo configuration in my GitHub -> [hugo.toml](https://github.com/masoodazizi/my-hugo-site/blob/main/hugo.toml)

---

## 3. Customizing My Website

### Homepage Setup
I customized the homepage by adding parameters in the `hugo.toml` file:
- **Avatar:** Linked my Gravatar profile to display my photo.
- **Bio:** Added my name and a short professional bio to the homepage.
- **Social Links:** Configured my GitHub, LinkedIn, and Twitter profiles to appear as clickable icons.

---

## 4. Adding Content

### Blog Posts
To create blog posts, I used Hugo’s command-line tool:

```
hugo new posts/my-first-post.md
```

Each post is written in Markdown, making it easy to structure content. Posts are automatically listed on the homepage.

### CV Page
I created a dedicated **CV page** in Markdown to highlight my professional journey. The page is scannable, well-structured, and always up-to-date, offering potential employers or collaborators a clear overview of my skills and experience.

### Contact Page
For my contact page, I integrated **Formspree**, which allows me to receive messages directly via email without a backend setup. Benefits of Formspree include:
- **No Backend Required:** Works seamlessly for static sites.
- **Email Notifications:** Sends form submissions to my email instantly.
- **User-Friendly Setup:** Embedding the form takes just a few lines of HTML.

Here’s the embedded form code:

```
<form action="https://formspree.io/f/your-form-id" method="POST">
  <label for="name">Name:</label>
  <input type="text" id="name" name="name" required>
  
  <label for="email">Email:</label>
  <input type="email" id="email" name="_replyto" required>
  
  <label for="message">Message:</label>
  <textarea id="message" name="message" rows="5" required></textarea>
  
  <button type="submit">Send</button>
</form>
```

---

## 5. Deploying My Site

### GitHub Pages Settings
Before the deployment workflow was configured, I updated the **GitHub Pages settings** in the repository:
1. **Enable GitHub Pages**: Go to **Settings > Pages**, select the source of build and deployment `Deploy from a branch` and then choose the branch `gh-pages`, and save.
2. **Custom Domain**: Add the domain in the GitHub Pages settings.
3. **Enforce HTTPS**: Ensure TLS is enabled for secure access to the site.

![GitHub Pages Settings](/images/github-pages-settings.png)

### Automating with GitHub Actions
I automated deployment using GitHub Actions, which builds the site and publishes it to GitHub Pages. My `.github/workflows/deploy.yml` file:

```
name: Deploy Hugo Site

on:
  push:
    branches:
      - main

jobs:
  build-deploy:
    runs-on: ubuntu-latest
    steps:
    - name: Checkout Code
      uses: actions/checkout@v3

    - name: Setup Hugo
      uses: peaceiris/actions-hugo@v2
      with:
        hugo-version: "latest"

    - name: Build Site
      run: hugo

    - name: Deploy to GitHub Pages
      uses: peaceiris/actions-gh-pages@v3
      with:
        github_token: ${{ secrets.GITHUB_TOKEN }}
        publish_dir: ./public
        publish_branch: gh-pages
```

---

## 6. Final Touches

### Footer Customization
To remove or modify the theme information in the footer, I edited the layout files in `themes/paper/layouts/`. Alternatively, some themes allow this customization via the `hugo.toml` file.

### SEO and Social Optimization
I added Open Graph and Twitter metadata to improve how my site appears in search results and social shares. This helps create a professional and engaging first impression.

### Public Repository
The full source code of my website is available [on GitHub](https://github.com/masoodazizi/my-hugo-site). Feel free to explore or adapt it for your own project.

---

## Conclusion

Building a personal website with Hugo and GitHub Pages has been an incredible learning experience. My website now serves as a hub for my blog, an online CV, and a professional contact page. With tools like Hugo, Formspree, and a custom domain, creating a modern, professional online presence is easier than ever.

If you’re inspired to create your own site, check out my [GitHub repository](https://github.com/masoodazizi/my-hugo-site) for the source code and follow these steps. Happy building!

---

*Prefer reading on Medium? [Check it out here](https://medium.com/@masoodazizi.com/level-up-your-online-presence-build-your-personal-website-with-ease-bd8a8c34625a).*
