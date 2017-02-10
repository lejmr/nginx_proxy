# HTTP proxy based Nginx
with some extra and nifty features included.


```
      - role: nginx_proxy
        domain: example.com
        http: 8084
        alias:
            - www
        domain_alias:
            - example.org
            - www.example.org
```
