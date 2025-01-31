# Step 1: Set Up the Project

## Create a New Directory for Your Project
Run the following commands in your terminal:

```bash
mkdir ci-cd-task
cd ci-cd-task
```

## Create the Folder Structure
Organize your project by creating the necessary folders:

```bash
mkdir -p .github/workflows src test
```
![my image](https://github.com/jayymeg/project-3/blob/07bfae7ad74ef5fbf9f5bffd7b4f21ba61603832/Task-3/Task-3%20images/P%201.png)


## Create the Files
Create the following files with the specified paths:

- `src/app.js`
![my image](https://github.com/jayymeg/project-3/blob/07bfae7ad74ef5fbf9f5bffd7b4f21ba61603832/Task-3/Task-3%20images/file%201.png)
- `test/app.test.js`
- `.github/workflows/ci-cd.yml`
- `.eslintrc.json`
- `package.json`
- `README.md`


---

# Step 2: Install Dependencies

Run the following commands to install Jest and ESLint as development dependencies:

```bash
npm install jest eslint --save-dev
```

---

# Step 3: Initialize Git

## Initialize Git and Commit the Project
Run the following commands to initialize a Git repository and commit your work:

```bash
git init
git add .
git commit -m "Initial commit for CI/CD pipeline"
```

## Push to GitHub
Add your remote GitHub repository and push your code:

```bash
git remote add origin <repository-url>
git branch -M main
git push -u origin main
```

---

# Step 4: Test the Workflow

## Create a Feature Branch
Create a new branch for testing the pipeline:

```bash
git checkout -b feature/test-pipeline
git push origin feature/test-pipeline
```

## Monitor the Workflow
1. Go to the **Actions** tab in your GitHub repository.
2. Watch the workflow execute steps:
   - Code checkout.
   - Install dependencies.
   - Run tests.
   - Lint code.
   - Simulate deployment.
```


