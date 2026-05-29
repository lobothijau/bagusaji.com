# bagusaji.com

Jekyll blog at [bagusaji.com](https://bagusaji.com).

## Requirements

* Ruby 3.4.5
* Node 22

## Usage

Start the dev server and visit [http://localhost:4000](http://localhost:4000).

```bash
bin/serve
```

Restart after changing `_config.yml`.

## Deploy

Netlify auto-deploys on push to `main`. Build config is in `netlify.toml`.

## Best practices

* Posts live in `_posts`, accessible via `site.posts`.
* Link to posts via `post_url`: `[My post]({% post_url 2024-01-01-my-post %})`
* Link to pages via `link`: `[Docs]({% link _pages/documentation.liquid %})`
* Images per post: `assets/images/my-post/`

### Add a new series

Add to `_config.yml` and `_data/series.yml`.

```yaml
# _config.yml
defaults:
  - scope:
      path: _posts/new-series/
      type: posts
    values:
      permalink: /new-series/:title/
      back: _posts/2024-01-01-new-series-intro.md
```

```yaml
# _data/series.yml
new-series:
  title: A new series
```

Set front matter in the post:

```yaml
---
series: new-series
series_title: A deep dive into stuff
---
```

Render navigation in the post body via `{% include series.liquid %}`.

## License

Content: [CC BY-NC 4.0](https://creativecommons.org/licenses/by-nc/4.0/) — Code: [MIT](LICENSE.md)
