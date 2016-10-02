---
title: Hexo Guides
tags:
  - Hexo
  - Blog
date: 2016-10-02 12:37:04
---


# Write New Articles #
We can create a draft by `hexo new draft draftName` and publish it by `hexo publish draftName`.
Also, we can directly create a new post by `hexo new postName`.

# Deploy Our Blog #
1. Install the deploy plugins.
2. Configure the `deploy` section of `_config.yml`
3. Run the following command:
```
hexo clean
hexo deploy
```

# Backup Our Blog #
1. Install the backup plugin.
2. Configure the `backup` section of `_config.yml`
3. Run the following command:
```
hexo clean
hexo backup
```

# Some Useful Plugins #
[hexo-math](https://github.com/akfish/hexo-math) is a tool for writing math formula in the articles.
[hexo-deployer-git](https://github.com/hexojs/hexo-deployer-git) is a tool for deploying our blog into the GitHub.
[hexo-git-backup](https://github.com/coneycode/hexo-git-backup) is a tool for backing up our blog.
