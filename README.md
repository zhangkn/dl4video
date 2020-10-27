# Backup branch for unmerged pull requests

I noticed that most archives of youtube-dl do NOT contain the unmerged pull requests. This is a problem beacuse the youtube-dl project was way behind on acceping pull requests, and there is some signifcant stuff that was never merged.

Github creats branches for each unmerged pull request, but they are not fetched by default.[1]

So i created a "sidecar" branch, where each commit is merged with each unmerged pull request, in order of pull request number.

The reason that I put all of the pull requests into a single branch is beacuse it is much easier to manage this way. Otherwise, you would have over 4000 branches.
With a single branch, you can "unpack" every one of the pull request branches, without cloggig up your branch namespace. And if you don't want to include it, simply deleting it will purge everything.

If you want the original branches, it is probably simplest to pull from a repo that I set up that has the original branches. The downside to doing this is that it can make management more complicatd. There's no way that I know of to "remap" them back to the repo interface, and they may cause conflicts of some kind.

Originally obtained from:
https://git.osuv.de/star/youtube-dl.git

```
  git clone https://github.com/unqueued/youtube-dl-prs
  cd youtube-dl-prs
  git fetch origin  '+refs/pull/*/head:refs/remotes/origin/pr/*'
  git push --all my-repo
```


[1]: https://stackoverflow.com/questions/27567846/how-can-i-check-out-a-github-pull-request-with-git
