## Inception

Let's now wrap this up...

A) Let's record the exact versions of the PyPI packages we used in case we want to reference them in the future

One of the conventional ways of doing this is like so...

`touch requirements.txt`
```
agentops==0.3.12
crewai==0.63.6
python-dotenv==1.0.1
```

B) Let's store a copy of this code on GitHub

We want to store a copy of all of the files and folders in this project EXCEPT for the .env file holding our secrets...

If we add this file called `.gitignore` at the root of our project we list the files and folders we do NOT want to upload to GitHub...

Notice how our editor, VSCode, grays out the files and folders listed in the .gitignore to indicate that they will not be tracked by .git

And after we upload our code to GitHub, notice how the .env file containing our secrets is nowhere to be found

If your unfamiliar with how .git and GitHub works there are plenty of resources online for getting up to speed for example check out this video series I made a couple years ago.

C) And finally, let's close our Devcontainer and the POOF!

We're back on our base machine (aka our laptop or Desktop) and it's like nothing ever happened.