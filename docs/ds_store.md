<h1 align="center">.DS_Store Files</h1>

<br>

### Automated Exploitation

- ds-spider - [Repository](https://github.com/olivercalazans/ds-spider)

```bash
pip install ds-store requests
python3 ds-spider.py https://example.com/.DS_Store
```

- ds_store_exp - [Repository](https://github.com/lijiejie/ds_store_exp)

```bash
pip install ds-store requests
python3 ds_store_exp.py http://target.com/.DS_Store
```


<br>
<br>


### Manual

- Check for the presence of a `.DS_Store` file:

```bash
curl -I https://example.com/.DS_Store
```

- If the response is `200 OK`, the file exists. Download it:

```bash
curl -s https://example.com/.DS_Store --output sample.DS_Store

# View the raw binary (readable strings are often interleaved with non-printable bytes)
strings sample.DS_Store
```

- Even without a parser, it is possible to search for printable strings (filenames) using:

```bash
cat sample.DS_Store | strings | grep -E '\.(php|html|js|css|zip|sql|txt|env|yml|json)$'
```
