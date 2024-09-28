## Inception

To wrap this up, let's do a few quick things... 

A) Let's record the exact versions of `crewai` and `agentops` we used in this project just in case we want to reference them

One of the conventional ways of doing this is like so...

`touch requirements.txt`
```
agentops==0.3.12
crewai==0.63.6
```

B) Let's store a copy of this code so you can reference it. Let's store it on GitHub

If your unfamiliar with how .git and GitHub works there are plenty of resources online for getting up to speed

So what we can do is tell .git to store a copy of all the files and folders in our project EXCEPT for the ones listed in this special .gitignore file

REMEMBER that on principle we never want to share our API keys

And notice how our editor, VSCode, grays the files and folders listed in the .gitignore for us

So when we upload our code to GitHub notice how the .env file containing our API keys is nowhere to be found

C) Let's close our Devcontainer and the POOF!

We are back on our base machine and it's like nothing ever happened.