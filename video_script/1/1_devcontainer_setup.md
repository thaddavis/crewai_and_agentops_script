## SHOW THE BOILERPLATE DIAGRAM

This is the 1st set of files that we will add...

project_root/
├── .devcontainer/
│   └── devcontainer.json
└── Dockerfile.dev

mkdir .devcontainer
touch .devcontainer/devcontainer.json
touch Dockerfile.dev

These files are compatible with Docker...

## Populate `devcontainer.json`

```devcontainer.json
{
  "name": "CrewAI + AgentOps",
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
WORKDIR /code # set the working directory
ENV PYTHONPATH=/code
```

## Build the Devcontainer

Alrighty, now that we have these files added we can launch our Devcontainer like so...

SHIFT + COMMAND + P -> `Dev Containers: Reopen in Container`

To gloss over the details, we are now in another computer running on our computer. Inception type ish. We can play around with CrewAI in this machine, close it when we're done, and then our base machine will be clean as if nothing ever happened.

Let me know in the comments if you like this approach. I find it helps me stay organized.

Let's run a quick test and make sure we are looking good.

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

```.py
pwd
```