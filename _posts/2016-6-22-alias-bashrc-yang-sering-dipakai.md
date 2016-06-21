---
layout: post
title: Alias di bashrc yang sering (aku) pakai :)
---

Karena seringnya install PC/laptop, maka kadang2 seringkali nambah alias untuk bash. Berikut yang sering jadi alias

```bash
# git alias
alias gs='git status'
alias gb='git branch'
alias gd='git diff'
alias gcm='git commit -m'
alias ga='git add'
alias gl='git log'

# composer alias
alias cda='composer dumpautoload'

# laravel alias
alias art='php artisan'

# service alias
alias serverstart='sudo service nginx start && sudo service php5.6-fpm start && sudo service mysql start'
alias serverstop='sudo service nginx stop && sudo service php5.6-fpm stop && sudo service mysql stop'
alias serverrestart='sudo service nginx restart && sudo service php5.6-fpm restart && sudo service mysql restart'
```