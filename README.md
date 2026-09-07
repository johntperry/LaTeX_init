# $ \LaTeX $ initialisation

LaTeX_init uses the python package cookiecutter to instantly generate an instance of a $ \LaTeX $ document in the format desired. It solves the problem of wanting to use $ \LaTeX $ to format a given document due to its versatility without the hassle of having to copy/paste previous $ \LaTeX $ projects or needing to change a number of different in-text sections that would be required by using `git clone` by asking a series of simple questions and actively inputting where appropriate.

By default, this project allows the choice of a few different document formats which are appropriate for different document formats. Currently, this includes:
- `article`: For short documents to short reports, this does it all!
- `report`: Like article but serious, use this for a no-holds-barred serious document format.
- `moderncv`: This reproduces a professional and formal letter, using `moderncv`'s impressive and fast letter formatting settings.

## Initialisation
 Generate from the command line in the folder desired using the command:

`
python -m cookiecutter https://github.com/johntperry/LaTeX_init.git
`

then answering the given questions to customise the setup.

To ensure citations work correctly, ensure that the vscode settings.json file includes the following:
```
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
```
in essence, this re-runs the compilation after the first run which allows citations/references that refer to points later in the document to still correctly reference without breaking.

## Future Improvements
For future, consider adding a setting with cookiecutter that allows for setting up multiple different formats with the same command, and the argument "What file type is desired?" > "short-report"/"long-report" etc. This also means that changes across the base packages (.sty files) and in the main document remain more reliably synced across all template formats.

Future additions: (update project init also)
- Have a hook that allows a pre-prompt to check if there are any properties which can be inherited as a daughter file to a larger project. (Like exists in the repo 'Project_init')
- This should read the 'project_defaults' json and reduce the number of questions that need to be answered each time a folder is copied.
- Update the 'what file type is desired' question to be more representative of the actual desired document type, e.g.:
    - 'short/long report', 'letter'.
    - This would require an extra layer of a cookiecutter hook to dynamically restructure into a document_class that is appropriate.