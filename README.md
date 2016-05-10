![Apache Logo](https://static.frapsoft.com/markdown/github/apache.gif)

# Apache htdigest authentication

## Module `mod_auth_digest`

Quick Introduction how to use the more secure [htdigest](http://httpd.apache.org/docs/current/mod/mod_auth_digest.html) authentication for the Apache webserver.  

### 1.) create a [.htaccess](https://httpd.apache.org/docs/2.4/howto/htaccess.html) to protect your data  

***best practice: only serve authentification data over a encrypted connection!***  

```
<Location "/var/www/website/wp-admin/">
    AuthType Digest
   	AuthName "protected"
    AuthDigestDomain "/wp-admin/" "http://myblog.loc/wp-admin/"
    AuthDigestProvider file
    AuthUserFile "/var/secure/.htpasswd"
    Require valid-user
</Location>
```


2.) create a `.htpasswd` file

`htdigest -c .htpasswd realm username` **important notice** realm must be the same string like in your "AuthName" setting above.

***best practice: save the .htpasswd files outside of the public accessible webfolder.***  


[![frapsoft on twitter](https://static.frapsoft.com/markdown/github/twitter.png)](https://twitter.com/frapsoft)

## License

Copyright (c) 2016 Maik Ellerbrock  
MIT: <https://opensource.org/licenses/mit-license.php>