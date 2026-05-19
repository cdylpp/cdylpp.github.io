# Cody J. Lepp

Personal website for Cody J. Lepp, built with Jekyll and hosted on GitHub Pages at <https://cdylpp.github.io>.

## Local Development

```sh
bundle install
bundle exec jekyll serve
```

## Deployment

Pushing to `main` runs the GitHub Actions workflow in `.github/workflows/deploy.yml`, builds the Jekyll site, and publishes `_site` to GitHub Pages.
