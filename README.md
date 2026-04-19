# Apollo Lab Website

This website is a modern, data-driven platform for the APOLLO Lab at Yale, built using Jekyll and refined with the "Elite" Apollo Design System.

## Table of Contents
- [Setup for Local Development](#setup-for-local-development)
- [Project Structure](#project-structure)
- [Adding & Managing Content](#adding--managing-content)
    - [News Feed](#news-feed)
    - [Research Threads](#research-threads)
    - [Lab Members](#lab-members)
    - [Publications](#publications)
- [Design Aesthetics](#design-aesthetics)

## Setup for Local Development
1. Install Jekyll following the [official quickstart guide](https://jekyllrb.com/docs/).
    - Preferably, install Ruby+Devkit 2.7.8 and RubyGems 3.4.20
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

## Project Structure

The site follows a **data-driven architecture**. Most content is managed in the `_data/` directory rather than individual markdown files.

- **Global Settings**: [_config.yml](_config.yml) (Manage site title, primary colors, and social links)
- **Content Engines**:
    - [_data/news.yml](_data/news.yml): The main news timeline.
    - [_data/research.yml](_data/research.yml): Research threads and homepage gallery media.
    - [_data/team.yml](_data/team.yml): Active and alumni lab members.
    - [_data/publications.yml](_data/publications.yml): Complete publication database.
- **Assets**:
    - [assets/theme/images/](assets/theme/images/): Categorized images for news, team, and research.
    - [assets/theme/videos/](assets/theme/videos/): Source videos for the homepage gallery and lab space.
- **Styling**: [_sass/_custom.scss](_sass/_custom.scss) (Controls the Elite mesh gradients and glassmorphism).

## Adding & Managing Content

### News Feed
News is managed in [_data/news.yml](_data/news.yml).
- **Format**: Add a new YAML entry at the top of the file.
- **Fields**: Include `title`, `date` (YYYY-MM-DD), `type` (e.g., paper, award), and `content`.
- **Automatic Styling**: The site automatically assigns icons based on the `type` or keywords in the `title`.

### Research Threads
Research is managed in [_data/research.yml](_data/research.yml).
- **Gallery Integration**: Entries with `gallery: true` and a valid `media_path` (image or video) will automatically appear in the homepage's auto-playing hero gallery.
- **Publication Linking**: Add exact paper titles to the `selected_publications` list within a thread to display them as "Selected Publications" on the research page.
- **Media Paths**: 
    - Images: `assets/theme/images/research/filename.jpg`
    - Videos: `assets/theme/videos/filename.mp4`

### Lab Members
Members are managed in [_data/team.yml](_data/team.yml).
- **Ordering**: No need to manually sort; the site automatically sorts members by last name (alphabetically) within their respective roles (PI, PhD, etc.).
- **Headshots**: Place images in `assets/theme/images/team/` and name them `firstname_lastname.jpg`.
- **Threads**: Link members to research threads by adding exact thread titles to their `threads` list.

### Publications
Publications are managed in [_data/publications.yml](_data/publications.yml).
- **Mapping**: Ensure the `title` field is accurate, as this is used to link papers to research threads and individual member profiles.
- **Filtering**: The publications page includes a live dashboard for filtering by research thread, year, and type.

## Design Aesthetics

The site uses a custom **Elite Apollo Design System** featuring:
- **Mesh Gradients**: Dynamic, animated backgrounds in page headers.
- **Glassmorphism**: Translucent "frosted glass" cards for titles and content overlays.
- **Color Sync**: Global colors are controlled via the `colors:` block in [_config.yml](_config.yml). Use the `apollo-primary` variables in SCSS for consistency.
