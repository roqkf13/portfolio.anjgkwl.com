source "https://rubygems.org"

# Jekyll 본체. GitHub Actions로 빌드/배포하는 것을 전제로 4.x 사용.
# (클래식 GitHub Pages 빌드를 쓸 경우 이 줄 대신 github-pages gem을 써야 함 — README 참고)
gem "jekyll", "~> 4.4"

# 기본 테마
gem "minima", "~> 2.5"

group :jekyll_plugins do
  gem "jekyll-feed", "~> 0.12"
  gem "jekyll-seo-tag", "~> 2.8"
  gem "jekyll-sitemap", "~> 1.4"
end

# Windows / JRuby 환경 보정 (WSL에서는 설치되지 않음)
platforms :mingw, :x64_mingw, :mswin, :jruby do
  gem "tzinfo", ">= 1", "< 3"
  gem "tzinfo-data"
end

gem "wdm", "~> 0.2", :platforms => [:mingw, :x64_mingw, :mswin]
gem "http_parser.rb", "~> 0.6.0", :platforms => [:jruby]
