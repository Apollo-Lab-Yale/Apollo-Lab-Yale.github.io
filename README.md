# Apollo Lab Website

This website is modified based on the Jekyll theme [petridish](https://github.com/peterdesmet/petridish).

## Table of Contents
- [Setup for Local Development](#setup-for-local-development)
- [Structure](#structure)
- [Adding Content](#adding-content)
    - [News](#news)
    - [Publications](#publications)
    - [Lab Members](#lab-members)
    - [Pages](#pages)


## Setup for Local Development
1. Install Jekyll following the [official quickstart guide](https://jekyllrb.com/docs/).
    - Preferably, install Ruby+Devkit 2.78 and RubyGems 3.4.20
2. Clone this repository to your computer
    ```
    git clone https://github.com/Apollo-Lab-Yale/Apollo-Lab-Yale.github.io.git
    ```
3. Navigate to the cloned repository
    ```
    cd Apollo-Lab-Yale.github.io
    ```
4. Install bundle executables
    ```
    bundle install
    ```
5. Run the website locally
    ```
    bundle exec jekyll serve
    ```

## Structure

The repository structure follows that of Jekyll websites.

- General site settings: [_config.yml](_config.yml)
- Pages: [pages/](pages/)
- Posts: [_posts/](_posts/) (posts in this folder are displayed on the news page)
- Images & static files: [assets/](assets/)
- Top navigation: [_data/navigation.yml](_data/navigation.yml)
- Footer content: [_data/footer.yml](_data/footer.yml)
- Team members: [_data/team.yml](_data/team.yml)

## Adding Content
### News
- Create a new file in [_posts/](_posts/) with the following filename format: `YYYY-MM-DD-title.md`
- Add the following header to the file:
    ```
    ---
    title: <title>
    description: <description>
    background:
      img: <image path>
    ---
    ```
    - `title` is the title of the news post
    - `description` is the description of the news post
    - `img` is the path to the image to be displayed on the news post. The image should be placed in folder named following the format `YYYY-MM-DD` in [assets/theme/images/news/](assets/theme/images/news/). If the folder does not exist, create it.
- Add the content of the news post below the header

### Publications
- Add a new entry to [_data/publications.yml](_data/publications.yml) following the format of the existing entries.

### Lab Members
- Add a new entry to [_data/team.yml](_data/team.yml) following the format of the existing entries.
- Add a profile picture of the lab member to [assets/theme/images/team/](assets/theme/images/team/). The image should be named following the format `firstname_lastname.jpg` or `firstname_lastname.png`.

### Pages
- Create a new file in [pages/](pages/) with the following filename format: `title.md`
- Add the following header to the file:
    ```
    ---
    title: <title>
    permalink: /<permalink>/
    ---
    ```
    - `title` is the title of the page
    - `permalink` is the permalink of the page
- Add the content of the page below the header
- Add the page to the navigation bar by adding the following entry to [_data/navigation.yml](_data/navigation.yml):
    ```
    - text: <title>
      href: /<permalink>/
    ```
    - `text` is the title of the page
    - `href` is the permalink of the page

