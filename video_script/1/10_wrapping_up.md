## Inception

To wrap this up, let's do a few quick things... 

A) Let's record the exact versions of `crewai` and `agentops` we used in this project for easy reference

One of the conventional ways of doing this is like so...

`touch requirements.txt`
```
agentops==0.3.12
crewai==0.63.6
```

B) Let's store a copy of this code so you can reference it. Let's store it one GitHub

If your unfamiliar with how .git and GitHub works there are plenty of resources for figuring it out

AND REMEMBER: We do not want to share our API keys

So what we can do is tell .git to store a copy of all the files and folders in our project EXCEPT for the ones listed in this special .gitignore

Notice how our editor, VSCode, grays out any files and folder listed in the .gitignore

When we upload our code to GitHub notice how the .env file containing our API keys is nowhere to be found

C) Let's close our Devcontainer and the POOF!

It's like nothing ever happened.