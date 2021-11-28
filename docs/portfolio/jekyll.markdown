# Creating a static website using Jekyll

Jekyll is a piece of software that allows users to quickly create and customise static websites or blogs. These websites can then be hosted on various platforms.

For example, Github Pages offers to host Jekyll generated static websites for free. On other platforms such as Amazon S3 you can pay a small fee per month depending on the size of the content you wish to store. Static websites are less demanding than dynamic websites so are a cheaper alternative which adds to their appeal.

This document provides instructions on how to:
- [Install Jekyll](#installing-jekyll)
- [Create a static website](#creating-a-static-website)
- [Customise your website](#customising-your-website)
- [Add content to your website](#adding-content-to-your-website)

**Note:** This document only covers users of Windows 10 devices. For other Operating Systems like macOS or Linux, there are guides available [here](https://jekyllrb.com/docs/installation/).

---


## Installing Jekyll
Jekyll is written in Ruby so this must be installed first.

1\. Download the recommended [RubyInstaller](https://rubyinstaller.org/downloads/) for Windows.

2\. Execute the executable file (`*`.exe), accept the licence terms and conditions, and select the default settings.

3\. After installation, select the checkbox for "Run `ridk install` to set up MSYS2 and toolchain. MSYS2 is required to install gems with C extensions", and then select "Finish."

4\. A command prompt window automatically opens and asks you what type of MSYS2 installation to start. Press the "Enter" key on your keyboard to select the default installation. Once this has completed, close the window.

You now have [Ruby](https://www.ruby-lang.org/en/) and [RubyGems](https://rubygems.org/) installed on your computer. RubyGems is a package management framework for Ruby that we can now use to install Jekyll.

5\. Open command prompt and make sure you are in your user directory. E.g. `C:\Users\<your_name>`. This ensures that when you install Jekyll, it is added to the `PATH` environment variable which will allow Jekyll to be executed anywhere in your file system without having to specify its source directory.

 Use RubyGems to install Jekyll and a package called bundler which Jekyll will need to generate a static site:
<pre><code>gem install jekyll bundler
</code></pre>
6\. Once the process has completed, check that Jekyll is installed by entering the following command:
<pre><code>jekyll -v
</code></pre>
If the installation has been successful then you should see, for example:
<pre><code>jekyll 4.2.0
</code></pre>
**Note:** The version you see may be different from the example. What is important is that you do see a version number.

## Creating a static website
Now that you have successfully installed Jekyll it is now easy to create a static website in a few simple steps.

1\. Firstly, open command prompt and navigate with the `cd` command to where you want your static website files to be generated and stored.

2\. To create a static website in the current directory, enter the following command:
<pre><code>jekyll new .
</code></pre>

If you want to create a static website in a new folder within your current directory then enter:

<pre><code>jekyll new ./&lt;new_folder&gt;
</code></pre>
Where you substitute `<new_folder>` with the name of your new folder.

3\. If you created a new folder in the last step, navigate to where you created your site. To test the site locally, enter:
<pre><code>bundle exec jekyll serve
</code></pre>
4\. You can now access and view this site at: [http://localhost:4000/](http://localhost:4000/). Open a browser and browse to this URL to preview your new website. To stop this process you can press CTRL and C keys simultaneously on your keyboard in the command prompt window. Command prompt asks for confirmation twice. Enter `y` when prompted twice to successfully stop the process.

## Customising your website
Your new jekyll site will have the following structure by default:
<pre><code>.
├── Gemfile
├── Gemfile.lock
├── _config.yml
├── _posts
├── about.markdown
└── index.markdown
</code></pre>

The first and most important file to configure is the `_config.yml` file. This file is what Jekyll uses to build your website. Any time you make a change to this file you need to rerun `bundle exec jekyll serve` to see the changes locally.

In the `_config.yml` file you can configure the following:

### Site settings
<pre><code>title: #The title of your website
email: your-email@example.com
description: # Your website description that will appear in your document head meta (for
  Google search results) and in your feed.xml site description.
baseurl: "" # the subpath of your site, e.g. /blog
url: "" # the base hostname & protocol for your site, e.g. http://example.com
twitter_username: jekyllrb
github_username:  jekyll
</code></pre>

If you don't want to configure certain variables because you don't intend to use them e.g. `twitter_username`, then leave them empty.

### Build settings
In the Build Settings you can choose what style your Jekyll site uses by selecting a theme. By default the style of your website is set to the Jekyll [Minima](https://github.com/jekyll/minima) theme. There are many other themes available on various websites such as:
- [GitHub.com #jekyll-theme repos](https://pages.github.com/themes/)
- [jamstackthemes.dev](https://jamstackthemes.dev/)
- [jekyllthemes.org](http://jekyllthemes.org/)
- [jekyllthemes.io](https://jekyllthemes.io/)
- [jekyll-themes.com](https://jekyll-themes.com/)

If you intend to host your website on Github Pages and want to use one of their supported themes then to configure your desired theme you must edit the following variable in the `_config.yml` file:

<pre><code>theme: minima
</code></pre>

If you want to use a different theme that is available on a public Github repository then you must replace the theme variable instead with:
<pre><code>remote_theme: OWNER/REPOSITORY
</code></pre>
For example, you could choose: `benbalter/retlab`

You can also configure additional Jekyll plugins in this file but this is more advanced and is not covered in this documentation. All the necessary plugins needed to support a Jekyll site are already installed by default. More information can be found [here](https://jekyllrb.com/docs/plugins/installation/).

Depending on the design of your theme there may be other variables that you can configure here. Make sure to consult the `README.md` of your theme to see what is available.

### Further theme customisations
Outside of the `_config.yml` file, most themes allow for further customisation and have additional folders as part of their theme for this purpose.
This can include some of the following:
- Being able to adjust the graphics used on your website in a `_data` or `assets` folder.
- Being able to configure your social media URLs or webpage navigation URLs in a `_data` folder.
- Being able to configure tags and images for your pages or blog posts in a `_data` folder.

Each theme's `README.md` has further details on what is possible in this area.

### Overriding theme defaults
You can override parts of a Jekyll theme if you want to make small changes to it. Typically a Jekyll theme has the following structure:
<pre><code>.
├── assets
├── _config.yml
├── _data
├── _includes
├── _layouts
├── _posts
├── _sass
├── _site
└── index.html
</code></pre>
However if the theme is gem-based you may not see all these folders available to you in your site directory. This is because they are stored in the Ruby Gem elsewhere on your device. However Jekyll is written so that it will consult your site directory first for the following files and if nothing is present it will use the defaults in the Ruby Gem:

---

Folder|Purpose
--- | ---
`/assets` | Typically contains the main CSS style theme
`/_layouts` | Contains template HTML pages for default, pages and blog posts
`/_includes` | Contains smaller template HTML pieces for items like headers and footers
`/_sass` | Contains smaller parts of your CSS style theme  

---

  To override the files within these folders you only need to copy the desired file to your site directory and modify it. To find the location of a gem's files on your device you need to open command prompt and enter:
<pre><code>bundle info --path &lt;theme&gt;
</code></pre>

Where `<theme>` is substituted for your theme name.

With this method you can then modify default font colours or edit the style of your website footer, for example.

**Note:** You must restrict your modifications to only within these folders specified above or listed in your theme's documentation. Any changes you make in other folders will be overwritten the next time you build the site locally. This doesn't apply to any new folders that you create for your own purposes.

### Overriding the website landing page
Your website landing page is typically configured through your `index.html` file. You can override this by creating an `index.md` file in your site directory and configuring it to the desired layout in the YAML front matter of the file.

For example, by default your theme landing page is a summary of your recent blog posts and you want it instead to be a webpage. So in your `index.md` you can configure the YAML front matter to the following:
<pre><code>---
layout: page
title: Home
permalink: /
---
</code></pre>
Within this configuration you have specified the layout template that the webpage should follow, i.e. page. You've specified its title: "Home", and specified that the permalink should be the root of the site. So whenever the website is first accessed, this is the page that is navigated to. Now you only need to add your desired content to the `*.markdown` file.

## Adding content to your website
Written content can be added to your website by adding `*.markdown` files within your site directory. Each file must begin with YAML front matter where you specify the layout template and other details so that Jekyll will understand how to structure the HTML page. Typically there are three types of layout:
- default
- page
- post

Any new pages can be placed in the main site directory or subfolders. For example, articles in a portfolio section of the site. You can specify a permalink in the front matter to explicitly configure the URL that navigates to this page.

Blog posts that use the "post" layout should be stored within the `_posts` directory.

### Adding content with images
Within your `*.markdown` files you can use markdown syntax to include an image in your content.
For example:
<pre><code>![](image.jpg)
</code></pre>
You must provide the correct path to the image. This path must be in reference to the current file's location. So if your `*.markdown` file is in the main directory of your website and your image is under `assets` then your path should be: `/assets/image.jpg`

But if your `*.markdown` file is in a subfolder of the main directory, then to explain to Jekyll that the image folder it is looking for is one directory up, you must add a `../`. For example:
<pre><code>![](../assets/image.jpg)
</code></pre>

Written by Sarah Haggarty
