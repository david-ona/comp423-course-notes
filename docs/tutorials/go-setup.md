# Setting up a dev container for Go

* Primary author: [David Ona](https://github.com/david-ona)
* Reviewer: [Thomas Roche](https://github.com/thomas092101)

## Introduction
This is a brief tutorial about how to write a "Hello COMP 423" program in Go using a dev container for setup.

## Prerequisites

- Install [Visual Studio Code](https://code.visualstudio.com/)
- Install the Dev Containers Extension through the VS Code Extensions tab.
- Install [Docker](https://www.docker.com/)

## Creating a Dev Container for Go

### Create a new project directory.
In VS Code, open a new terminal and run the following commands:

```
mkdir <your-project-name>
cd <your-project-name>
```

### Initialize a Git repository:

Run:

```git init```

### Create a Remote Repository on GitHub:

1) Log Into GitHub and navigate to the Create a New Repository page

2) Fill in the details:

- Repository Name
- Description
- Visibility

3) Click Create Repository

### Link your local Repository to GitHub

1) Add the GitHub repository as a remote:

```git remote add origin https://github.com/<your-username>/<repo-name>```

2) Push your local commits to the GitHub repository:

```git push --set-upstream origin main```

## Configure the Dev Container

Create a .devcontainer folder:

```mkdir .devcontainer```

Inside .devcontainer, create a devcontainer.json file, and add the following content to devcontainer.json:

``` 
{
    "name": "Go Dev Container",
    "image": "mcr.microsoft.com/devcontainers/go:1.23",
    "customizations": {
        "vscode": {
            "extensions": ["golang.go"]
        }
    }
}
```

### Dev Container Configuration Explanation

- name: The name of your container.
- image: This tells the container which Docker image to use. Here, we use the latest version of Go.
- customizations: Adds useful configurations to VS Code. Here, we install the Go extension for VS Code.

## Open the Project in the Dev Container

Reopen the project in the container by pressing Ctrl+Shift+P (or Cmd+Shift+P on Mac), typing "Dev Containers: Reopen in Container," and selecting the option. This may take a few mintues while the image is downloaded and the requirements are installed.

Once the projected is reopened in the container, write the following in the terminal to verify that Go has been installed and that your version is up to date:

```go version```

Initialize the Go Module with the following terminal command:

```go mod init hello-go```

This tracks the projects dependencies.

## Write the Hello 423 Program!

Create a new file named main.go in the root of your project. Then, write the following code:

```
package main

import "fmt"

func main() {
    fmt.Println("Hello COMP423")
}
```

This is your Go code. In this code, you:

- Declare a main package (a package is a way to group functions, and it's made up of all the files in the same directory).
- Import the fmt package which contains functions for formatting text, including printing to the console.
- Implement a main function to print a message to the console. A main function exectues by default when you run the main package.

## Run your code!

Use the following command in your terminal:

```
go run .
```

The run command compiles and runs your code in a single step.

## Build your code.

This is another way to run your code by compiling it and running it in two separate steps.
Use the go build terminal command to compile your program:

```go build -o hello423```

Then, run the program directly with:

```./hello423```

The build command is similar to the gcc command from COMP211. Both commands take a source code file as input and produce an executable file as output that you can then run. You can name the output executable with the argument after -o. The command go run compiles and runs the program in one step, but go build produces a standalone executable file.

## Commit your work.

Add all files to the Git repository:

```git add .```

Commit your changes:

```git commit -m <your meaningful commit message>```





## Works Cited
- [Go "Getting Started" Tutorial](https://go.dev/doc/tutorial/getting-started)
- [COMP423 MkDocs Tutorial](https://comp423-25s.github.io/resources/MkDocs/tutorial/)
- [MkDocs Code Blocks Documentation](https://squidfunk.github.io/mkdocs-material/reference/code-blocks/?h=code+block)
- [Microsoft Go Image](https://hub.docker.com/r/microsoft/devcontainers-go)