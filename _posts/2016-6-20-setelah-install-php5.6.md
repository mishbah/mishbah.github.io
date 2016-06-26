---
layout: post
title: Nginx setting for php5.6
categories: ["bug fix", solusi]
---

Jika anda mengunakan Nginx untuk menjalankan php maka jika anda menggunakan php versi 5.6 serta PHP-FPM (FastCGI Process Manager), ada hal yang perlu anda rubah pada setingan nginx anda. Jika sebelumnya seperti ini
{% highlight bash %}
fastcgi_pass unix:/var/run/php5-fpm.sock;
{% endhighlight %}

maka akan berubah seperti ini
{% highlight bash %}
fastcgi_pass unix:/var/run/php/php5.6-fpm.sock;
{% endhighlight %}