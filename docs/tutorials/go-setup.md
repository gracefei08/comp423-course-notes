# Setting up a dev container for Go
Primary author: [Grace Fei](https://github.com/gracefei08)

## Prerequisites
Before starting, ensure you have the following tools installed on your machine:

- [Docker](https://www.docker.com/)
- [Visual Studio Code](https://code.visualstudio.com/)
- Remote - Containers extension for VS Code
- [Git](https://git-scm.com/)

## Instructions

### Step 1: Start with a Blank Directory

1) Create a new directory for your project:

```bash
mkdir go-dev-container
cd go-dev-container
```

2) Initialize a Git repository:

```bash
git init
```

### Step 2: Create the Dev Container Configuration Files

1) Inside the project directory, create a .devcontainer folder:

```bash
mkdir .devcontainer
```

2) Inside .devcontainer, create a devcontainer.json file:

```bash
touch .devcontainer/devcontainer.json
```

3) Populate devcontainer.json with the following configuration:

```json 
{
  "name": "Go Dev Container",
  "image": "golang:1.20",
  "features": {},
  "customizations": {
    "vscode": {
      "settings": {
        "go.formatTool": "gofmt",
        "editor.formatOnSave": true
      },
      "extensions": ["golang.Go"]
    }
  },
  "postCreateCommand": "go mod init go-dev-container"
}
```
!!! info "Explanation of devcontainer.json"
    - name: Specifies the name of your Dev Container.
    - image: Uses the official Go Docker image with version 1.20.
    - features: Placeholder for additional Dev Container features.
    - customizations.vscode.extensions: Automatically installs the Go extension for VS Code.
    - postCreateCommand: Runs a command after the container is created to initialize a Go module.

### Step 3: Open the Project in the Dev Container

1) Open your project in VS Code.

2) Use the Remote-Containers: Open Folder in Container command from the Command Palette (Ctrl+Shift+P or Cmd+Shift+P).

3) Select your project folder.

4) VS Code will build and open the Dev Container.

### Step 4: Write the "Hello COMP423" Program

1) Create a new file named main.go in the project directory:

```
touch main.go
```

2) Add the following Go code to main.go:

``` go
package main

import "fmt"

func main() {
    fmt.Println("Hello COMP423")
}  
```

### Step 5: Build and Run the Program

1) Build the program using the build subcommand:

```bash
go build -o hello_comp423
```

This creates a binary file named hello_comp423 in your project directory. The build subcommand compiles the code but does not execute it immediately, similar to the gcc command used in COMP211 for compiling C programs.

2) Run the compiled binary:

```bash
./hello_comp423
```

Expected output:

```bash
Hello COMP423
```
!!! info Help
      If anything goes wrong, you can use the `$ go help` command to see helpful commands.

