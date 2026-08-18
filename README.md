# DevOps Documentation

The DevOps Documentation project is the central knowledge base for the
Trapdoor.cloud DevOps team. It captures team procedures, operational
guides, application runbooks, and onboarding material in one
searchable, version-controlled place.

The documentation is written in Markdown and rendered as a static
website with [Material for MkDocs](https://squidfunk.github.io/mkdocs-material/)
using the [zensical](https://pypi.org/project/zensical/) toolchain. The
live site is published at <https://docs.trapdoor.cloud/>.

## Project overview

The repository is laid out as follows:

| Path                    | Description                                             |
| ----------------------- | ------------------------------------------------------- |
| `docs/`                 | Source content for the site                             |
| `docs/docs/`            | About, editing and contributing guides                  |
| `docs/procedure/`       | Team procedures (e.g. Git branching and signing)        |
| `docs/app/`             | Application runbooks (e.g. Ansible)                     |
| `docs/team/`            | Team information and member profiles                    |
| `docs/stylesheets/`     | Custom CSS for the site                                 |
| `overrides/`            | Theme overrides and static templates                    |
| `zensical.toml`         | Site configuration, navigation and plugins              |
| `requirements.txt`      | Python dependencies for building and serving the site   |
| `Dockerfile`            | Container image for serving the site                    |
| `docker-compose.yml`    | Local containerised workflow                            |
| `site/`                 | Generated static output (gitignored, do not edit)       |

## Prerequisites

- Python 3.10 or later (the project tracks the latest Python release)
- `pip` and, for the containerised workflow, Docker

## Getting started

### 1. Create a virtual environment

```bash
python3 -m venv .venv
source .venv/bin/activate
```

### 2. Install the dependencies

```bash
pip install --upgrade pip
pip install -r requirements.txt
```

### 3. Serve the site locally

```bash
zensical serve
```

Then open <http://127.0.0.1:8000/> in your browser. The local server
auto-reloads whenever you save a change, so you can preview edits live.

## Running with Docker

A `Dockerfile` and `docker-compose.yml` are provided for running the
site in a container without polluting your local Python environment:

```bash
docker compose up --build
```

This builds the image, mounts the repository at
`/opt/devops-docs`, and exposes the site on port 8000.

## Building a static export

To generate the static HTML into `site/` for deployment elsewhere:

```bash
zensical build
```

PDF export of the site is also supported and is enabled by setting the
`ENABLE_PDF_EXPORT` environment variable.

## How to contribute

Contributions are very welcome. Everyone who contributes earns a
coffee on the house. There are two ways to make edits:

1. **Web GUI**: simple edits can be made directly from the rendered
   site. This works well for small changes.
2. **Local checkout**: for anything non-trivial, clone the repository,
   edit the Markdown sources, and submit a pull request. This is the
   strongly recommended approach.

Before making changes, please read the [contributing guide](docs/docs/contributing.md)
and the [writing guide](docs/docs/writing/) so your edits match the
existing style and conventions.

New contributors should [request access](mailto:ashley@example.com)
before they can push changes.

## Documentation tips

- Navigate the site via the side navigation bar, or use the search
  bar at the top of the page.
- Diagrams are supported using Mermaid syntax inside fenced code
  blocks.
- See the [CHANGELOG](docs/docs/CHANGELOG.md) for the latest updates
  to the site and its tooling.

## Related links

- Live site: <https://docs.trapdoor.cloud/>
- Source repository: <https://github.com/ashleykleynhans/devops-docs>
