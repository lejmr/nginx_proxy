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


