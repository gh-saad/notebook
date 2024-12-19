# What is Git
  
  Version control system

# key terms
  
  Repository
  commit
  push
  pull
  contributor
  clone
  stash
  barach
  

## Clone a private repository to cPanel

* Create a password-less ssh-key from

  cPanel > Terminal by entering the following command

```bash
ssh-keygen -t rsa -f ~/.ssh/<repo-name> -b 4096 -C "<cpanel_username>@<hostname>"
ssh-keygen -t ecdsa -f ~/.ssh/<repo-name> -b 256
```

Run only first time

```bash
touch ~/.ssh/config
```

Write in the config

```bash
...
Host github.com-<repo-name>
  Hostname github.com
  IdentityFile=/home/<cpanel_username>/.ssh/<repo-name>
```

Press Esc and :wq enter to save and exit.

```bash
chmod 0600 ~/.ssh/config

chown <cpanel_username>@<hostname> ~/.ssh/config
```

Verify connection with github

```bash
ssh -i ~/.ssh/<repo-name> -T git@github.com
```

Run to clone the repository  

```bash
git clone git@github.com-<repo-name>:<git-username>/<repo-name>.git
```

```bash
cd ~/.ssh/
ssh-keygen -t rsa -b 4096 -C "username@example"
ssh-keygen -t ecdsa -b 256 -m PEM
```

* Now display the generated public-key using the command

```bash
cat ~/.ssh/id_rsa.pub
```

* Copy and paste the displayed public-key into the

  bitbucket.org > Personal Settings > Security > SSH Keys

  Open Cpanel > Terminal move to location

```bash
cd folder_name
```

* Clone Git repo

If your are using Delopyment key

```bash
eval "$(ssh-agent -s)"
ssh-add ~/.ssh/thedxboffplan
```

and then

```bash
git clone git@bitbucket.org:username/project.git
```

Authurized key from Cpanel

Initial commit: set up Node.js project
feat(user-auth): implement user authentication
fix(database): resolve connection issue with MongoDB
docs(readme): update installation instructions
refactor(api): improve error handling in API module
test(unit): add test cases for user service
chore(dependencies): update npm packages