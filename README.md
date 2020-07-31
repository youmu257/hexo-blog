# Setp up hexo-blog
1. Run ```npm install``` download package by package.json
    -  if you want deploy to git repository, run ```npm install hexo-deployer-git --save```
3. Configure _config.yml to setting deploy git repository
4. Deploy the website
    - ```hexo clean & hexo d -g```
5. Go to https://youmu257.github.io/ check the result

# Local check result
1. Start local server
    - ```hexo serve```
2. Go to http://localhost:4000 check the result

# Add category
1. Run ```hexo new page categories_name```
2. Edit source/categories_name/index.php
    - Add ```type: "category"```
3. Edit _posts/your_page.md
    - Add ```categories: "categories_name"```

# Add tag
1. Run ```hexo new page tags_name```
2. Edit source/categories_name/index.php
    - Add ```type: "tags"```
3. Edit _posts/your_page.md
    - Add ```tags: "tags_name"```

# Reference
- [Hexo+GitHub，新手也可以快速建立部落格](https://blackmaple.me/hexo-tutorial/)
- [Hexo搜尋引擎優化](https://hsiangfeng.github.io/hexo/20190514/2072033203/)
