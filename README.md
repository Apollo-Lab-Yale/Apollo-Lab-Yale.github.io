# Apollo Lab Website

This website is modified based on the Jekyll theme [petridish](https://github.com/peterdesmet/petridish).

## Table of Contents
- [Setup for Local Development](#setup-for-local-development)
- [Structure](#structure)


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
