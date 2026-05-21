# Website Quick Start

This site is a Jekyll site hosted with GitHub Pages. Most content lives in Markdown or YAML files, so normal updates do not require editing HTML layouts.

## Common Files

- `_pages/about.md`: home page content, profile image settings, subtitle, and portfolio text.
- `_pages/projects.md`: projects landing page. It lists project files from `_projects/`.
- `_pages/cv.md`: CV/history page wrapper. Most CV content comes from `_data/cv.yml`.
- `_projects/`: one Markdown file per project card/detail page.
- `_data/cv.yml`: profile, education, work history, interests, and CV sections.
- `_data/socials.yml`: social links shown by the theme.
- `_config.yml`: global site settings, author info, navigation behavior, analytics, and enabled features.
- `assets/img/`: images used by pages and projects.

## Run the Site Locally

This project is built with Ruby `3.3.5`, matching the GitHub Actions workflow. Do not use the macOS system Ruby at `/usr/bin/ruby`; it is usually too old for this site.

Check your Ruby version:

```sh
ruby -v
which ruby
```

If you use `rbenv`, install and select the project Ruby:

```sh
brew install rbenv ruby-build
echo 'eval "$(rbenv init - zsh)"' >> ~/.zshrc
eval "$(rbenv init - zsh)"
RUBY_CONFIGURE_OPTS="--disable-yjit" rbenv install 3.3.5
rbenv local 3.3.5
rbenv rehash
ruby -v
which ruby
```

Install the Bundler version required by `Gemfile.lock` after Ruby `3.3.5` is active:

```sh
gem install bundler:2.5.18
```

Install dependencies once:

```sh
bundle install
```

Start the local server:

```sh
bundle exec jekyll serve
```

Open the local URL printed by Jekyll, usually:

```text
http://127.0.0.1:4000/
```

If Jekyll is already running and you edit content, refresh the browser. Most Markdown, YAML, Sass, and config changes rebuild automatically.

## Add a Page

Create a new Markdown file in `_pages/`, for example `_pages/contact.md`.

Use front matter like this:

```md
---
layout: page
title: contact
permalink: /contact/
description: Contact information.
nav: true
nav_order: 4
---

Page content goes here.
```

Key fields:

- `layout`: usually `page`. The home page uses `about`, and the CV page uses `cv`.
- `title`: page title shown by the theme.
- `permalink`: public URL for the page. Use leading and trailing slashes, like `/contact/`.
- `nav`: set to `true` if the page should appear in the top navigation.
- `nav_order`: controls navigation order. Lower numbers appear first.

After adding a page, run the site locally and check the new URL.

## Update an Existing Page

Edit the Markdown file for the page:

- Home page: `_pages/about.md`
- Projects page: `_pages/projects.md`
- CV/history page wrapper: `_pages/cv.md`
- 404 page: `_pages/404.md`

Keep the front matter between the opening and closing `---` lines. The content below the second `---` is normal Markdown and can be edited freely.

For the home page, the `profile` block controls the image and contact box:

```yaml
profile:
  align: right
  image: me.jpeg
  image_circular: true
  more_info: >
    <p>San Diego, CA</p>
    <p><a href="mailto:cdylpp@gmail.com">cdylpp@gmail.com</a></p>
```

Images referenced here should be placed in `assets/img/`.

## Add or Update Projects

Each project is a separate file in `_projects/`.

To add a project, create a file like `_projects/my-project.md`:

```md
---
layout: page
title: My Project
description: Short description shown on the projects page.
img:
importance: 5
category: software
github: https://github.com/cdylpp/my-project
---

Longer project description goes here.
```

Notes:

- `importance` controls sort order. Lower numbers appear earlier.
- `description` appears on the project card.
- `github` adds a GitHub link.
- `img` can be left blank, or set to an image filename from `assets/img/`.

To update a project, edit its file in `_projects/`.

To remove a project, delete its file from `_projects/`, then run the site locally and check `/projects/`.

## Update CV or Social Links

Edit `_data/cv.yml` to change the CV/history content. Preserve the indentation because YAML depends on spaces.

Common section types in this site:

- `map`: key/value profile rows.
- `time_table`: dated education, work, or project entries.
- `nested_list`: grouped bullet lists.
- `list`: simple bullet lists.

Edit `_data/socials.yml` to change social icons and links. Uncomment or add only the accounts you want shown.

## Update Site Settings

Edit `_config.yml` for global settings such as:

- Site title, description, keywords, and author info.
- Footer text.
- Analytics IDs.
- Navigation and layout settings.
- Feature toggles like announcements, latest posts, search, and RSS.

After changing `_config.yml`, restart Jekyll if the local server does not pick up the change.

## Remove Content Safely

Before removing anything, find where it is referenced:

```sh
rg "thing-to-remove"
```

Safe removal checklist:

1. Remove the content from the source file.
2. Remove links to that content from other pages.
3. Remove related images only after confirming no page still references them.
4. Run `bundle exec jekyll serve`.
5. Visit the changed pages and check the terminal for build errors.

Be careful with these files:

- Do not remove `_config.yml`.
- Do not remove `_pages/about.md` unless another page has `permalink: /`.
- Do not remove front matter from Markdown files.
- Do not change YAML indentation casually.
- Do not delete theme files in `_layouts`, `_includes`, `_sass`, or `_plugins` unless you are intentionally changing the theme.

## Check Changes Before Committing

See what changed:

```sh
git status
git diff
```

Run the site locally:

```sh
bundle exec jekyll serve
```

Check the pages you changed in the browser. Also check the terminal for Jekyll errors or warnings.

## Commit and Publish

Stage the files you changed:

```sh
git add QUICKSTART.md _pages/about.md _projects/my-project.md
```

Commit with a short message:

```sh
git commit -m "Update website content"
```

Push to GitHub:

```sh
git push
```

Pushing to `main` runs the GitHub Actions workflow in `.github/workflows/deploy.yml` and publishes the site to GitHub Pages.

After pushing, check:

- The GitHub Actions run completed successfully.
- The live site at `https://cdylpp.github.io` shows the expected changes.

## Quick Troubleshooting

- If `bundle install` says `Could not find 'bundler' (2.5.18)`, check `ruby -v` and `which ruby`. If you see Ruby `2.6` or `/usr/bin/ruby`, switch to Ruby `3.3.5`, then run `gem install bundler:2.5.18` and `bundle install` again.
- If `rbenv install 3.3.5` fails while linking YJIT on macOS arm64, install it with `RUBY_CONFIGURE_OPTS="--disable-yjit" rbenv install 3.3.5`.
- If `gem install` says you do not have write permissions for `/Library/Ruby/Gems/2.6.0`, stop and switch to the rbenv Ruby first. Do not use `sudo gem install` for this project.
- If the site will not build, read the first error in the Jekyll terminal output.
- If a page is missing, check its `permalink` and make sure `_pages` is still included in `_config.yml`.
- If navigation is wrong, check `nav: true` and `nav_order`.
- If a project is missing, check that the file is in `_projects/` and has valid front matter.
- If an image is missing, confirm the filename matches exactly and the image is in `assets/img/`.
- If YAML errors appear, check indentation and missing colons in `_config.yml` or `_data/*.yml`.
