mkdir vcs-task
cd vcs-task
git init

echo "echo Hello" > script1.sh
echo "echo Script 2" > script2.sh
echo "echo Script 3" > script3.sh
chmod +x script*.sh

git remote add origin https://github.com/<username>/vcs-task.git
git branch -M main
git push -u origin main

git checkout -b feature-branch
# edit script1.sh
git add .
git commit -m "Feature update"
git checkout main
git merge feature-branch

git checkout -b rebase-branch
# edit script2.sh
git add .
git commit -m "Rebase change"
git checkout main
# edit script2.sh
git add .
git commit -m "Main change"
git checkout rebase-branch
git rebase main

# make temp edits
git stash
git stash apply

