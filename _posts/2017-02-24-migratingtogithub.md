---
layout: post
title: Migrating to GitHub pages
---

This blog was initially hosted on a raspberry pi running Arch Linux. I was planning to run it on a virtual server as I am not allowed to host a website over a private IP address (Vodafone you s***). Github pages is a great option for me. They use jekyll too so I can migrate without any hassle! I deleted the record for `blog.xvzf.tech` and replaced it by a CNAME record pointing to `xvzf.github.io `. Next, I had to modify the GitHub pages settings to enable my custom domain.

![GitHub Pages Settings](http://blog.xvzf.tech/public/images/github_pages_settings.png "GitHub Pages Settings")

Unfortunately GitHub pages won’t provide a valid certificate. The common name (CN) field of the certificate contains the FQDN (full qualified domain name) of the GitHub pages provider server. In order to be a valid certificate, the CN has to be set to blog.xvzf.tech. Maybe they fix that in some time!

{% highlight BASH %}
Nmap scan report for blog.xvzf.tech (151.101.64.133)
Host is up (0.028s latency).
Other addresses for blog.xvzf.tech (not scanned): 151.101.128.133 151.101.192.133 151.101.0.133
Not shown: 998 filtered ports
PORT    STATE SERVICE        VERSION
80/tcp  open  http-proxy     Varnish
|_http-server-header: GitHub.com
|_http-title:           xvzf &middot; prepend tar      
443/tcp open  ssl/http-proxy Varnish
|_http-title:           xvzf &middot; prepend tar      
| ssl-cert: Subject: commonName=www.github.com/organizationName=Fastly, Inc./stateOrProvinceName=California/countryName=US
| Subject Alternative Name: DNS:www.github.com, DNS:*.github.com, DNS:github.com, DNS:*.github.io, DNS:github.io, DNS:*.githubusercontent.com, DNS:githubusercontent.com
| Not valid before: 2016-01-20T00:00:00
|_Not valid after:  2017-04-06T12:00:00
|_ssl-date: TLS randomness does not represent time
{% endhighlight %}


  Everything seems to be working now! Free hosting! I am fine with that.
