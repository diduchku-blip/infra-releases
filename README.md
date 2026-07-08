# Infra — Version Registry

Public update registry for **Infra**, the self-hosted Operational Governance Platform.

Each Infra instance checks this registry for available updates (Admin Settings → Updates → "Check for updates"). No instance data ever flows here — instances only **read** `registry.json`.

## Registry URL

```
https://raw.githubusercontent.com/diduchku-blip/infra-releases/main/registry.json
```

Set this as `VERSION_CHECK_URL` at build/deploy time, or paste it into an instance's Admin Settings as the version-check URL override.

## Format

```json
{
  "version": "0.2.0",
  "releaseNotes": "What changed…",
  "downloadUrl": "optional link to the release artifact"
}
```

- `version` — semver of the latest published release. Instances compare against their own current version.
- `releaseNotes` — shown to the instance operator in the update banner (optional).
- `downloadUrl` — where to obtain the release, e.g. a Docker image reference (optional).

## Publishing a release

1. Ship the release (deploy / publish the image).
2. Edit `registry.json`: bump `version`, rewrite `releaseNotes`.
3. Commit to `main`. Instances pick it up on their next check.

Release history = this file's commit history.
