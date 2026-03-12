
## Option B: Prefer Rebase (cleaner history)

```bash
git config pull.rebase true
git add .
git commit -m "My local changes"
git pull --rebase origin main
# Resolve conflicts if needed, then continue rebase with `git rebase --continue`
git push origin main
```

---
## ⁉️ Error
````bash
error: cannot pull with rebase: You have unstaged changes.
Please commit or stash them.
````

This happens because `git pull --rebase` requires a clean working directory—i.e. no changes that haven’t been staged or committed. Git refuses to rebase with unstaged local edits to prevent accidental data loss.

#### ️⚡Option 1: Stash, pull + rebase, then apply stash (recommended if work isn’t ready to commit)

Use this if your `edits are work-in-progress` or you want to combine them with the remote updates:
````bash 
# Save your local changes (unstaged/staged)
git stash push -m "WIP before pull"

# Sync with remote and rebase cleanly
git pull --rebase           # or `git fetch` then `git rebase origin/main`

# Reapply your changes on top
git stash pop
````
- `git stash` temporarily stores your local changes.
- `git pull --rebase` fast-forwards and rebases your branch cleanly.
- `git stash pop` brings back your edits (merge conflicts may come up, resolve them manually).
#### 💥 Option 2 – **Reset your local branch to exactly match the remote, discarding all local edits (dangerous!)**

Use this if you want your local files to mirror GitHub’s state—with no local modifications:
````bash 
git fetch origin
git reset --hard origin/main
git clean -fd             # (optional) removes untracked files/directories
````

- `git fetch` updates your remote-tracking branch.
- `git reset --hard origin/main` forces your local `main` branch to match the commit snapshot of `origin/main`, discarding all local changes.
-  `git clean -fd` removes any files or directories not tracked by Git. Use with **extreme caution**—you cannot undo it. **`💥IMPOSSIBLE TO REVERT BACK`**


---

## Ublock Filters 

```lua 
! 2023-12-10 https://www.pinterest.com
www.pinterest.com##.m1e.INd.XiG.sLG.Pj7 > .Hsu.iyn.zI7.XiG.INd > .m1e.INd.XiG.sLG.Pj7 > .Hsu.iyn.zI7.XiG > .MIw.L4E.kVc.hCL
www.pinterest.com##.dB7.C9i.un8.jzS
www.pinterest.com##.Hsu.iyn.zI7.mQ8.Eqh > .Hsu.iyn.zI7
www.pinterest.com##div.Hb7.MIw.Yl-:nth-of-type(14)

! 2024-01-26 https://www.youtube.com
||www.gstatic.com/youtube/img/promos/growth/5d26e51605d7a9f11baa1ab11814f28790758a5ef945c5222e1f4a8bdf3527ba_244x112.webp$image

! 2024-01-31 https://www.maxicours.com
www.maxicours.com##.text-center.img-wrapper

! 2024-02-05 https://www.youtube.com
||www.gstatic.com/youtube/img/promos/growth/e943637a4e2bbf813c331b9c089473570b1098fa6321e5d37166ef74a3581ac5_244x112.webp$image

! 2024-03-05 https://en.m.wikibooks.org
en.m.wikibooks.org##[href="https://commons.wikimedia.org/wiki/Special:MyLanguage/Commons:Wiki_Loves_Folklore_2024"]
||upload.wikimedia.org/wikipedia/commons/0/08/WLA24_Rolling_Banner.png$image

! May 24, 2024 https://www.coursera.org
||d3njjcbhbojbot.cloudfront.net/api/utilities/v1/imageproxy/https://images.ctfassets.net/wp1lcwdav1p1/14maDlt0Gf9QGrtfwdjUSM/a671b5ceb9c950f5ee6e3710509feba1/iStock-1134444079.jpg?w=1500&h=680&q=60&fit=fill&f=faces&fm=jpg&fl=progressive&auto=format%2Ccompress&dpr=*&w=1000$image
```
