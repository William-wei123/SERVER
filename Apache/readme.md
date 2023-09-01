## 反向代理fastapi 接口
000-default.conf
```

    <VirtualHost *:80>
            ServerName 163
            ServerAlias 163.
            ServerAdmin webmaster@example.com
            DocumentRoot /var/www/example.com/public_html
        
            <Directory /var/www/example.com/public_html>
                Options -Indexes +FollowSymLinks
                AllowOverride All
            </Directory>
            <Proxy *>
                AuthType none
                AuthBasicAuthoritative Off
                SetEnv proxy-chain-auth On
                Order allow,deny
                Allow from all
            </Proxy>
            ProxyRequests On #off表示开启反向代理  on表示开启正向代理
            ProxyPass /t http://localhost:8070
            ProxyPassReverse /t http://localhost:8070
            ProxyPass /openapi.json http://localhost:8070/openapi.json
            ProxyPassReverse /openapi.json http://localhost:8070/openapi.json
        
            ErrorLog ${APACHE_LOG_DIR}/example.com-error.log
            CustomLog ${APACHE_LOG_DIR}/example.com-access.log combined
        </VirtualHost>
        
        # vim: syntax=apache ts=4 sw=4 sts=4 sr noet

```
