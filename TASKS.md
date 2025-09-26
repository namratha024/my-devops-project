1️⃣ Initialize Local Repository and Link to GitHub
# Navigate to project folder (or create one)
cd ~
mkdir my-devops-project
cd my-devops-project

# Initialize Git
git init

# Add GitHub remote (replace <username>)
git remote add origin https://github.com/<username>/my-devops-project.git

# Create initial files
echo "# My DevOps Project" > README.md
echo "app.py" > app.py
echo "node_modules/" > .gitignore

# Stage and commit
git add .
git commit -m "Initial commit: Add README, app.py, .gitignore"

# Push to GitHub main
git branch -M main
git push -u origin main

2️⃣ Create Dev and Feature Branches
# Create dev branch
git checkout -b dev
git push -u origin dev

# Create a feature branch from dev
git checkout -b feature/add-logging
git push -u origin feature/add-logging

3️⃣ Make Changes in Feature Branch
# Edit app.py locally or directly on GitHub
nano app.py
# Example content:
print('Hello DevOps')
print("Logging feature: Started application")
print("Logging feature: Additional debug info")

# Stage and commit
git add app.py
git commit -m "Add logging print statements in app.py"

# Push feature branch
git push origin feature/add-logging

4️⃣ Create Pull Request (Feature → Dev)

Go to GitHub → Pull Requests → New Pull Request

Base: dev

Compare: feature/add-logging

Title: Add logging feature

Description: Added print statements in app.py to simulate logging functionality.

Click Create Pull Request → Merge Pull Request → Confirm Merge

5️⃣ Delete Feature Branch
# Locally
git checkout dev
git branch -d feature/add-logging

# On GitHub (click Delete branch after merge)
# Or via terminal
git push origin --delete feature/add-logging

6️⃣ Merge Dev → Main
# Switch to main
git checkout main

# Pull latest changes from GitHub
git pull origin main

# Merge dev into main
git merge dev

# Push main branch
git push origin main


⚠️ If conflicts appear, resolve them:

# Open file with conflict
nano app.py
# Remove conflict markers <<<<<<<, =======, >>>>>>>
# Save and exit

# Stage and commit
git add app.py
git commit -m "Resolve merge conflict in app.py"
git push origin dev  # or main depending on branch

7️⃣ Tag a Release (Optional)
git checkout main
git tag v1.0
git push origin v1.0

8️⃣ Keep Branches Updated
git checkout dev
git pull origin dev

git checkout main
git pull origin main


Always create new feature branches from dev for future tasks.
