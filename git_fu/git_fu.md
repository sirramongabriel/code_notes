#Git notes
----------------------

<blockquote>
    .. A Git Commnando Manifest 
</blockquote>
-------------------------------
command:

    git-update-index - Register file contents in the working tree to the index

options:

    --really-refresh
    Like --refresh, but checks stat information unconditionally, without regard to the "assume unchanged" setting.
    
sources:

[Git documentation](https://git-scm.com/docs/git-update-index)
[SO-Git not tracking changes to subdirectory](https://stackoverflow.com/questions/9034999/why-isnt-git-tracking-changes-in-a-subdirectory)
-------------------------

### Move a dirty workstation to a new branch

<blockquote>
  I just accepted a pull request from master, stepped away only to return and begin working in the master branch..
  Now I have a dirty master branch that is only supposed to be updated by pull request, what to do?
</blockquote>

0. from master branch
1. type 'git stash'
2. checkout another branch, or create a new branch
3. type 'git stash pop'
--------------------------
