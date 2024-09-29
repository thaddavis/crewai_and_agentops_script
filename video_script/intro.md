(LOOK CAMERA)

In this video we'll introduce 2 new tools coming out of the Agent development world

The 1st is CrewAI and the 2nd is AgentOps

CrewAI is a Multi-Agent framework and AgentOps is an Agent Observability tool

CrewAI is one of the leaders in their space as is AgentOps...

(LOOK AWAY)

For reference, here's a list showing the leading open source multi-agent frameworks ordered by GitHub stars as of October 2024...

1. LangChain/LangGraph - 92.7k/5.8k stars
  - 81 contributors - 41.9k in Discord - https://github.com/langchain-ai/langgraph
2. MetaGPT - 43.7k stars
  - 97 contributors - 5.1k in Discord - https://github.com/geekan/MetaGPT
3. AutoGen - 31.1k stars
  - 346 contributors - 19.7k in Discord - https://github.com/microsoft/autogen
4. Flowise - 30.1k stars
  - 139 contributors - 1.2k in Discord - https://github.com/FlowiseAI/Flowise
5. LangFlow - 29.5k stars
  - 162 contributors - 7.9k in Discord - https://github.com/langflow-ai/langflow
6. CrewAI - 19.5k stars
  - 142 contributors - 7.6k on X.com - https://github.com/crewAIInc/crewAI
7. Superagent - 5.1k stars
  - 66 contributors - 202 on Discord - https://github.com/superagent-ai/superagent
8. Agent Zero - 4.3k stars
  - 6 contributors - 1,316 on Discord - https://github.com/frdel/agent-zero
9. ell - 3.7k stars
  - 19 contributors - 456 on Discord - https://github.com/MadcowD/ell
10. Agency Swarm - 2.4k stars
  - 10 contributors - 329 on Discord - https://github.com/VRSEN/agency-swarm

<!-- And just so we get an overall view of the multi-agent landscape, let's rerank by social media reach...

1. LangChain/LangGraph - 92.7k/5.8k stars - 81 contributors - 41.9k in Discord - https://github.com/langchain-ai/langgraph
2. AutoGen - 31.1k stars - 346 contributors - 19.7k in Discord - https://github.com/microsoft/autogen
3. LangFlow - 29.5k stars - 162 contributors - 7.9k in Discord - https://github.com/langflow-ai/langflow
4. CrewAI - 19.5k stars - 142 contributors - 7.6k on X.com - https://github.com/crewAIInc/crewAI
5. MetaGPT - 43.7k stars - 97 contributors - 5.1k in Discord - https://github.com/geekan/MetaGPT
6. Agent Zero - 4.3k stars - 6 contributors - 1.3k on Discord - https://github.com/frdel/agent-zero
7. Flowise - 30.1k stars - 139 contributors - 1.2k in Discord - https://github.com/FlowiseAI/Flowise
8. ell - 3.7k stars - 19 contributors - 456 on Discord - https://github.com/MadcowD/ell
9. Agency Swarm - 2.4k stars - 10 contributors - 329 on Discord - https://github.com/VRSEN/agency-swarm
10. Superagent - 5.1k stars - 66 contributors - 202 on Discord - https://github.com/superagent-ai/superagent -->

https://www.linkedin.com/posts/adamsil_here-is-everything-that-you-need-to-know-activity-7241894867885293569-uvBt?utm_source=share&utm_medium=member_desktop

And here is a list showing the leading open source Agent Observability tools ordered by GitHub stars as of October 2024 as well

1. LangChain/LangSmith - 92.7k/379 stars - 36 contributors - 41.9k in Discord - https://github.com/langchain-ai/langsmith-sdk 
2. LangFuse - 5.7k - 54 contributors - 1.7k in Discord - https://github.com/langfuse/langfuse
3. AgentOps - 1.7k stars - 19 contributors - 2.3k in Discord - https://github.com/AgentOps-AI/agentops

<!-- AND let's rerank by social media reach to get an overall view again...

1. LangChain/LangSmith - 92.7k/379 stars - 36 contributors - 41.9k in Discord - https://github.com/langchain-ai/langsmith-sdk
2. AgentOps - 1.7k stars - 19 contributors - 2.3k in Discord - https://github.com/AgentOps-AI/agentops
3. LangFuse - 5.7k - 54 contributors - 1.7k in Discord - https://github.com/langfuse/langfuse -->

(LOOK CAMERA)

If there are other companies that should have been on these lists please let me know in the comments...

(CUT)

For the remainder of this video, we'll DEMO how YOU can use CrewAI w/ AgentOps via 2 beginner-friendly examples

- 1) In DEMO #1, we'll build a team of agents from scratch manually so we get a solid understanding of how CrewAI works (plus we'll also show how to include monitoring w/ AgentOps)
- 2) In DEMO #2, we'll build a team of agents using the CrewAI CLI and task them with writing us a hit song (that we'll actually make to see what it sounds like) and we'll be integrating AgentOps into this 2nd group of agents for monitoring as well. Using the CrewAI CLI is the recommended approach for how to build CrewAI-based projects.

- IF you want to code along step-by-step, you'll need to install 2 tools onto your machine: VSCode & Docker Desktop

- Both of these 2 tools are FREE and should only take a few clicks and a few minutes to install as they offer extremely easy-to-use installation processes with support for Mac, Windows, and Linux.

- I'll be using Mac in this video but the general process of what we'll be doing will be the same for Windows and Linux. 

- Let me quickly show how I installed these 2 tools on Mac so you get a feel for how easy it was for me BUT if your experience is not as straightforward and you get stuck, please leave a comment so I'm aware or try entering descriptions of your issues into Google or ChatGPT for help troubleshooting

- Here's how to download and install Docker Desktop on Mac...
- Go to the official download page
  - https://www.docker.com/products/docker-desktop/
- Download the appropriate version for your machine
  - for me this is Apple Silicon
- Double click the downloaded file and you'll be presented with a window to add Docker Desktop to your Applications folder
- AND THAT'S IT

- Here's how to download and install VSCode on Mac...
- Go to the official download page linked in the Description
  - https://code.visualstudio.com/Download
- Download the appropriate version
  - for me it's Apple Silicon
- Unzip the downloaded .zip file
- Drag the unzipped application into your Applications folder
- AND THAT'S IT

- IT'S THAT EASY: https://www.youtube.com/watch?v=v83ckl-5i8Q&t=26s

Finally, you will need to add the following extensions to VSCode once it's installed

After opening VSCode, you can come over to the Extensions Marketplace available in the side menu and install:

- A) the Docker extension (id: ms-azuretools.vscode-docker)
  - type "Docker" in the search bar and after finding it in the panel you should see a button to install it in one click
- and B) the "Dev Containers" extension (id: ms-vscode-remote.remote-containers)
  - type "Dev Containers" in the search bar and after finding it in the panel you should also see a button to install it in one click

- ALL OF THE CODE PRESENTED IS LINKED IN A PUBLIC GITHUB REPO