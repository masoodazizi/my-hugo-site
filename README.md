# My Hugo Site

Welcome to **Masood's Digital Space**, a minimalist and professional Hugo-powered website built with the **Paper theme**, and hosted on GitHub Pages. This repository contains all the source files and configuration needed to build and deploy the site.

## Features
- **Modern Hugo Framework**: Fast and customizable static site generator.
- **Paper Theme**: A clean and minimalist design for showcasing content effectively.
- **GitHub Pages Deployment**: Automatically deployed via GitHub Actions.
- **Responsive Design**: Works seamlessly across devices.
- **Blog-ready**: Includes blog posts like "Welcome to My Blog" and supports images and Markdown.

## Tools and Technologies Used

- **Hugo Framework**: A fast and flexible static site generator for building lightweight websites.
- **Paper Theme**: A minimalist and responsive theme for professional-looking websites.
- **GitHub Repository**: Source code hosted on GitHub for version control and collaboration. [Explore the repository](https://github.com/masoodazizi/my-hugo-site).
- **GitHub Actions**: Automation for building and deploying the site to GitHub Pages.
- **GitHub Pages**: Reliable and free hosting with seamless integration for static websites.

## How the Site Was Built

This website was created through a series of steps:
1. Initializing a new Hugo site and configuring the Paper theme.
2. Adding content, including blog posts, a CV page, and a contact page.
3. Integrating a custom domain and setting up HTTPS via GitHub Pages.
4. Automating the deployment process using GitHub Actions.
5. Customizing the site's SEO, metadata, and layout for a professional online presence.

For a detailed walkthrough of the process, including all configuration steps and tools used, read the full blog post:
[How to Build and Publish a Personal Website](https://masoodazizi.com/how-to-build-and-publish-a-personal-website/)

## Deployment

The site is automatically built and deployed using GitHub Actions. The workflow file ensures that every push to the `main` branch triggers a build and deploys the static files to the `gh-pages` branch.

### Deployment Workflow

The deployment is configured using the `.github/workflows/deploy.yml` file:
```yaml
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

## How to Run Locally

To preview or contribute to the site, clone the repository and run Hugo locally:

1. Clone the repository:
   ```bash
   git clone https://github.com/masoodazizi/my-hugo-site.git
   cd my-hugo-site
   ```

2. Run the Hugo development server:
   ```bash
   hugo server
   ```

3. Open your browser and navigate to `http://localhost:1313` to view the site (The port may differ).

## Acknowledgments

Special thanks to the creators of:
- [Hugo](https://gohugo.io/)
- [Paper Theme](https://github.com/nanxiaobei/hugo-paper)
- [GitHub Actions](https://github.com/features/actions)
- [Formspree](https://formspree.io/)

## License

This project is licensed under the [MIT License](LICENSE).

## Blog Post

For a detailed guide on how this site was built and published, check out the blog post:
[How to Build and Publish a Personal Website](https://masoodazizi.com/how-to-build-and-publish-a-personal-website/)

Feel free to explore, fork, or contribute to the repository!
