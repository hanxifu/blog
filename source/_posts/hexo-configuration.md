---
title: hexo-configuration
date: 2020-08-06 20:07:11
tags: [hexo]
---

# Hexo Mathjax 配置

1. `yay pandoc`
2. `npm install hexo-renderer-pandoc --save`
3. `npm install hexo-math --save`
4. go to `node_modules/hexo-renderer-pandoc/index.js:58` (maybe changed one day). Change to `  var args = [ '-f', 'markdown-smart'+extensions, '-t', 'html-smart', math, '--standalone']`
5. here's the related configurations in `_config.yml`:

    ```yaml
    math:
        engine: 'mathjax'
        mathjax:
            src: https://cdnjs.cloudflare.com/ajax/libs/mathjax/2.7.1/MathJax.js
            config:
            enable: true
            per_page: true

    markdown:
        plugins:
            - markdown-it-footnote
            - markdown-it-sup
            - markdown-it-sub
            - markdown-it-abbr
            - markdown-it-emoji
            - hexo-math
    ```

Now it's ready!

Run `hexo c && hexo g && hexo server` to see your pages!