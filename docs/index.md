# AVDASI 2 docs

This site contains general documentation for the AVDASI 2[^1] design, build, and test unit. It's aimed at students on the unit, but we're publishing it openly in case it's useful to others. If you use it, [we'd love to hear about it](mailto:AVDASI2@bristol.ac.uk).

It's hosted on the [AVDASI 2 GitHub org](https://github.com/AVDASI2), and uses [MkDocs](https://www.mkdocs.org) auto-compiled via a GitHub Action. Code from repos like [AVDASI 2 Example_Code](https://github.com/AVDASI2/Example_Code) can be auto-synced to the docs so code snippets can be displayed and will update after every new push. 

## Contribute

Anyone can [fork and pull request](https://docs.github.com/en/get-started/exploring-projects-on-github/contributing-to-a-project) changes to the docs which will be reviewed by admins and published. 

If you want to trial stuff locally before pull requesting just clone the (original or forked) repo and do:

```bash
pip install mkdocs-material mkdocs-implicit-index
mkdocs serve
```

Then open [http://127.0.0.1:8000](http://127.0.0.1:8000).

## Navigation structure

This MkDocs is configured to use [mkdocs-literate-nav](https://oprypin.github.io/mkdocs-literate-nav/) to pull nav and page ordering from a list in _index.md_ within each folder, like this:

- [Avionics](Avionics/)
- [Aerodynamics](Aerodynamics/)
- [Structures](Structures/)

[^1] Aerospace Vehicle Design And Systems Integration
