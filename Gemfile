source "https://rubygems.org"

# Jekyll version is pinned by the github-pages meta-gem so that local builds
# match what GitHub Pages actually runs. Run Jekyll with `bundle exec`:
#
#     bundle exec jekyll serve --livereload
#
gem "github-pages", group: :jekyll_plugins

group :jekyll_plugins do
  gem "jekyll-feed"
  gem "jekyll-sitemap"
end

# --- Ruby 3.4+ compatibility -------------------------------------------------
# These were bundled gems in the stdlib and were removed in Ruby 3.4/3.5.
# github-pages pins Jekyll 3.10, which predates that change, so declare them.
gem "base64"
gem "bigdecimal"
gem "csv"
gem "logger"
gem "ostruct"
gem "webrick"

# Windows-only filesystem watcher
gem "wdm", "~> 0.1.0" if Gem.win_platform?
