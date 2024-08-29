# JForum: Get off of S****forge, finally!

JForum people, come get your project (https://github.com/JForum).

I've done the "hard part" and exported to github:

https://git-scm.com/book/en/v2/Git-and-Other-Systems-Git-as-a-Client

```bash
svn checkout https://svn.code.sf.net/p/jforum2/code/trunk jforum2-code
( \
  cd jforum-code; \
  svn log -q | awk -F '|' '/^r/ {gsub(/ /, "", $2); sub(" $", "", $2); print $2" = "$2" <"$2">"}' | sort -u > users.txt; \
  cp users.txt ..; \
)
vim users.txt # touch up
cat > users.txt <<EOF
andowson = andowson@gmail.com <andowson@gmail.com>
Andowson = andowson@gmail.com <andowson@gmail.com>
andowson@gmail.com = andowson@gmail.com <andowson@gmail.com>
heribender@gmail.com = heribender@gmail.com <heribender@gmail.com>
lohmaier@gmail.com = lohmaier@gmail.com <lohmaier@gmail.com>
(noauthor) = (noauthor) <(noauthor)>
peter.risko76@gmail.com = peter.risko76@gmail.com <peter.risko76@gmail.com>
rvanderwerf = rvanderwerf <rvanderwerf>
udittmer = ulf.dittmer@googlemail.com <ulf.dittmer@googlemail.com>
ulf.dittmer@googlemail.com = ulf.dittmer@googlemail.com <ulf.dittmer@googlemail.com>
EOF
git svn clone svn://svn.code.sf.net/p/jforum2/code git-version4 --authors-file=users.txt -T trunk -b branches -t tags
gh repo create JForum-get-off-sourceforge-finally/jforum --public --source git-version4 --push
```

Now you guys don't have an excuse to live like this (`svn`, etc...).
