<h1 align="center">WordPress</h1>

<br>

<h2 align="center">Version Core</h2>

### WPScan (No flag required)

```bash
wpscan --url https://example.com
```

<br>

### Agressive scanning

- Sniffing web page

```bash
curl -s https://example.com | grep -E '(generator" content="[0-9.]+")|(wp_blog_version = "[0-9.]+")|(ver=[0-9.]+)'
```

- `wp-admin/load-styles.php` – The Etag header frequently contains the core version.

```bash
curl -I https://example.com/wp-admin/load-scripts.php
```

- `wp-admin/load-scripts.php` – Follows the same logic as the styles file.

```bash
curl -I https://example.com/wp-admin/load-scripts.php
```

- `wp-links-opml.php` – This file may contain version information in its content.

```bash
curl https://example.com/wp-links-opml.php
```

- `sitemap.xml` – The sitemap generator can reveal the WordPress version.

```bash
curl https://example.com/wp-sitemap.xml
```

- `readme.html` – When this file is present, it clearly exposes the version.

```bash
curl https://example.com/readme.html
```


<br>
<br>


<h2 align="center">User enumeration</h2>

### WPScan 
 - flag: `-e u` or `--enumerate u`

```bash
wpscan -e u --url https://example.com
```

<br>

### Manual Scanning

- REST API Analysis

```bash
http://example.com/wp-json/wp/v2/users
```

- Author Enumeration (author URL)

```bash
http://example.com/?author=1
```

- Enumeration via WP-Login

```bash
http://example.com/wp-login.php

# NON-EXISTENT USER
ERROR: Invalid username.

# WRONG PASSWORD
ERROR: The password you entered for the username username is incorrect.
```

- XML Sitemaps

```bash
http://example.com/wp-sitemap-users-1.xml

OR

http://example.com/author-sitemap.xml

```

- RSS Feeds

```bash
http://example.com/feed/

OR

http://example.com/comments/feed/
```


<br>
<br>


<h2 align="center">Themes and Plugins</h2>

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


<h2 align="center">WP-Cron Detection</h2>

- WPScan (No flag required)

```bash
wpscan --url https://example.com
```

### Manual

```bash
curl -sI http://example.com/wp-cron.php?doing_wp_cron=1
```
