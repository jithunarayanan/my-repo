##git commands
Quick setup —
Get started by creating a new file or uploading an existing file. I recommend every repository include a README, LICENSE, and .gitignore.
##Add user in our machine
```
git config --global user.name "username"
git config --global user.email "user_email"
```
##Create a new repository on the command line
```
echo "# man" >> README.md
git init
git add README.md
git commit -m "first commit"
git branch -M main
git remote add origin <repo_link>
git push -u origin main
```
##push an existing repository from the command line
```
git remote add origin <repo_link>
git branch -M main
git push -u origin main
```
