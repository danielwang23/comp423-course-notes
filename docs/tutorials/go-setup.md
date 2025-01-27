# Setting up a dev container for Go!

* Primary author: [Daniel Wang](https://github.com/danielwang23)
* Reviewer: [Paul Yang](https://github.com/Paulyang80)

# Introduction

Go (often referred to as *Golang*) is a statically-typed, open source programming language created by Google to develop web applications, cloud and networking services, and other types of software. It emphasizes simplicity, efficiency, and concurrency, making it popular for modern applications.

In this tutorial, you’ll learn how to set up a basic Development Container (dev container) for Go in Visual Studio Code from a blank directory, to configuring git, and running a simple “Hello COMP423” program.

---

# Prerequisites

!!! note "Before You Begin"
    Ensure the following prerequisites are met before starting the setup process:

1. **A GitHub account**: If you don’t have one yet, sign up at [GitHub](https://github.com/).
2. **Git installed**: Install Git if you do not already have it.
3. **Docker installed**: Required to run the dev container.
4. Install **Visual Studio Code (VS Code)** and the **Remote - Containers** plugin under extensions.
5. Have a basic understanding of Git workflows, command-line basics, and containerized development.

---

## Step 1: Creating a new Git Repository

1. Open a new bash terminal (or in VS Code terminal).
2. Create and navigate into a new, empty directory:

        mkdir go-hello-comp423
        cd go-hello-comp423
    
3. Initialize a new Git repository:

        git init

4. Create a new repository on **GitHub**, and then link it to your local project:

        git remote add origin https://github.com/yourusername/go-hello-comp423.git

5. Push your initial commit:

        echo "# Go DevContainer Project" > README.md
        git add README.md
        git commit -m "Initial commit"
        git push -u origin main

---

## Step 2: Configuring your Dev Container

We’ll use a Microsoft Go Dev Container base image so that we don’t have to build everything from scratch.

1. Create a folder named ```.devcontainer```:

        mkdir .devcontainer

2. Inside that folder, create a file called ```devcontainer.json``` (can be done with ```touch .devcontainer/devcontainer.json``` in terminal) with the following contents:

```Json
    {
      "name": "Go Dev Container",
      "image": "mcr.microsoft.com/devcontainers/go:latest",
      "customizations": {
        "vscode": {
          "extensions": [
            "golang.go"
           ]
         }
       }
    }
```

!!! info "Explanation"
    - name: The display name for the container in VS Code.
    - image: Points to a prebuilt Go environment maintained by Microsoft.
    - extensions: Automatically installs the official Go plugin for VS Code (published by the Go Team at Google).

3. Commit and push the configuration:

```bash
    git add .devcontainer/devcontainer.json
    git commit -m "Added DevContainer configuration"
    git push
```

---

## Step 3: Open the DevContainer

1. Open your ```go-hello-comp423``` project directory in VS Code.
2. Open the Command Palette (Ctrl+Shift+P on Windows/Linux or Cmd+Shift+P on Mac).
3. Search for and select Remote-Containers: Open Folder in Container.

    - Wait for VS Code to build and provision your container. Once complete, your environment
    will be running inside the container, with Go and all required tools installed.

4. Verify the container setup by checking the Go version:

        go --version

You should see a recent Go version displayed. This confirms Go is installed successfully in your Dev Container.

---

## Step 4: Create a New Go Project

1. Create a new file, main.go:

        touch main.go

2. In ```main.go```, write a simple Go program:

```go
    package main

    import "fmt"

    func main() {
        fmt.Println("Hello COMP423")
    }
```

---

## Step 6: Run the Program

!!! Tip "Running Go Programs"
    You can run Go programs directly without building them using the ```go run``` command.

1. Run the program using ```go run```:

```bash
    go run main.go
```

You should see the output:

```bash
    Hello COMP423
```

--- 

## Step 7: Building your program

Alternatively, you can use ```go build``` which compiles your Go code into a binary file that is compiled, and executable.

1. Build the project:

        go build main.go

2. After building, you will see a binary executable file named ```main``` (on Linux/macOS)

3. Run the binary file directly:

            ./main

    This should again print:

            Hello COMP423

!!! note "Difference Between ```run``` and ```build```" 
    - ```go run```: Compiles and runs the code immediately but doesn't create a binary file. 
    - ```go build```: Compiles the code into a binary executable file, which can be kept, dsitributed, or executed multiple times later without recompiling.
--- 

## Step 8: Commiting your work and Sharing

1. Commit and Push changes in your program to Github:

        git add main.go
        git commit -m "Added Hello COMP423 program"
        git push
 
!!! Success "Success" 
    Congratulations, now you have successfully completed the tutorial!

## **Summary**

Congratulations! Throughout this tutorial you have:

- Started from a blank directory and initialized a Git repository.
- Created a Dev Container configuration using Microsoft’s base Go image.
- Installed the official Go plugin for VS Code.
- Written a “Hello COMP423” program in Go.
- Explored both go run for executing your program.
- You’re now set up with a reproducible, containerized Go development environment! Keep experimenting with Go modules, package imports, testing, and more as you progress through your Go journey.

## References:

- [Go (programming language)](https://go.dev/)
- [Go Documentation](https://go.dev/doc/)
- [Go Library](https://pkg.go.dev/std)
- [Go Plugin](https://code.visualstudio.com/docs/languages/go)