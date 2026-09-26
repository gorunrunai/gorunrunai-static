# gorunrunai.github.io

Source for **[gorunrunai.github.io](https://gorunrunai.github.io)**, the website of [GoRunRun Local AI](https://github.com/gorunrunai/local-ai).

The site is plain Markdown built with Jekyll and the [Just the Docs](https://just-the-docs.com) theme, published by a GitHub Actions workflow. Edit a `.md` file, push to `main`, and the site updates within a minute or two.

| Page | File |
|---|---|
| Home | `index.md` |
| Install | `install.md` |
| User guide | `guide/*.md` |
| Screenshots | `screenshots.md` (images in `assets/images/`) |
| FAQ, Privacy | `faq.md`, `privacy.md` |
| Developers | `developers/*.md` |

Preview locally (needs Ruby):

```sh
bundle install
bundle exec jekyll serve    # http://127.0.0.1:4000
```

## Hosting setup (one time)
1. Repository **Settings → Pages**: Source **GitHub Actions**. `.github/workflows/pages.yml` builds the site with the `Gemfile`'s Jekyll (the same as the local preview) and publishes it on every push to `main`, at `https://gorunrunai.github.io/` (this repo's name makes it the organization's root site).
2. Optional custom domain, e.g. `local.gorunrun.ai`: enter it under **Settings → Pages → Custom domain** (with the Actions build, that setting is used, not a `CNAME` file), set `url:` in `_config.yml` to match, and turn on **Enforce HTTPS** once the certificate is issued. `gorunrunai.github.io` then redirects to it.
3. For that domain, a DNS `CNAME` record at your registrar: `local` pointing to `gorunrunai.github.io`.
4. Optional: verify `gorunrun.ai` for the organization under **Organization settings → Pages** to protect the domain.

## License

The website's content and design are proprietary: © 2026 GoRunRun, all rights reserved. See [LICENSE](LICENSE).
The GoRunRun Local AI app itself is open source under the Apache License 2.0, in [its own repository](https://github.com/gorunrunai/local-ai).
