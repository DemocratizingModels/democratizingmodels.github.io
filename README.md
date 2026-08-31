# DEMOS Website

This repository contains the source code for the [DEMOS website](https://democratizing-models.github.io/).

DEMOS — **Democratizing Models** — develops and supports an open ecosystem for the exchange, preservation, and reuse of scientific models across disciplines.

The website is built with [MkDocs](https://www.mkdocs.org/) using the [Material for MkDocs](https://squidfunk.github.io/mkdocs-material/) theme. Dependencies and development tasks are managed with [Pixi](https://pixi.sh/).

## Repository structure

```text
.
├── .github/workflows/   # CI and GitHub Pages deployment
├── docs/                # Website content and assets
├── mkdocs.yml           # MkDocs configuration
├── pixi.toml            # Dependencies and development tasks
└── pixi.lock            # Locked development environment
```

The website is available in English and German. The language configuration, navigation, theme, plugins, and other site-wide settings are defined in `mkdocs.yml`.

## Local development

### Prerequisites

Install [Pixi](https://pixi.sh/).

All other dependencies are installed automatically from `pixi.toml` and `pixi.lock`.

### Serve the website locally

```bash
pixi run serve
```

The development server is available at:

```text
http://localhost:8000
```

Changes to the documentation are automatically picked up by MkDocs.

### Build the website

```bash
pixi run build
```

The generated static website is written to `site/`.

### Validate the website

To perform the same build and link checks used in CI:

```bash
pixi run build-check
```

This performs a strict MkDocs build and checks links in the generated website.

## Contributing

Website content lives in `docs/`.

For ordinary content changes:

1. create a branch,
2. edit or add the corresponding Markdown files,
3. run `pixi run serve` to inspect the result locally,
4. run `pixi run build-check` before submitting the changes,
5. open a pull request against `main`.

Pull requests are built and validated by GitHub Actions, but the public website is deployed only after changes have been merged into `main`.

## Deployment

The website is hosted using GitHub Pages.

The GitHub Actions workflow in `.github/workflows/docs.yml` validates pull requests targeting `main` and pushes to `main`. Deployment to GitHub Pages is performed only for pushes to the `main` branch.

## License

This repository is distributed under the [MIT License](LICENSE.md).
