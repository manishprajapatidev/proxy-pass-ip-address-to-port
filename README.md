# Use Apache as a proxy server to access internal IPs from an external machine

# Install apache2. On Ubuntu
```
sudo apt-get install apache2
```
# Enable the various modules needed. You can do that with the a2enmod tool:
```
sudo a2enmod proxy
sudo a2enmod proxy_http
sudo a2enmod proxy_ajp
sudo a2enmod rewrite
sudo a2enmod deflate
sudo a2enmod headers
sudo a2enmod proxy_balancer
sudo a2enmod proxy_connect
sudo a2enmod proxy_html
```

# Configure Apache by editing the /etc/apache2/sites-available/000-default.conf file to read:
```
sudo nano /etc/apache2/sites-available/000-default.conf
```

```
<VirtualHost *:*>
    ProxyPreserveHost On
    
    # Servers to proxy the connection, or;
    # List of application servers:
    # Usage:
    # ProxyPass / http://[IP Addr.]:[port]/
    # ProxyPassReverse / http://[IP Addr.]:[port]/

    # Example: 
    ProxyPass / http://localhost:3000/
    ProxyPassReverse / http://localhost:3000/
    ServerName localhost
</VirtualHost>
```
 
 # Restart the apache2 service
 ```
 sudo service apache2 restart
 ```
### Plugins

Dillinger is currently extended with the following plugins. Instructions on how to use them in your own application are linked below.

| Plugin | README |
| ------ | ------ |
| Dropbox | [plugins/dropbox/README.md][PlDb] |
| GitHub | [plugins/github/README.md][PlGh] |
| Google Drive | [plugins/googledrive/README.md][PlGd] |
| OneDrive | [plugins/onedrive/README.md][PlOd] |
| Medium | [plugins/medium/README.md][PlMe] |
| Google Analytics | [plugins/googleanalytics/README.md][PlGa] |
