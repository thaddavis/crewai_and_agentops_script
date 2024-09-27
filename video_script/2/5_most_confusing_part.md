## So this is BY FAR the most confusing part of this walkthrough but bear with me

- Because the crewai CLI generates the project files within a new folder and not in the current folder...
- I will move the generated files up one level...
- I'll move everything up one level with this command: `mv .* * ..`
- All the files within the generate folder are now in the current folder

- We want our current folder to hold a `crewai` project and not a folder within our current folder to hold a `crewai` project
- Once again excuse me if this is confusing

- We also have to update an import: `from src.frequency_music_crew.crew import FrequencyMusicCrewCrew`
- delete the poetry.lock
- reinstall the dependencies: `poetry install`
- And now we should be good √

## Fixing import warnings

- `poetry env info`
- And copy the "path" into the interpreter path setting in VSCode
- SHIFT + COMMAND + P
  - `Python: Select Interpreter`

- This let's VSCode know where to look for 3rd party packages
- And I know it's confusing because we used one tool aka `pip` to install `crewai` onto our machine and we are using another tool aka `poetry` to install packages into our project but AYE! welcome to Python development