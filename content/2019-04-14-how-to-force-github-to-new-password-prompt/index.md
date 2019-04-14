---
title: 403 Forbidden error message when you try to push to a GitHub repository using HTTPS
date: 2019-04-14
tags: [git]
path: blog/build-a-blog-under-5-min
cover: ./preview.png
excerpt: I created a new github account and wanted to push my first project to it. This article shows you how to enforce a new password prompt when getting a 403 error during git push.
---

The problem was I already had another github account that I normally pushed to. So when I wanted to push
to my new github account I got following error.

```none
error: The requested URL returned error: 403 Forbidden while accessing https://github.com/github-username/github-repository-name.git/info/refs
```

To fix it I had to find a way to enforce a new password prompt.

First I checked which url was configured:

```none
git config -l | grep url
```

which gave me following output:

```none
remote.origin.url=https://github.com/github-username/github-repository-name.git
```

to enforce now a new password prompt I had to change the `github.com` to `github-username@github.com`:

```none
git remote set-url origin "https://github-username@github.com/github-username/github-repository-name.git"
```

When I tried to push again I was able to type in a password and push to the new github repo.
