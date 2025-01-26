# Setting Up a Dev Container for Rust

* Primary author: [Ishita Siddamreddy](https://github.com/ishitasr76)
* Reviewer: [Suhas Puttoju](https://github.com/suhasp3)

## **Prerequisites**
* Docker: have it downloaded on your device
* Visual Studio Code (VS Code):
* Git: 
* VS Code Remove - Containers Extension
* Introduction knowledge of the basics of Rust programming language

## **Project Setup: Creating the Repository**
### Step 1: Setting up a Dev Container Project
**Create a new project Directory**

Open a terminal or the command prompt to run the commands. In this section we will be creating a directory and initializing it in the git repo. We will then create a README file for our project.

1. Create a new directory for your project
```bash
mkdir rust-tutorial
cd rust-tutorial
```
2. Initialize the new Git repository
```bash
git init
```
3. Create the README file
```bash
echo "# Rust Tutorial" > README.md
git add README.md
git commit -m "Initial commit with README"
```

### Step 2: Create a Remote Repository on GitHub
1. Log in to your GitHub account and navigate to the "Create a New Repository" page.
2. Ensure you fill in the following details:
    * Repository Name: `rust-tutorial`
    * Description: "Simple Rust tutorial that outputs Hello COMP423!"
    * Visibility: Public

3. Do not initialize the repository with a README, .gitignore, or license. You already did that using the terminal in the previous step. 
4. Click **Create Repository**.

### Step 3: Link the local repository to the GitHub (remote repository)
1. Add the GitHub repository as a remote
```bash
git remote add origin https://github.com/<your-username>/rust-tutorial.git
```
Make sure to replace `<your-username>` with your GitHub username.
2. Check what your repository's default branch is using `git branch`. You should expect it to indicate that your default branch is `main`.
3. Push your local commits to the GitHub repository. 
```bash
git push --set-upstream origin main
```
All the changes you have made so far should now be pushed up to remote repository and you can see this commit on GitHub as well. 

## **Set up the Development Environemnt**
### Step 1: Add Development Container Configuration
1. Open the `rust-tutorial` directory on VS Code. 
    * File->Open Folder->rust-tutorial
2. Install the Dev Containers extension for VS Code.
3. Create a `.devcontainer` directory in the root of your project. Add the `devcontainer.json` file to the created directory. The configuration of the file should be: 
`.devcontainer/devcontainer.json`
4. In this file, add the following code
```bash
{
  "name": "COMP423 Course Notes",
  "image": "mcr.microsoft.com/devcontainers/rust:latest",
  "customizations": {
    "vscode": {
      "settings": {},
      "extensions": ["rust-lang.rust-analyzer"]
    }
  },
  "postCreateCommand": "cargo build"
}

```
We are adding the `rust-analyzer` extension via VS Code automatically whenever the container is created. It provides us with a variety of different features such as code completion, error detection, etc.
### Step 2: Add `Cargo.toml` Rust Dependency Configuration
1.  In the root directory, create a file called `Cargo.toml`
2. Add the following lines of code to the file to specify the dependencies
```rust
[package]
name = "rust-devcontainer"
version = "0.1.0"
edition = "2021"

[dependencies]
serde = "1.0"
tokio = "1.0"
```

3. Verify the Rust installation by running the following code in the terminal.
```bash
rustc --version
```
Make sure the recent version is being run to ensure the setup was successful. 

### Step 3: Reopen the project in VS Code Dev Container
Open the project in the container by pressing `Ctrl+Shift+P` and typing in "Dev Containers: Reopen in Container"

After this, open up a new terminal in VS Code and run `rustc --version`

## **Making the Actual Project**
### Step 1: Create the Rust Project
1. In the project root, run the following code.
```bash
cargo new hello_comp423 --vcs none
cd hello_comp423
```
This will create a new Rust Binary Project without making/initializing a git repository

### Step 2: Writing and running the program
1. Modify the `main.rs` file
Navigate to the `hello_comp423/src/main.rs` file and update its contents:
```rust
fn main() {
    println!("Hello COMP423");
}
```
2. Compile the program
```bash
cargo build
```
3. Run the program
```bash
cargo run
```

## **You are all done!**
You are successfully created your first rust program :) 



