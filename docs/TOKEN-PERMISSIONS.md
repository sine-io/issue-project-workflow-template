# Token permissions

## Issues only

Use the repository `GITHUB_TOKEN` with workflow permission `issues: write`, or a PAT with target repository `Issues: Read and write`.

## Issues and organization Project

Use a PAT stored as the repository or organization Actions secret `PROJECT_TOKEN`.

Fine-grained PAT permissions:

- Repository access: the target repository.
- Repository permissions: `Issues: Read and write`, `Metadata: Read`.
- Organization permissions: `Projects: Read and write`.

Classic PAT scopes:

- `project`.
- `repo` when the target repository is private.

Secrets are not copied when a repository is generated from this template. Configure `PROJECT_TOKEN` on every new repository, or expose one organization secret to selected repositories.

GitHub can create a Project and then return `Resource not accessible by personal access token` when the token cannot read the created node. Do not repeatedly retry Project creation with the same under-scoped token. Grant the permission, inspect the organization Project list, and rerun; the bootstrap script reuses a matching title.
