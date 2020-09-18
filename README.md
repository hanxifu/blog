# How to Generate Pages

```shell
yay -Syu pandoc
npm install hexo-cli -g
npm install
git submodule update --init --recursive
git clone https://github.com/theme-next/hexo-theme-next ./themes/next
hexo clean && hexo g
# hexo s
hexo deploy
```
