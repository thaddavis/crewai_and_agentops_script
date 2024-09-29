## Inception

To wrap this up, let's do a few quick things... 

A) Let's record the exact versions of `crewai` and `agentops` we used in this project just in case we want to reference them

One of the conventional ways of doing this is like so...

`touch requirements.txt`
```
agentops==0.3.12
crewai==0.63.6
```

B) Let's store a copy of this code, so you can check it out, on GitHub

If your unfamiliar with how .git and GitHub works there are plenty of resources online for getting up to speed

So what do is use .git to store a copy of all the files and folders in our project...

EXCEPT for the ones listed in this special .gitignore file - for example the .env file

REMEMBER that we never want to share our API keys in order to prevent others from abusing our 3rd-party accounts

So notice how our editor, VSCode, grays the files and folders listed in the .gitignore to indicate to use that they will not be tracked by .git

And after we upload our code to GitHub, notice how the .env file, containing our API keys, is nowhere to be found

C) And finally, let's close our Devcontainer and the POOF!

We are back on our base machine (aka our laptop or Desktop) and it's like nothing ever happened.