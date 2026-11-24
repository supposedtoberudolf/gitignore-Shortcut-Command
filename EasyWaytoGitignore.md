# Easy Way to Generate `.gitignore`

A quick bash script to instantly generate a ready-to-use `.gitignore` file (for C/C++, CMake, C#/.NET, Java, Node.js, Python, IDEs, OS, and temporary files) in any project folder.

## Setup Instructions

### 1. Create a local `bin` directory
```bash
mkdir -p ~/bin
```

### 2. Create the `gitignore` script
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

### 3. Make the script executable
```bash
chmod +x ~/bin/gitignore
```

### 4. Add `~/bin` to your `PATH`
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

## Usage

Navigate to your project folder and run:
```bash
gitignore
```