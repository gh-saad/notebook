# Git

## Clone a private repository to cPanel

* Create a password-less ssh-key from

  cPanel > Terminal by entering the following command

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