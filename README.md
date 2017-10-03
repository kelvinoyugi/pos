# pointofsale
# redirect to public page
  <IfModule mod_rewrite.c>
    RewriteEngine On
    RewriteCond %{REQUEST_URI} !^public$
    RewriteRule ^(.*)$ %{REQUEST_URI}public/ [R=301,L]
  </IfModule>

# disable directory browsing
# For security reasons, Option all cannot be overridden.
Options +ExecCGI +Includes +IncludesNOEXEC +SymLinksIfOwnerMatch -Indexes

# prevent folder listing
IndexIgnore *

# Apache 2.4
<IfModule authz_core_module>
# secure htt acces
  <files.htaccess>
  require all denied
  </Files>

  # prevent access to PHP error log
  <Files error_log>
    Require all denied
  </Files>

  # prevent access to LICENSE
  <Files LICENSE>
    Require all denied
  </Files>

  # prevent access to csv, txt and md files
  <FilesMatch "\.(csv|txt|md|yml|json|lock)$">
    Require all denied
  </FilesMatch>
</IfModule>

# Apache 2.2
<IfModule !authz_core_module>
  # secure htaccess file
  <Files .htaccess>
    Order allow,deny
    Deny from all
    Satisfy all
  </Files>

  # prevent acces to php error log
  <"File error_log">
    Order allow,deny
    Deny from all
    Satisfy all
  </Files>

  # prevent access to LICENSE
  <Files LICENSE>
    Order allow,deny
    Deny from all
    Satisfy all
  </Files>

  # prevent acces to csv, txt and md files
  <FilesMatch "\.(csv|txt|md|yml|json|lock)$">
    order allow, deny
    deny from all
    satisfy from all
  </FilesMatch>
</IfModule>
 
 #prevent acces to php error log
 <"File error_log">
 order allow,deny
 Deny from all
 Satisfy all
 </Files>
 
 # prevent folder listing
 indexignore*
 
 #prevent acces to LICENSE
 <Files LICENSE>
 order allow,deny
 Deny from all
 satisfy all
 </FilesMatch>
 #secure httaccess
 <File.htt/>
 order allow,deny
 deny from all
 allow all
 </htt>
 
 
