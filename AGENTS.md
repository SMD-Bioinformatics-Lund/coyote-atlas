# Coyote Atlas repository instructions

Atlas owns reviewed HGNC/VEP reference bundles, their manifests, validation and
optional API publication. Clinical contracts belong to Coyote Core. The Coyote
application owns database initialization, authentication, authorization and audit.

- Preserve bundle identities, source notices, record counts and SHA-256 checksums.
  Never replace a released bundle in place. Reference updates need reviewed source
  evidence and a new bundle identity.
- Base commands must work without the server, database or reporting dependencies.
  Optional API routes use the server's existing permissions and repositories.
  Importing Atlas or starting the application never installs reference records.
- Keep Python code typed, follow Ruff conventions and document real behavior.
  Reuse Core contracts and keep its standalone dependency pinned to a reviewed commit.
- Use synthetic fixtures and mocked transports. Tests must not contact databases,
  brokers or application deployments. Run affected tests and the smoke suite;
  check a built wheel's bundle before releasing it.
- Preserve the README layout, badges, logo, documentation structure and public
  interfaces unless their change is explicitly requested. The application's
  scripts/branding/generate_logos.py remains the shared logo blueprint; do not
  add another generator here.
- Use repository-relative paths. Keep credentials, private exports and temporary
  development files out of source control. Operate only within this checkout and
  resources explicitly authorized for the task.
- Develop on focused branches from dev. Main is reserved for approved releases.
  Changelog headings, release names and tags use vMAJOR.MINOR.PATCH; package
  metadata uses the unprefixed version. Do not publish to PyPI or merge into main
  without explicit approval.
- Preserve GPL-3.0-only and all reference-data notices. GitHub changes require
  authorization. Deployment-server access remains explicitly authorized and read-only.
