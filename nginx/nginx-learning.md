# Nginx 学习笔记

思维导图整理 ![](https://github.com/liujiee/notebook/blob/main/nginx/images/nginx-learing1113.png)


### Serving Static Content

Web Server

* /data/www: Container HTML files
* /data/images:  Container images
* Configuration: A server block inside the http block with two location blocks

```
http{
	server{
		location / {
			root /data/www;
		}
		location /images {
			root /data;
		}
	}
}

```

### Setting Up a Simple Proxy Server (前置代理)

```
http{
	server{
		location / {
			root /data/www;
		}
		location /images {
			root /data;
		}
	}

server{
		listen 8080;
		location / {
			proxy_pass http://localhost:80;
		}
	}

}


```
