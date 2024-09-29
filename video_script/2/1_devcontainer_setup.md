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

These files are related to "Docker" and will help us create a little "mini-machine" or development sandbox running on top of our base machine so we stay organized...

## Populate `devcontainer.json`

```devcontainer.json
{
  "name": "CrewAI + AgentOps (Pt. 2)",
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

To gloss over the details, we are now in a "mini-computer" running on top of our computer. We can play around with CrewAI in this "mini-computer", close it when we're done, and then our base machine (aka our laptop or Desktop or whatever we're using) will be clean as if nothing ever happened.

Let's run a quick test to make sure we're looking good.

As CrewAI is a Python-based tool, and we created a Devcontainer with Python installed (Python 3.12 to be exact)

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

And we are √

the `pwd` command stands for "present working directory"