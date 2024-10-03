# SECOND APPROACH

We are now going build a crew of agents using the CrewAI command line interface (or CLI)...

After we set up our crew using the CrewAI CLI, we'll layer on AgentOps for monitoring them

The only software you'll need to install to follow along is Docker Desktop & VSCode

- Docker Desktop will allow us to create a "mini-computer" that runs on top of our actual computer (aka: our laptop or Desktop) and we can experiment with new software inside of this "mini-computer" (like CrewAI) before killing it to easily delete the additional software we installed onto it. This technique keeps our actual base computer clean and untouched. I like this approach for staying organized.

- VSCode is a code editor...

- Think of VSCode as Microsoft Word but for reading and editing code instead of documents

- After installing VSCode, you'll also need to install 2 VSCode plugins btw, namely the

- the Docker extension (id: ms-azuretools.vscode-docker)
- and the "Dev Containers" extension (id: ms-vscode-remote.remote-containers)

- FYI: Both Docker and VSCode are FREE and include support for Mac, Windows, & Linux.

- Let me quickly show you how to install them on Mac so you get a feel for how easy it was for me BUT if your experience is not as straightforward and you get stuck, leave a comment or try entering descriptions of your issues into Google or ChatGPT for help

- Let's go!

https://docs.crewai.com/getting-started/Start-a-New-CrewAI-Project-Template-Method/#creating-a-new-project