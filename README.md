# Setup hexo-blog
1. Run ```npm install``` download package by package.json
    -  if you want deploy to git repository, run ```npm install hexo-deployer-git --save```
2. Configure _config.yml to setting deploy git repository
3. Deploy the website
    ```
    npm run clean
    npm run deploy
    ```
4. Go to https://youmu257.github.io/ check the result

# Local check result
1. Start local server
    - ```npm run server```
2. Go to http://localhost:4000 check the result

# Add new post
1. Create new post in source/_posts/your_post.md

# Add article
1. Run ```npx hexo new post "your_article_name"```
2. Edit source/_posts/your_article_name.md

# Add category
1. Run ```npx hexo new page categories_name```
2. Edit source/categories_name/index.md
    - Add ```type: "category"```
3. Edit source/_posts/your_post.md
    - Add ```categories: "categories_name"```

# Add tag
1. Run ```npx hexo new page tags_name```
2. Edit source/categories_name/index.md
    - Add ```type: "tags"```
3. Edit source/_posts/your_post.md
    - Add ```tags: "tags_name"```

# Reference
- [【學習筆記】如何使用 Hexo + GitHub Pages 架設個人網誌](https://hackmd.io/@Heidi-Liu/note-hexo-github)
- [Hexo搜尋引擎優化](https://hsiangfeng.github.io/hexo/20190514/2072033203/)
