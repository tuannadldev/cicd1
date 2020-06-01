# cicd1 step by step
1. Register SSL key from https://www.sslforfree.com/
2. Configs ssl for domain 
server {
    listen 80;
    listen 443 ssl;
    server_name jenkins.localhost.com;
    ssl_certificate /etc/nginx/ssl/jenkins/certificate.crt;
    ssl_certificate_key /etc/nginx/ssl/jenkins/private.key;
    ssl_protocols TLSv1 TLSv1.1 TLSv1.2;
    ssl_prefer_server_ciphers on;
    ssl_ciphers 'EECDH+AESGCM:EDH+AESGCM:AES256+EECDH:AES256+EDH';

    location / {
      proxy_pass          http://127.0.0.1:8080;
      proxy_read_timeout  90;
      # Required for new HTTP-based CLI
      proxy_http_version 1.1;
      proxy_request_buffering off;
      add_header 'X-SSH-Endpoint' 'jenkins.thetechdl.net:50022' always;
    }
}
3 . Intasll Jenkin form package stable
4. Install plugin custom
5. Add Itemm for begin
