# GitHub Actions Toolkit

A centralized toolkit of reusable GitHub Actions and workflows for `sm-techlabs` projects.

This repository helps standardize CI/CD tasks across multiple repositories by offering
versioned composite actions, reusable workflows, and helper scripts.

---

## 📁 Structure

```bash
github-actions-toolkit/
├── .github/
│   └── workflows/      # Reusable workflows (must live here)
├── actions/            # Composite actions
├── scripts/            # Helper shell scripts
└── README.md
```

---

## 🧱 Components

### Composite Actions

| Name             | Description                                 |
|------------------|---------------------------------------------|
| `connect-to-oci` | Sets up OCI authentication for workflows    |

### Reusable Workflows

| Name           | Description                      |
|----------------|----------------------------------|
| _(coming soon)_| Common workflows (build, deploy) |

---

## ⚙️ Usage

### Using a Composite Action

```yaml
steps:
  - uses: sm-techlabs/github-actions-toolkit/actions/connect-to-oci@main
```

> Ensure required secrets like `OCI_CONFIG_FILE` and `OCI_PRIVATE_KEY` are available.

### Using a Reusable Workflow

```yaml
jobs:
  setup:
    uses: sm-techlabs/github-actions-toolkit/.github/workflows/my-workflow.yml@v1
    with:
      some-input: value
    secrets:
      my-secret: ${{ secrets.MY_SECRET }}
```

---

## 🔐 Secrets & Security

- Store secrets in the `sm-techlabs` **organization** to avoid duplication.
- Secrets should be rotated periodically (especially private keys and fingerprints).
- The action will fail if configuration is missing or invalid.

---

## Versioning and Usage

This repository uses [semantic versioning](https://semver.org/) with automated releases managed by GitHub Actions and [go-semantic-release](https://github.com/go-semantic-release/semantic-release).

- The entire repository is versioned as a single unit.
- Tags are created automatically in the form `vX.Y.Z` on merges to `main`.
- To use an action or workflow at a stable version, reference the tag prefix:

```yaml
uses: sm-techlabs/github-actions-toolkit/actions/connect-to-oci@v1
```
---

## 🤝 Contributing

We welcome internal contributions to expand the toolkit:

- Add new reusable workflows or actions
- Follow best practices and keep scripts clean
- Test thoroughly before merging to `main`

---

## 📬 Contact

For questions or issues, open an issue or reach out to a member of `sm-techlabs`.
