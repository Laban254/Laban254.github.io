
# Dev Kibe Blog

Welcome to my personal blog powered by Jekyll! This blog is a space where I share insights, tutorials, and experiences related to software development.

## Table of Contents

- [Introduction](#introduction)
- [Getting Started](#getting-started)
- [Configuration](#configuration)
- [Adding Posts](#adding-posts)
- [Deployment](#deployment)
- [Contributing](#contributing)
- [License](#license)

## Introduction

This blog uses Jekyll, a simple, blog-aware static site generator. Jekyll allows you to write your content in Markdown, making it easy to create and manage blog posts.

## Getting Started

### Prerequisites

- Ruby installed (version 2.5 or higher)
- Bundler gem (install using `gem install bundler`)
- Jekyll gem (install using `gem install jekyll`)

### Installation

1. Clone the repository:

   ```bash
   git clone https://github.com/Laban254/Laban254.github.io.git
   cd Laban254.github.io`` 

2.  Install dependencies:
    
    `bundle install` 
    
3.  Serve the site locally:
   
    
    `bundle exec jekyll serve` 
    
    Your site will be running at `http://127.0.0.1:4000`.
    

## Configuration

The main configuration file for your Jekyll site is located at `_config.yml`. You can customize the following fields:

-   **title**: The title of your blog
-   **email**: Your contact email
-   **description**: A short description of your blog
-   **author**: Your name
-   **baseurl**: If using a subpath, set it here; otherwise, keep it empty.
-   **url**: Your GitHub Pages URL (e.g., `https://laban254.github.io`)

## Adding Posts

To add a new blog post:

1.  Create a new Markdown file in the `_posts` directory. The filename should follow this format: `YYYY-MM-DD-title.md`.
    
2.  Use the following front matter template at the beginning of your post:

    
  

      ---
        layout: post
        title: "Your Post Title"
        date: YYYY-MM-DD HH:MM:SS +/-TZ
        categories: category1 category2
        ---
    
3.  Write your post in Markdown below the front matter.
    

## Deployment

Your site is automatically deployed to GitHub Pages when you push changes to the `main` branch of this repository. Make sure to build your site and commit the changes to reflect updates.

## Contributing

Contributions are welcome! Please feel free to submit a pull request or raise an issue if you have any suggestions or improvements.

## License

This project is licensed under the MIT License. See the LICENSE file for more details.