# Repository Organization Standard

**Status:** Initial standard  
**Classification:** Required principles; recommended layouts  
**Applies to:** Repositories using Project Foundation standards and resources

## 1. Purpose

This standard establishes a consistent approach to organizing repositories so projects are understandable, maintainable, testable, secure, and approachable for future contributors.

It defines shared organizational principles and reference layouts. It does not require every project to use an identical directory tree.

A Python application, PowerShell toolkit, Django website, Raspberry Pi application, and infrastructure repository have different needs. Their structures should reflect those needs while preserving common expectations.

## 2. Core Requirements

Repositories MUST:

1. Have a root README that explains the project's purpose, supported environment, setup, usage, testing, and documentation entry points.
2. Separate implementation, tests, documentation, configuration, and generated output when those responsibilities exist.
3. Keep secrets and private environment-specific information out of every commit and every Git ref, including branches, tags, and historical commits.
4. Provide safe example configuration that helps a user configure the project locally without exposing private values.
5. Identify supported platforms, runtimes, and material operational constraints.
6. Document non-obvious setup, build, test, deployment, and maintenance procedures.
7. Avoid committing generated files, caches, local IDE state, build output, or machine-specific files unless there is a documented reason.
8. Keep project-specific decisions and configuration in the consuming repository rather than assuming Project Foundation can determine them centrally.

Repositories SHOULD:

- Group files by responsibility rather than by the person who created them.
- Keep directory nesting understandable and avoid unnecessary layers.
- Use predictable names and consistent casing.
- Include automated tests that mirror the implementation structure where practical.
- Provide a clear separation between reusable code and project-specific entry points.
- Keep architecture and setup documentation close to the code it describes.
- Use a lock file or another reproducible dependency mechanism when supported by the ecosystem.

## 3. Reference Repository Layout

The following is a starting model, not a mandatory directory tree:

    project/
    ├── .github/
    │   ├── ISSUE_TEMPLATE/
    │   ├── workflows/
    │   └── PULL_REQUEST_TEMPLATE.md
    ├── config/
    │   ├── examples/
    │   └── schemas/
    ├── docs/
    ├── scripts/
    ├── src/
    ├── tests/
    ├── examples/
    ├── assets/
    ├── .editorconfig
    ├── .gitignore
    ├── CONTRIBUTING.md
    ├── LICENSE
    └── README.md

Use only the directories a project needs. Do not create empty folders simply to match this illustration.

### Directory responsibilities

| Location | Responsibility |
| --- | --- |
| `.github/` | GitHub-specific configuration, issue/PR templates, and Actions workflows |
| `config/` | Safe defaults, configuration examples, and schemas; local secrets do not belong here |
| `docs/` | User, developer, architecture, deployment, and operational documentation |
| `scripts/` | Developer, build, maintenance, and administrative scripts |
| `src/` | Application or library implementation |
| `tests/` | Automated tests, organized by component or language |
| `examples/` | Safe, self-contained demonstrations and sample input |
| `assets/` | Static resources required by the project |
| `dist/`, `build/`, `coverage/` | Generated output; normally ignored by Git |

A project may use a language ecosystem's conventional layout instead of `src/`. For example, a Python package may use a package directory at the root, and a PowerShell module may use a module-name directory containing its manifest and module files.

## 4. Organizing Multi-Language Projects

Projects containing more than one language SHOULD make language boundaries clear without splitting a single logical feature across arbitrary locations.

A mixed Python and PowerShell project might use:

    project/
    ├── src/
    │   ├── python/
    │   │   └── package_name/
    │   └── powershell/
    │       └── ModuleName/
    ├── tests/
    │   ├── python/
    │   └── powershell/
    ├── config/
    ├── docs/
    ├── scripts/
    └── README.md

This is illustrative. A project may choose another structure when it better fits its packaging, import, module, or deployment conventions.

### One-Click IT Toolkit as a reference

The One-Click IT Toolkit is an important reference because it combines Python and PowerShell, targets Windows, Linux, and macOS, and is designed for offline or air-gapped use.

The repository organization for this type of project should make the following easy to identify:

- Which components are implemented in Python and which are implemented in PowerShell.
- Which tests validate each language and supported operating system.
- Which configuration is safe to commit and which configuration is local to an operator's machine.
- Which resources are bundled with the project and which are optional.
- Which commands perform checks and which commands make system changes.
- Which operations require elevated privileges or explicit operator selection.

The toolkit's offline requirement also demonstrates why build-time automation and runtime behavior must be documented separately. CI may obtain test tooling in its isolated environment, but that must not silently introduce an Internet dependency into the deployed toolkit.

Do not reorganize a working project solely to match the example above. Prefer incremental changes that improve discoverability without disrupting established interfaces or validated behavior.

## 5. Configuration and Local Setup

Configuration MUST be designed so a user can understand how to set up the project without publishing private values.

### 5.1 Separate examples from local configuration

A recommended pattern is:

    config/
    ├── defaults.yaml
    ├── examples/
    │   └── application.example.yaml
    └── schemas/
        └── application.schema.json

For environment variables:

- Commit a `.env.example` containing variable names and clearly fake or placeholder values.
- Ignore the actual `.env` file.
- Document how to copy the example to a local file and populate it.
- Never put real tokens, passwords, private keys, or connection strings in the example.

For local configuration overrides, use a predictable ignored filename such as `config.local.yaml` or `settings.local.json`. Document its precedence and expected schema.

### 5.2 Examples must be useful but synthetic

Examples SHOULD show the shape, type, and purpose of each setting. They MUST NOT contain actual personal, organizational, customer, production, or infrastructure details.

Use values such as:

- `YOUR_DEVICE_ADDRESS`
- `REPLACE_WITH_LOCAL_VALUE`
- `example.invalid`
- `user@example.invalid`
- Reserved documentation IP addresses such as `192.0.2.10`

Do not copy actual logs, screenshots, database records, network diagrams, configuration exports, or command output into public documentation until they have been reviewed and sanitized.

### 5.3 Avoid machine-specific assumptions

Do not hard-code an individual developer's:

- Home directory or username.
- Hostname or device name.
- Internal IP address, subnet, DNS name, or domain.
- Drive letter or mount path.
- Wi-Fi SSID, network details, or service endpoint.
- Account identifier, email address, or organization-specific resource name.

Use configuration, command-line arguments, environment variables, or platform-aware path resolution as appropriate.

### 5.4 Configuration precedence

When a project supports multiple configuration sources, document which source takes precedence.

A common model is:

1. Built-in safe defaults.
2. Project configuration file.
3. Local, ignored configuration override.
4. Environment variables.
5. Explicit command-line arguments.

This is a recommendation, not a universal requirement. A project should use a precedence model that suits its technology and explain it clearly.

Configuration should be validated where practical. Missing required values should produce useful errors rather than silently falling back to unsafe or unintended values.

## 6. Public Repository Privacy and Git History

**This is a required standard for every public repository and every repository intended to become public.**

Private information MUST NOT be committed at any point—not even temporarily, in a feature branch, in a tag, in an old commit, or in a file that is later deleted.

Deleting a file in a later commit does not remove its earlier contents from Git history.

### 6.1 Information that must not be committed

Examples include:

- Passwords, API keys, access tokens, private keys, certificates, and recovery codes.
- Real connection strings or authenticated URLs.
- Personal contact details or private account identifiers.
- Customer, employee, member, or other non-public personal information.
- Internal hostnames, private network maps, production addresses, or sensitive infrastructure details.
- Proprietary configuration, exports, logs, database contents, or screenshots.
- Meeting credentials, private links, access codes, and device-management credentials.
- Any information the owner or responsible organization has not authorized for public release.

This list is not exhaustive. When uncertain, keep the information out of the repository until its publication is explicitly approved.

### 6.2 Treat the entire Git history as public

Before pushing a branch, tag, or repository to a public remote, review the complete set of commits and refs that will be published.

Do not assume that a value is safe because:

- It is no longer present in the current working tree.
- The file is now listed in `.gitignore`.
- The secret was deleted in a later commit.
- The branch is not the default branch.
- The value is believed to be temporary or expired.

A public repository's history should be treated as permanently disclosed. Clones, forks, caches, and references may continue to contain prior commits even after history is rewritten.

### 6.3 If private information is committed

Treat it as an exposure incident:

1. Revoke or rotate the affected credential immediately. Do not rely on deleting the commit.
2. Determine what information was exposed and who or what it may affect.
3. Remove the sensitive content from the repository and, where appropriate, coordinate a history rewrite.
4. Review branches, tags, releases, pull requests, logs, artifacts, and other copies that may retain the information.
5. Confirm the replacement configuration is safe and that the original secret is no longer valid.
6. Document the incident and corrective action without repeating the exposed value.

History rewriting is cleanup, not containment. Credential revocation and impact assessment come first.

### 6.4 Prevention and review

Repositories SHOULD use layered prevention:

- A carefully maintained `.gitignore`.
- Safe example configuration and local-only overrides.
- Secret scanning before pushes and in CI.
- Dependency and code scanning where appropriate.
- Review of staged changes and diffs before committing.
- Review of all refs and history before public release or migration.

Automated scanners reduce risk but do not prove that a repository is safe. Human review remains required.

## 7. GitHub-Specific Organization

GitHub-specific files belong under `.github/`.

GitHub Actions workflow files, including reusable workflows, MUST be stored directly under `.github/workflows/`.

A consuming repository should keep its own caller workflow under its own `.github/workflows/` directory. It chooses when to invoke a shared workflow, which inputs to provide, what permissions to grant, and what additional project-specific jobs to run.

Project Foundation provides reusable building blocks; it does not own the consuming repository's operational configuration.

## 8. Documentation Placement

At minimum, the root README SHOULD answer:

- What does this project do?
- Who or what is it for?
- What platforms and versions are supported?
- How is it installed or configured?
- How is it run?
- How are tests executed?
- Where are detailed guides and troubleshooting instructions?
- What are the security, privacy, and operational constraints?

Use `docs/` for deeper material. Keep the root README useful as an entry point rather than turning it into the entire manual.

## 9. Tests and Generated Files

Tests SHOULD be organized so contributors can identify which component they validate.

Where practical, mirror source boundaries:

    src/
    └── component/

    tests/
    └── component/

Generated output, caches, virtual environments, local databases, temporary files, coverage reports, and IDE state SHOULD be ignored unless they are intentional release assets or required source inputs.

If generated files are committed, document why they are tracked and how they are reproduced.

## 10. Project Independence and Exceptions

Each repository owns its:

- Project-specific directory structure.
- Runtime and build configuration.
- Dependency and version choices.
- CI triggers, inputs, permissions, and required checks.
- Deployment and release process.
- Local setup and operational instructions.

Project Foundation templates and reusable workflows are optional starting points that projects adopt and configure deliberately.

A project may deviate from a recommended layout or practice when its technology or operating environment warrants it. Exceptions to Required standards must be justified and documented, especially where security, privacy, or public disclosure is involved.

## 11. Review Checklist

Before publishing or materially reorganizing a repository, confirm:

- [ ] Root README accurately explains the project and setup.
- [ ] Source, tests, documentation, configuration, and scripts are discoverable.
- [ ] No real secrets or private information exist in the files or the history being published.
- [ ] Local configuration is ignored and safe examples are provided.
- [ ] Examples use synthetic values and do not reveal real infrastructure.
- [ ] Supported platforms, dependencies, and offline/runtime constraints are documented.
- [ ] Generated output and local machine files are excluded unless intentionally tracked.
- [ ] GitHub workflows are stored in supported locations.
- [ ] Project-specific configuration remains owned by the project.
- [ ] Any deviations from Required standards are documented.

## 12. Evolution

This standard will be validated and refined as projects adopt it, beginning with the One-Click IT Toolkit.

Changes should reflect demonstrated needs and should not force disruptive restructuring of stable projects merely to achieve visual uniformity.
