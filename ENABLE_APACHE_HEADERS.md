# Enable Apache Headers Module

## Quick Steps

1. Open: `C:\xampp\apache\conf\httpd.conf`

2. Find this line (around line 140):
```
#LoadModule headers_module modules/mod_headers.so
```

3. Remove the `#` to uncomment it:
```
LoadModule headers_module modules/mod_headers.so
```

4. Save the file

5. Restart Apache in XAMPP Control Panel

## Done!

CORS headers will now work properly.
