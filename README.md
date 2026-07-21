# Clemens Leopold - Personal Website

Personal blog and project portfolio built with Jekyll and the Minima theme.

## About

This is my personal corner of the web where I share my coding journey, projects, and occasional musings about contemporary art and life in Berlin. The site serves as both a portfolio and a blog documenting my ongoing work and interests.

## Features

- Blog posts about art exhibitions, personal projects, and coding
- Front-page post list with per-post thumbnail graphics
- CV/Resume page
- Clean, minimalist design
- Responsive layout
- Auto-generated sitemap (`/sitemap.xml`) for search engines

## Tech Stack

- **Jekyll** - Static site generator
- **Minima** - Jekyll theme
- **GitHub Pages** - Hosting and deployment
- **Claude Code** - For development
- **SCSS** - Styling and responsive design
- **jekyll-sitemap** - Sitemap generation

## Local Development

To run the site locally:

```bash
bundle install
bundle exec jekyll serve
```

The site will be available at `http://localhost:4000`

## Structure

```
_posts/          # Blog posts
_layouts/        # Custom theme layout overrides (e.g. home.html)
_includes/       # Custom template partial overrides
assets/          # Images, CSS, and other static files
_config.yml      # Site configuration
index.markdown   # Homepage
CV.markdown      # Resume/CV page
```

Post URLs follow `/:year/:month/:day/:title/` and don't include categories, so a post's `categories` front matter is safe to set as a YAML list (e.g. `categories: [coding, claudecode]`) without affecting its URL.

### Post thumbnails

The front page (`_layouts/home.html`, which overrides Minima's default) shows a thumbnail beside each post. Set the image per post via the `thumbnail` front-matter field:

```yaml
thumbnail: /assets/images/my-image.png
```

Posts without a `thumbnail` fall back to `default_thumbnail` in `_config.yml` (`/assets/images/placeholder.svg`).

## Contact

- GitHub: [@febtwenty](https://github.com/febtwenty)
- LinkedIn: [Clemens Leopold](https://linkedin.com/in/clemens-leopold)

## License

Content © 2025 Clemens Leopold. All rights reserved.

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

The MIT License applies to the code, design, and site structure. Blog posts, images, and other original content remain under copyright.

---

Built with Jekyll and hosted on GitHub Pages.
