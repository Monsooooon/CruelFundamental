### git中merge和rebase区别

------

1. rebase把当前的commit放到公共分支的最后面，merge把当前的commit和公共分支合并在一起；
2. 用merge命令解决完冲突后会产生一个commit，而用rebase命令解决完冲突后不会产生额外的commit。

emergence ref:yswdra.md