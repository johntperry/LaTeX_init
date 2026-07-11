This file uses cookiecutter to instantly generate an instance of a LaTeX document in the format desired, generate from the command line in the folder desired using the command:
python -m cookiecutter https://github.com/johntperry/LaTeX_init.git
and then input the names of some of the desired arguments to finish the setup.

To ensure citations work correctly, ensure that the vscode settings.json file includes the following:
    "latex-workshop.latex.recipes": [
        {
            "name": "latexmk 🔃",
            "tools": [
                "latexmk"
            ]
        }
    ],
    "latex-workshop.latex.autoBuild.run": "onSave",
    "latex-workshop.latex.currentRecipe.name": "latexmk 🔃"

For future, consider adding a setting with cookiecutter that allows for setting up multiple different formats with the same command, and the argument "What file type is desired?" > "short-report"/"long-report" etc. This also means that changes across the base packages (.sty files) and in the main document remain more reliably synced across all template formats.

Future additions: (update project init also)
- Have a hook that allows a pre-prompt to check if there are any properties which can be inherited as a daughter file to a larger project.
- This should read the 'project_defaults' json and reduce the number of questions that need to be answered each time a folder is copied.