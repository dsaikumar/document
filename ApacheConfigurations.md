# Apache Web server configurations

## Enable the proxy module in Apache

**For setting the proxy need to uncomment these in the file for enabling the proxy setup**

    LoadModule proxy_module modules/mod_proxy.so
    
    LoadModule proxy_module modules/mod_proxy_http.so
    
    LoadModule proxy_module modules/mod_proxy_ajp.so
    
Save and restart the apache server



## Configuration of Proxy in Apache

Add these lines to httpd/conf/httpd.conf  file

    ProxyPreserveHost on

    ProxyPass /url1 http://alias.host.com/url
    
    ProxyPassReverse /url http://alias.host.com/url
    

## Configuration for multiple ports running of apache and binding to different server ip or different port of same ip

    Listen localhost:4444
    <VirtualHost *:4444>
        DocumentRoot C:/apps/ApacheSoftwareFoundation/Apache2.2/htdocs/4444
        ServerName localhost
        ProxyPreserveHost On
        
        ProxyPass /cab http://localhost:8080/cab
        ProxyPassReverse /cab http://localhost:8080/cab
        
        ProxyPass /manage http://localhost:8080/manage
        ProxyPassReverse /manage http://localhost:8080/manage
        
        ProxyPass /core http://localhost:5555/core
        ProxyPassReverse /dsnap-core http://localhost:5555/core
        
        ErrorLog logs/localhost-error4444.log
    </VirtualHost>
    
    Listen localhost:5555
    <VirtualHost *:5555>
        DocumentRoot C:/apps/ApacheSoftwareFoundation/Apache2.2/htdocs/5555
        ServerName localhost
        ProxyPreserveHost On   
        
        ProxyPass /core http://localhost:8080/core
        ProxyPassReverse /core http://localhost:8080/core    
    
        ErrorLog logs/localhost-error5555.log
    </VirtualHost>

## To include other configurations

> Include "/path/hosts.conf"