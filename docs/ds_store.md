<h1 align="center">.DS_Store Files</h1>

<br>

### Check for the presence of a `.DS_Store` file:

```bash
curl -I https://example.com/.DS_Store
```

<br>

### If the response is `200 OK`, the file exists. Download it:

```bash
curl -s https://example.com/.DS_Store --output sample.DS_Store

# View the raw binary (readable strings are often interleaved with non-printable bytes)
strings sample.DS_Store
```

<br>

### It is possible to search for printable strings (filenames) using:

```bash
cat sample.DS_Store | strings | grep -E '\.(php|html|js|css|zip|sql|txt|env|yml|json)$'
```
