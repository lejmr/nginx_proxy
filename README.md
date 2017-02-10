# HTTP proxy based Nginx
yet another HTTP proxy, but with some extra and nifty features included. The reason why you want to use this role is because you are running your own VPS with multiple docker containers each providing HTTP service, and you dont want bother with anything else than just binding docker http port onto DNS and its aliases. 

Hey do you want SSL for your service? Do you have it already issued? Or you want to use Letsencrypt? Yeah, both options are possible. You can just simply use this role. As a bonus your Letsencrypt certificates will refresh on their own (at midnight).

To bind example.com onto your docker container listening on port 8080 with Letsencrypt issued SSL certificates is stupidly easy:


```
      - role: nginx_proxy
        domain: example.com
        http: 8080
        ssl: yes
        alias:
            - www
        domain_alias:
            - example.org
            - www.example.org
```

## More sophisticated usage

Sometimes you are in situation (if you are using lejmr/iredmail container) that your container already provides you with HTTPs, but you want to use different certificate. Easy again:


```
      - role: nginx_proxy
        domain: example.com
        http: 8080
        https: 8081
        ssl: yes
```


And what if one wants to bind container onto a sublocation? That sounds like an already sophisticated problem, but easy again:


```
      - role: nginx_proxy
        domain: example.com
        http: 8080
        ssl: yes
        locations:
            mysql:
                port: 8081
                
```


