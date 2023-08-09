# Notebooks Now! Submission Template

[![Made with MyST](https://img.shields.io/badge/made%20with-myst-orange)](https://franklin-notebooks_now_myst_lite.curve.space)
[![Binder](https://mybinder.org/badge_logo.svg)](https://mybinder.org/v2/gh/Notebooks-Now/submission-myst-lite/HEAD?labpath=article.ipynb)

This submission template is for a simple notebook-based publication with one source file, supporting data, bibliography, and MyST build configuration.

## Source file

The source file for this template is a Jupyter notebook. There is not necessarily anything special about this notebook. It may contain markdown cells, code cells, and outputs from common Python packages, including pandas, matplotlib, plotly, seaborn, and altair. Specific markdown cells may be tagged in their metadata as `"part": "abstract"`, or `"part": "availability"` - these cells will be extracted from the document and included as the specified part in the built output.

## Supporting material

### Supplementary data

By convention, all data should be saved in `data/` directory. There is nothing magic about this directory; references to your data from your notebook must still specify the correct relative path.

### Supplementary images

Similar to the `data/` directory, images for figures should be specified in `images/` directory.

### Bibliography

Bibliography entries may be specified two ways, both described in the [MyST docs](https://myst-tools.org/docs/mystjs/citations). They may be listed explicitly in bibtex format, by convention in the file `references.bib`, and referenced by key using a `cite` MyST role. They may also be specified as inline DOI links. These do not require full bibliographic information; the data is fetched implicitly on build from the DOI.

## MyST configuration

A `myst.yml` file must be provided to configure notebook metadata and exports. This includes authors, affiliations, licenses, keywords, and [much more](https://myst-tools.org/docs/mystjs/frontmatter).

## Building output artfiacts

To build PDF/JATS output from your source data, you must have the MyST CLI installed

```
npm install myst-cli
```

Then build all exports defined in the `myst.yml` file:

```
myst build --all
```

## Dependency management

Please use `pip` and `pip-compile` for dependency management and virtual environment configuration. The `pip-compile` workflow results in fine-grained, pinned dependencies that improves the lifetime of a submission.

To manage your dependencies, edit the `requirements.in` file, adding high level packages there, pin those packages only if necessary for your case.

Then in the same folder ad `requirements.in` run `pip-compile`. This will update or create the `requirements.txt` file with pinned dependencies. The latest versions of `requirements.in` and `requirements.txt` should be commited to the repository.

Then setup your virtual environment as normal:

```bash
python -n venv env
source env/bin/activate
python -m pip install -r requirements.txt
```

### Installing `pip-compile`

We recommand installing `pip-compile` in your base python environment, not in your reproducible execution environment.
