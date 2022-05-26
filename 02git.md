You can go to commit "m" and make the necessary changes. Then with --amend you can update this commit as "m' " (git hashes always change between commits because they are a calculation that git does).

Then from n (which still points to m) you can rebase m', this way a commit "n' " will be generated out of "m' "

As explained above, the hashes change regardless of whether there are new changes since it is a new commit with different parent.

