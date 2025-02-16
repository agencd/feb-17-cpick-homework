# Homework Assignment - Due by Friday, February 21

# -----------------------------------------------------------------
# GIT CHERRY-PICK PRACTICE SCENARIO: "La Famiglia Pizzeria"
# -----------------------------------------------------------------
# Story Context:
#   You’re building a website for La Famiglia Pizzeria with three separate
#   sections of the menu (pizza, dessert, drinks) in parallel feature branches.
#   You’ll merge the Pizza and Dessert sections to main, then cherry-pick
#   just one commit (the "coffee" commit) from the Drinks branch into main.
# -----------------------------------------------------------------

# 1) Repository Setup
  - Create a folder named la-famiglia-pizzeria in your terminal under your GitHub parent folder.
  - Initialize Git using git init.
  - Create a README.md file with the content la-famiglia-pizzeria.
  - Create your repository on GitHub with the same folder name.
  - Do not check the “Add a README.md” box, since we're practicing creating the repository locally first and then on GitHub.
  - Identify the repository URL using the SSH method.
  - Return to your terminal and execute git branch -M main to set your base branch to main.
  - Stage README.md and then commit your changes.
  - Execute git remote add origin REPO_URL.
  - Finally, synchronize your local repository with your remote repository by executing git push.
  

# 2) Ensure you’re on the main branch and up to date
  - git checkout main
  - git pull

# --------------------------------------------------------
# CREATE FEATURE 1: PIZZA MENU
# --------------------------------------------------------
# 3) Create and switch to the feature/pizza-menu branch
  - git checkout -b feature/pizza-menu

# 4) Create pizza.md and add some content
  - echo "# Pizza Menu" > pizza.md
  - echo "- Margherita" >> pizza.md
  - echo "- Pepperoni" >> pizza.md
  - echo "- Vegetarian" >> pizza.md

# 5) Commit the changes
  - git add pizza.md
  - git commit -m "Add pizza menu"

# 6) Create a second commit on this branch (Four Cheese)
  - echo "- Four Cheese" >> pizza.md
  - git add pizza.md
  - git commit -m "Add four cheese pizza item"

# 7) Push the pizza branch
  - git push -u origin feature/pizza-menu

# --------------------------------------------------------
# CREATE FEATURE 2: DESSERT MENU
# --------------------------------------------------------
# 8) Switch back to main
  - git checkout main

# 9) Create and switch to the feature/dessert-menu branch
  - git checkout -b feature/dessert-menu

# 10) Create dessert.md and add some content
  - echo "# Dessert Menu" > dessert.md
  - echo "- Tiramisu" >> dessert.md
  - echo "- Gelato" >> dessert.md

# 11) Commit the changes
  - git add dessert.md
  - git commit -m "Add dessert menu"

# 12) Push the dessert branch
  - git push -u origin feature/dessert-menu

# --------------------------------------------------------
# CREATE FEATURE 3: DRINKS MENU
# --------------------------------------------------------
# 13) Switch back to main
  - git checkout main

# 14) Create and switch to the feature/drinks-menu branch
  - git checkout -b feature/drinks-menu

# 15) Create drinks.md and commit
  - echo "# Drinks Menu" > drinks.md
  - echo "- Soda" >> drinks.md
  - echo "- Water" >> drinks.md
  - echo "- Juice" >> drinks.md
  - git add drinks.md
  - git commit -m "Add basic drinks menu"

# 16) Create a second commit (Coffee options, to be cherry-picked later)
  - echo "- Coffee (Espresso, Cappuccino, Latte)" >> drinks.md
  - git add drinks.md
  - git commit -m "Add coffee options"

# 17) Create a third commit (Placeholder for beers)
  - echo "- Beer (Coming soon...)" >> drinks.md
  - git add drinks.md
  - git commit -m "Add placeholder for beers"

# 18) Push the drinks branch
  - git push -u origin feature/drinks-menu

# --------------------------------------------------------
# MERGE PIZZA & DESSERT INTO MAIN
# --------------------------------------------------------
# 19) Merge Pizza branch into main
  - git checkout main
  - git merge feature/pizza-menu
  - git push
### If there are conflicts, resolve them, then:
### git add .
### git commit (if needed after conflicts resolved)
### In this step we are merging our feature branches to main using the git cli

# 20) Merge Dessert branch into main
  - git merge feature/dessert-menu
  - git push
### Again, resolve conflicts if any appear

# --------------------------------------------------------
# CHERRY-PICK COFFEE COMMIT FROM DRINKS
# --------------------------------------------------------
# 21) Identify the commit hash for "Add coffee options"
  - git checkout feature/drinks-menu
  - git log --oneline
# Copy the commit hash corresponding to "Add coffee options" (call it <coffee-hash>)

# 22) Go back to main
  - git checkout main

# 23) Cherry-pick just that one commit
  - git cherry-pick <coffee-hash>
### If there are conflicts, resolve them, then:
### git add .
### git cherry-pick --continue

# 24) Confirm the coffee commit is now in main
  - git log --oneline

# 25) Push final changes to main
  - git push

# -----------------------------------------------------------------
# END OF SCENARIO
# -----------------------------------------------------------------
# At this point:
#   - main has pizza.md, dessert.md, and only the coffee lines from drinks.md.
#   - The rest of the drinks are still on the feature/drinks-menu branch.
#   - You've successfully practiced merging and cherry-picking!
#   - Please submit your repository url to me directly from teams message.
# -----------------------------------------------------------------
