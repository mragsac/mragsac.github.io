# mragsac.github.io

This repository contains code for the website hosted at https://mragsac.github.io through `gh-pages` at the custom domain https://mragsac.com. It was built using [`quarto`](https://quarto.org/), an [open-source](https://github.com/quarto-dev) scientific and technical publishing system sponsored by [Posit, PBC](https://posit.co/). 

## Interested in using `quarto` for a GitHub website?

If you're interested in using `quarto` for your own site, I recommend following the steps below to get started with a simple static webpage.

1. Download `quarto` for your system and tool of choice from the [Getting Started](https://quarto.org/docs/get-started/) page. I use `quarto` for macOS and [Visual Studio Code](https://code.visualstudio.com/)!

2. Create a [website project](https://quarto.org/docs/websites/) using the `quarto` CLI utility where `$WEBSITE_NAME_HERE` is `$GITHUB_USERNAME.github.io`

```bash
# Create a new website project with the quarto CLI
quarto create project website $WEBSITE_NAME_HERE
```

3. After creating a new website project, make sure you have the following files present: 
    * `_quarto.yml` : Website options and HTML defaults for documents created for the website (this includes [navigation options](https://quarto.org/docs/websites/website-navigation.html), [search options](https://quarto.org/docs/websites/website-search.html), and [other tools](https://quarto.org/docs/websites/website-tools.html))
    * `index.qmd` : Landing page for your website (mine is configured like an [about page](https://quarto.org/docs/websites/website-about.html) to take advantage of existing templates)
    * `404.qmd` : Default stylings for a [`404` website page](https://quarto.org/docs/websites/website-navigation.html#pages-404)
    * `.gitignore` : Specifies files to ignore when uploading to GitHub, such as the `/.quarto/` hidden folder and `/_site/` default directory
    * `.nojekyll` : Prevents additional processing of the `quarto` website with Jekyll (turned on by default by GitHub)
    
> [!NOTE]  
> If you're interested in creating a blog or archive of posts on your personal website, `quarto` also has that functionality! You can find more information on `quarto`'s documentation for [Listing Pages](https://quarto.org/docs/websites/website-listings.html).

## Configuring the `_quarto.yml` file to export to a custom directory for easy deployment

I've published my site with GitHub Pages using the [documentation](https://quarto.org/docs/publishing/github-pages.html) on the `quarto` website, but to make things easier for others, I've reproduced the steps I took here.

1. Change the default website rendering directory from `/_sites/` to `docs` by specifying it as the output directory in the `_quarto.yml` configuration file

```yaml
# _quarto.yml

project:
  type: website
  output-dir: docs
```

2. Next, render the website and initialize all files to add to your `$GITHUB_USERNAME.github.io` repository 

```bash
# First render the website and then add the rendered files to GitHub 
quarto render
git add docs
git commit -m "Publish site to docs/"
git push
```

3. Finally, configure your GitHub repository (`$GITHUB_USERNAME.github.io`) to publish from the `/docs/` directory of your `main` branch in the `Settings > Pages` section under "Code and automation"

Once you've set this up, GitHub will trigger a deployment of your website to the `https://$GITHUB_USERNAME.github.io` URL (or a custom domain if you have that configured) whenever you commit and push to your `main` branch!
