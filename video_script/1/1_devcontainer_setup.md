## SHOW THE BOILERPLATE DIAGRAM

Alright! Here we go! From scratch! CrewAI & AgentsOps!

Here we have a empty folder somewhere on our computer as our starting point...

First we're going to set ourselves up so we have a solid foundation to build on top of...

This is the 1st set of files we will add to this empty folder...

project_root/
├── .devcontainer/
│   └── devcontainer.json
└── Dockerfile.dev

mkdir .devcontainer
touch .devcontainer/devcontainer.json
touch Dockerfile.dev

If you've never seen these files before, they might seem strange, but they're related to a popular tool called "Docker"

In the spirit of beginner friendliness we will avoid getting too technical, so for practical purposes just know that we are using Docker because it helps us stay organized.

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

## `Dockerfile.dev` file

- and here is the content to paste into the `Dockerfile.dev` file...

```.Dockerfile.dev
FROM python:3.12-slim
RUN apt-get update && apt-get install -y build-essential
WORKDIR /code # set the working directory
ENV PYTHONPATH=/code
```

## Build the Devcontainer

Alrighty, now that we have these files set up we can launch our "Devcontainer" like so with VSCode...

SHIFT + COMMAND + P -> `Dev Containers: Reopen in Container`

To gloss over the details, we are now building a "mini-computer" that will run on top of our actual computer. We can play around with CrewAI in this "mini-computer", close it when we're done, and then our base machine (aka our laptop / or Desktop) will be clean as if nothing ever happened.

Once again the reason why we are doing this is because over the long term it help us stay organized.

If you know of a better approach than working in Devcontainers, leave a comment so I'm aware.

After building the Devcontainer we should see a new container listed in Docker...

Let's run a quick test and make sure we're looking good.

As CrewAI is a tool built on top of Python, let's make sure we have Python installed

If you take a quick look at the content of the `Dockerfile` you can see we asked Docker to build us a "mini-machine" with Python 3.12 installed on it (PLUS some extra C++ libraries that we will need)

The remaining lines...
  A - tell Docker where in the file system of this "mini-machine" we want to work
  B - tells the Python interpreter where to look for code we import througout our project

The Python interpreter is a tool that reads Python code and executes it for us

After our Devcontainer is built, let's make sure it works as we expect

```.py
pwd
```

And let's make sure Python is working as expected...

```.py
python --version
touch main.py
echo "print('Hello World')" > main.py
python main.py
```

√

And let's delete this file as we won't need it moving forward

```.py
rm main.py
```