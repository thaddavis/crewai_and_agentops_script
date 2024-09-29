## SHOW THE BOILERPLATE DIAGRAM

Alright! Here we go! From scratch! CrewAI! AgentsOps!

Here we have an empty folder somewhere on our computer as our starting point...

First, we're going to set ourselves up so we have a solid foundation to build on top of...

This is the 1st set of files we'll add to this empty folder...

project_root/
├── .devcontainer/
│   └── devcontainer.json
└── Dockerfile.dev

mkdir .devcontainer
touch .devcontainer/devcontainer.json
touch Dockerfile.dev

If you've never seen these files before, they're related to a popular tool called "Docker"

To stay beginner-friendly we'll avoid getting too technical, but just know, that we're using Docker to stay organized.

## `devcontainer.json` file

- Here is the content to paste into the `devcontainer.json` file

```devcontainer.json
{
  "name": "CrewAI + AgentOps (Pt. 1)",
  "build": {
    "dockerfile": "../Dockerfile.dev"
  },
  "customizations": {
    "vscode": {
        "extensions": [
            "ms-python.python",
            "ms-python.vscode-pylance",
            "ms-python.black-formatter",
            "ms-python.debugpy",
            "ms-azuretools.vscode-docker",
            "shd101wyy.markdown-preview-enhanced"
        ],
        "settings": {}
    }
  },
  "forwardPorts": [],
  "workspaceMount": "source=${localWorkspaceFolder},target=/code,type=bind,consistency=delegated",
  "workspaceFolder": "/code",
  "runArgs": []
}
```

Over the course of this video you'll understand what the content of this file means...

## `Dockerfile.dev` file

- and here is the content to paste into the `Dockerfile.dev` file...

```.Dockerfile.dev
FROM python:3.12-slim
RUN apt-get update && apt-get install -y build-essential
WORKDIR /code # set the working directory
ENV PYTHONPATH=/code
```

Likewise, over the course of this video you'll understand what the content of this file means...

## Build the Devcontainer

Alrighty, now that we have these files set up we can launch our Devcontainer...

(LOOK CAMERA)

To gloss over the details, when I say "launch our Devcontainer" I mean we're going to build a "mini-computer" / or "mini-machine" that will run on top of our actual computer. We can play around with CrewAI in this "mini-machine", close it when we're done, and then our base machine (aka our laptop or Desktop or whatever we're using) will be clean as if nothing ever happened.

Here's how we launch the Devcontainer...

In VSCode we type...

SHIFT + COMMAND + P -> `Dev Containers: Reopen in Container`

Once again the reason why we're doing this is because over the long term it help us stay organized.

If you know of a better approach than working in Devcontainers, leave a comment so I'm aware.

After building the Devcontainer we should see a new container listed in the Docker Desktop GUI...

Let's quickly test out this Development Container and make sure we're looking good...

As CrewAI is a tool built on top of Python, let's make sure we have Python installed

Let's make sure Python is working as expected...

```.py
python --version
touch main.py
echo "print('Hello World')" > main.py
python main.py
```

The Python interpreter is a program that reads instructions written in the Python programming language and executes them

So here we are passing the main.py file to the Python interpreter and it prints out the text "Hello World"

GREAT!

If we look at the content of the `Dockerfile` you can see we asked Docker to build us a "mini-machine" with Python 3.12 installed (PLUS some extra C++ libraries that are required by CrewAI under the hood)

The remaining lines of this Dockerfile specify where in the file system of this Devcontainer, or "mini-machine", we want to do our coding work

So if we type...

```.py
pwd
```

You see we're in the /code folder of our "mini-machine"

This code folder is sitting at the root of the file system on our "mini-machine"

If we take a look at the root of the file system of our actual machine you can see the /code folder is nowhere to be found...

So moving forward we'll be doing all of our work inside this "mini-machine" or Dev container...

At the end of this walkthrough we will kill our Dev container and our base machine will be clean as if nothing ever happened...

If any beginners are feeling lost at this point, I recommend watching the whole video to get an overall perspective of what's going on here before returning to any confusing parts...

√

Let's quickly delete this test file as we won't need it moving forward

```.py
rm main.py
```