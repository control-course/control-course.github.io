# Bristol Flight Lab docs

This site contains general documentation for [Bristol Flight Lab](http://bristolflightlab.com).

It's hosted on the [Flight Lab's GitHub org](http://github.com/UoBFlightLab), and uses [MkDocs](https://www.mkdocs.org) auto-compiled via a GitHub Action. Flight Lab members can push changes to the docs which will be approved by an owner and published. If you want to trial stuff locally first just clone the repo and do:

```bash
pip install mkdocs-material mkdocs-implicit-index
mkdocs serve
```

Then open [http://127.0.0.1:8000](http://127.0.0.1:8000).

## Navigation structure

This MkDocs is configured to use [mkdocs-literate-nav](https://oprypin.github.io/mkdocs-literate-nav/) to pull nav and page ordering from a list in _index.md_ within each folder, like this:

- [Flight controller basics](flight-controller-basics/)
- [Conventions and standards](conventions/)
- [Example section](example-section/)
- [AVDASI 2](AVDASI-2/)
