## Build the Devcontainer

Ok! Here we go! Starting from scratch (aka an empty folder)...

## SHOW THE BOILERPLATE DIAGRAM

This is the 1st set of files that we'll add to this empty folder...

project_root/
├── .devcontainer/
│   └── devcontainer.json
└── Dockerfile.dev

mkdir .devcontainer
touch .devcontainer/devcontainer.json
touch Dockerfile.dev

These files are related to "Docker" and will help us create a little "mini-machine" or development sandbox running on top of our machine...

## Populate `devcontainer.json`

```devcontainer.json
{
  "name": "CrewAI + AgentOps (DEMO 2)",
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

## Populate `Dockerfile.dev`

```.Dockerfile.dev
FROM python:3.12-slim
RUN apt-get update && apt-get install -y build-essential
```

## Build the Devcontainer

Now that we have these files added we can launch our "mini-machine" or Development container like so...

SHIFT + COMMAND + P -> `Dev Containers: Reopen in Container`

This "Dev containers" command palette option will only be available if you have the "Dev containers" extension installed on your VSCode

## Waiting

Now we wait for the Dev container to be built...

## After

To gloss over the details, we are now in a "mini-computer" running on top of our computer

Let's run a quick test to make sure we're looking good.

As CrewAI is a Python-based tool, we created a Devcontainer with Python installed (Python 3.12 to be exact as you see cause by line  of the Dockerfile.dev)...

Let's make sure Python is working as expected

```.py
python --version
touch main.py
echo "print('Hello World')" > main.py
python main.py
```

√

```.py
rm main.py
```

And let's double check that we're in the location we specified in the .devcontainer.json file...

```.py
pwd
```

FYI: the `pwd` command stands for "present working directory"

If we look at the root of our base machine we can see that the /code folder is no where to be found...

The mental model to keep in mind is that we have 2 machines running on our machine...

- the base machine (aka our laptop or Desktop)
- and the Dev container (which is like a little mini-machine running on top of our base machine)

Each of these systems has its own file system and is capable of having completely different software installed

We will be working in the Dev container moving forward so that when we finish this walkthrough we can simply kill the Dev container and our base machine will be left clean

This helps us stay organized overtime and avoids us having to install unnecessary software on our base machine