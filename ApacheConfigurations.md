# Configuration of Proxy in Apache

Add these lines to httpd/conf/httpd.conf  file

    ProxyPreserveHost on

    ProxyPass /url1 http://alias.host.com/url
    
    ProxyPassReverse /url http://alias.host.com/url
    

- - -
# Enable the proxy module in Apache

**For setting the proxy need to uncomment these in the file for enabling the proxy setup**

    LoadModule proxy_module modules/mod_proxy.so
    
    LoadModule proxy_module modules/mod_proxy_http.so
    
    LoadModule proxy_module modules/mod_proxy_ajp.so
    


Save and restart the apache server