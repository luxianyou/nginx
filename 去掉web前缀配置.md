## 关键词：NGINX 网站前缀 PRIFEX
## 去掉访问页面的前缀 

···
server {
       listen       80;
       server_name  testcenter.jack.net 10.0.4.109;

        #charadd koi8-r;
        proxy_set_header Host $host;
        proxy_set_header X-Real-IP $remote_addr;
        proxy_set_header Fdd-Request-Origin 'external';
        proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;

        #access_log  /data0/logs/nginx/host.access.log  main;

        location / {
            proxy_pass http://127.0.0.1:8080/JackTestCenter/;
            add_header 'Access-Control-Allow-Methods' 'GET,POST,PUT,DELETE,OPTIONS';
            add_header 'Access-Control-Allow-Credentials' 'true';
            add_header 'Access-Control-Allow-Origin' "*";
        }
        location ~/JackTestCenter {
            proxy_pass http://127.0.0.1:8080;
            add_header 'Access-Control-Allow-Methods' 'GET,POST,PUT,DELETE,OPTIONS';
            add_header 'Access-Control-Allow-Credentials' 'true';
            add_header 'Access-Control-Allow-Origin' "*";
        }

}
···
