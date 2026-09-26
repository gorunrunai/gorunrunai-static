# Used both for the local preview and by the GitHub Actions build that publishes the site.
#   bundle install && bundle exec jekyll serve    # http://127.0.0.1:4000
source "https://rubygems.org"
gem "jekyll", "~> 4.4"
group :jekyll_plugins do
  gem "jekyll-remote-theme"
  gem "jekyll-seo-tag"
  gem "jekyll-sitemap"
  gem "jekyll-include-cache"
end
gem "webrick"
# Standard libraries that newer Rubies no longer bundle.
gem "csv"
gem "base64"
gem "bigdecimal"
gem "logger"
