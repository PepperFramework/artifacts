# How to git credentials on ubuntu

## 1. Create an ssh key

```
ssh-keygen -t ed25519 -C "[EMAIL ADDRESS]"
```

Enter a passphrase.

Then:

```
eval $(ssh-agent -s)
ssh-add ~/.ssh/[NEW KEY (file name above)]
```

Copy the content from the .pub file:

```
nano ~/.ssh/[NEW KEY (file name above)].pub
```

## 2. Add the key to GitHub

https://github.com/settings/keys

Press "New SSH key", add a name and copy the content into the input field.

## 3. Config git

```
git config --global credential.helper cache
```

## 4. Clone a repository

Use the ssh url while cloning a new repository! (Not the default https)

## 5. Convert old repositories:

```
git remote set-url origin [SSH Link]
```

