# Installation

Atlas requires Python 3.12 or newer. Its base installation includes the reviewed
Core library and HTTPX; it does not install the Coyote server or connect to a database.

## Use this checkout

From the Atlas repository root:

```bash
uv venv
uv pip install -e .
.venv/bin/coyote-atlas inspect
.venv/bin/coyote-atlas validate
```

The Core Git dependency selects an exact application commit and its `core`
subdirectory. No Coyote package needs to be published to PyPI for this installation.
`inspect` displays bundle identity and datasets; `validate` checks resource
integrity and contracts. Neither command needs a running application.

## Install reviewed wheels

Use an organization-provided wheel set with Atlas and its reviewed Core and
third-party dependencies. Install that dependency set first, then the Atlas wheel:

```bash
python -m pip install --no-deps /path/to/wheels/coyote_atlas-1.0.0-py3-none-any.whl
python -m pip check
coyote-atlas inspect
coyote-atlas validate
```

The package carries its reference data. The current working directory does not
select a different reference source.

## Add Atlas to a server

The standard Coyote application includes an explicitly pinned Atlas artifact.
For a separately installed server, install the matching reviewed Atlas wheel into
its environment and restart the API through the normal deployment procedure.
The optional `api` extra declares the server dependency for package resolvers;
unpublished server artifacts must come from the reviewed application release.

The server discovers the `coyote.api.routers` and `coyote.reference_bundles` entry
points. Installation makes reference routes available; it does not populate or
replace database records. Follow [usage](usage.md) for explicit reference installation.
