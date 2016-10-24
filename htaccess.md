# CI need

     RewriteEngine On  #打開改寫引擎
     # RewriteBase /  #這裡要說明說明.htaccess的擺放路徑，/ 代表擺放在apache的根目錄下
     
     RewriteCond $1 !^(index\.php|images|css|js|robots\.txt|favicon\.ico|sitemap.xml)
     RewriteCond %{REQUEST_FILENAME} !-f
     RewriteCond %{REQUEST_FILENAME} !-d
     RewriteRule ^(.*)$ ./index.php?/$1 [L,QSA]

# httpd redirect to https #

     RewriteEngine On
     RewriteCond %{HTTPS} off
     RewriteRule ^(.*)$ https://%{HTTP_HOST}%{REQUEST_URI} [L,R=301]
     

