<h1 align="center">WordPress</h1>

<br>

### Version Core with 
- WPScan (No flag required)

```bash
wpscan --url https://example.com
```

- Manual scanning
  - Passive scanning
    - **Meta Generator**: In the `<meta name="generator" content="WordPress 6.x.x">` tag.
    - **JavaScript Variables**: In scripts that expose the version, such as `wp_blog_version = "6.x.x";`.
    - **HTML Comments**: In comments that accidentally include the version.
    - **Query Parameters**: In URLs of files (like CSS and JS) that include `?ver=6.x.x`.

- Agressive scanning

1. `wp-admin/load-styles.php` – The Etag header frequently contains the core version.

```bash
curl -I https://example.com/wp-admin/load-scripts.php
```

2. `wp-admin/load-scripts.php` – Follows the same logic as the styles file.

```bash
curl -I https://example.com/wp-admin/load-scripts.php
```

3. `wp-links-opml.php` – This file may contain version information in its content.

```bash
curl https://example.com/wp-links-opml.php
```

4. `sitemap.xml` – The sitemap generator can reveal the WordPress version.

```bash
curl https://example.com/wp-sitemap.xml
```

5. `readme.html` – When this file is present, it clearly exposes the version.

```bash
curl https://example.com/readme.html
```


<br>
<br>


### User enumeration

- WPScan (flag `-e u` or `--enumerate u`)

```bash
wpscan -e u --url https://example.com
```

- Manual Scanning

1. REST API Analysis

```bash
http://example.com/wp-json/wp/v2/users
```

2. Author Enumeration (author URL)

```bash
http://example.com/?author=1
```

3. Enumeration via WP-Login

```bash
http://example.com/wp-login.php

# NON-EXISTENT USER
ERROR: Invalid username.

# WRONG PASSWORD
ERROR: The password you entered for the username username is incorrect.
```

4. XML Sitemaps

```bash
http://example.com/wp-sitemap-users-1.xml

OR

http://example.com/author-sitemap.xml

```

5. RSS Feeds

```bash
http://example.com/feed/

OR

http://example.com/comments/feed/
```


<br>
<br>


### Themes and Plugins

- WPScan
  - flag `vp`: Vulnerable Plugins
  - flag `p`: All Plugins
  - flag `vt`: Vulnerable Themes
  - flag `t`: All Themes

```bash
wpscan --url https://example.com --enumerate vp, vt
```

- Manual

```bash
curl -s https://example.com | grep -Eo "wp-content/(themes|plugins)/[^\"']+"
```


<br>
<br>


### WP-Cron Detection

- WPScan (No flag required)

```bash
wpscan --url https://example.com
```

### Manual

```bash
curl -sI http://example.com/wp-cron.php?doing_wp_cron=1
```
