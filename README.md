# Easy Way to Generate `.gitignore`

## Description

Easy Way to Generate `.gitignore` is a Bash command-line script that creates a ready-to-use `.gitignore` file in any project folder. It includes ignore rules for C/C++, CMake, C#/.NET, Java, JavaScript/Node.js, Python, common IDEs, OS generated files, and temporary files. Instead of writing or copying `.gitignore` rules for every new project, you can run a single command to generate the file right away.

## Features

* Generates a `.gitignore` file in your current working directory with one command
* Checks if a `.gitignore` file already exists and asks for confirmation before overwriting it
* Keeps the existing `.gitignore` file unchanged if you cancel the overwrite prompt
* Includes ignore rules for:
  * C and C++
  * CMake
  * C# and .NET
  * Java
  * JavaScript and Node.js
  * Python
  * IDE and editor files (`.vscode/`, `.idea/`, `*.iml`)
  * OS generated files (`.DS_Store`, `Thumbs.db`, `desktop.ini`)
  * Temporary files (`*.tmp`, `*.temp`, `*.log`, `*.swp`, `*.swo`, `*~`, `tempCodeRunnerFile.c`)
* Works from any folder once `~/bin` is added to your `PATH`

## Tech Stack

* Bash

## Project Structure

```text
.
└── EasyWaytoGitignore.md   # Setup instructions, the gitignore Bash script, and usage steps
```

## Requirements

* Bash (Linux, Git Bash, or WSL) or Zsh (macOS or Zsh environments)

## Installation

1. Create a local `bin` directory in your home folder:

```bash
mkdir -p ~/bin
```

2. Create the `gitignore` script inside `~/bin`:

```bash
cat > ~/bin/gitignore <<'EOF'
#!/bin/bash

if [ -f ".gitignore" ]; then
    read -r -p ".gitignore already exists. Overwrite? (y/N): " confirm
    if [[ ! "$confirm" =~ ^[Yy]$ ]]; then
        echo "Aborted. Existing .gitignore was not modified."
        exit 0
    fi
fi

cat > .gitignore <<'GITIGNORE'
# C / C++
*.exe
*.out
*.o
*.obj
*.a
*.so
*.dll
*.dylib
*.gch

# CMake
CMakeFiles/
CMakeCache.txt
cmake_install.cmake
Makefile
compile_commands.json

# C# / .NET
bin/
obj/
*.user
*.suo
*.userosscache
*.ncb
*.sln.docstates
.vs/

# Java
*.class
*.jar
*.war
*.ear
target/
out/
.gradle/
build/

# JavaScript / Node.js
node_modules/
npm-debug.log*
yarn-debug.log*
yarn-error.log*
.pnpm-debug.log*
.npm/
.yarn/
.pnp.*
dist/

# Python
__pycache__/
*.py[cod]
*.pyo
*.pyd
.pytest_cache/
.mypy_cache/
.ruff_cache/
.venv/
venv/
env/
ENV/
*.egg-info/
dist/
build/

# IDE / Editors
.vscode/
.idea/
*.iml

# OS generated files
.DS_Store
Thumbs.db
desktop.ini

# Temporary files
*.tmp
*.temp
*.log
*.swp
*.swo
*~
tempCodeRunnerFile.c
GITIGNORE

echo ".gitignore created successfully!"
EOF
```

3. Make the script executable:

```bash
chmod +x ~/bin/gitignore
```

4. Add `~/bin` to your `PATH`:

For **Bash** (Linux / Git Bash / WSL):

```bash
echo 'export PATH="$HOME/bin:$PATH"' >> ~/.bashrc
source ~/.bashrc
```

For **Zsh** (macOS / Zsh users):

```bash
echo 'export PATH="$HOME/bin:$PATH"' >> ~/.zshrc
source ~/.zshrc
```

## How to Run / Usage

1. Navigate to your project folder in the terminal.
2. Run the command:

```bash
gitignore
```

### Sample Output (New File)

```text
.gitignore created successfully!
```

### Sample Output (Existing `.gitignore`)

If a `.gitignore` file already exists in the folder, the script asks before overwriting it:

```text
.gitignore already exists. Overwrite? (y/N): n
Aborted. Existing .gitignore was not modified.
```

Enter `y` or `Y` to overwrite the existing file:

```text
.gitignore already exists. Overwrite? (y/N): y
.gitignore created successfully!
```
