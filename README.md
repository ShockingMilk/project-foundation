# Project Foundation

**ShockingMilk Development Standards & Resources**

*Build consistently. Develop confidently. Improve continuously.*

## Overview

Project Foundation provides shared development standards, resources, templates, and automation. It is intended to help projects establish consistent engineering practices without requiring them to share an identical architecture or repository structure.

Each project remains responsible for adopting and adapting these resources to meet its own technical and operational requirements.

## Purpose

Project Foundation exists to:

- Establish consistent development and documentation practices.
- Provide reusable repository structures and project templates.
- Centralize common development standards and conventions.
- Share reusable GitHub Actions workflows and automation.
- Encourage modular, maintainable, and testable architecture.
- Improve project onboarding and long-term maintainability.
- Reduce duplicated effort across projects.

## Repository Contents

| Directory | Purpose |
| --- | --- |
| `.github/` | GitHub templates and repository configuration |
| `docs/` | Project guidance and foundational documentation |
| `standards/` | Shared development and engineering standards |
| `templates/` | Reusable repository and technology-specific templates |
| `workflows/` | Reusable GitHub Actions workflows |
| `examples/` | Demonstrations and reference implementations |

The repository will evolve as standards and reusable resources are established through actual project development.

### Workflows

The root-level `workflows/` directory contains workflow examples, reference material, and supporting documentation.

Reusable GitHub Actions workflows intended for direct use by other repositories are maintained under `.github/workflows/`.

Consuming repositories retain their own workflow configuration, triggers, permissions, secrets, and project-specific execution requirements.

## Guiding Principles

1. **Consistency without unnecessary restriction** — Share common practices without forcing unrelated projects into identical structures.
2. **Modularity** — Keep responsibilities separated and components understandable.
3. **Maintainability** — Favor solutions that can be understood and maintained by someone other than the original developer.
4. **Practicality** — Prefer solutions that solve real problems over unnecessary complexity.
5. **Security** — Treat security, privacy, and safe configuration as foundational requirements.
6. **Documentation** — Make projects understandable, usable, and supportable.
7. **Continuous improvement** — Standards should evolve as experience identifies better approaches.

## Standards Classification

Guidance in Project Foundation will generally be classified as:

- **Required:** Expected practices across projects unless a documented exception is justified.
- **Recommended:** Preferred practices that can be adapted to individual project requirements.

Technology-specific standards may establish additional requirements where appropriate.

## Getting Started

If you're starting a new project:

1. Review the foundational standards.
2. Select the appropriate repository or technology template.
3. Adapt the structure to the project's actual requirements.
4. Configure testing and automation.
5. Document project-specific decisions and exceptions.

Start with:

- [Vision and Scope](docs/vision-and-scope.md)
- [Contributing](CONTRIBUTING.md)
- [Repository Organization](standards/repository-organization.md) *(planned)*

## Development Ecosystem

Project Foundation supports multiple independent projects, including:

- One-Click IT Toolkit
- AstroLab
- Meetinghouse Broadcast
- Meetinghouse Technology
- AD Cleanup
- Cluster

These projects are independent. Project Foundation provides shared guidance and resources rather than becoming a dependency that every project must have available at runtime.

## Licensing

Project Foundation uses a dual-license approach to make its resources reusable while respecting the different purposes of software and documentation.

- **Software and executable resources:** MIT License
- **Documentation, written standards, and educational material:** Creative Commons Attribution 4.0 International (CC BY 4.0)

See the [LICENSE](LICENSE) file for an explanation of which license applies to each type of material.

Third-party material may be subject to separate licensing terms. Always review applicable notices before reusing third-party resources.

## Contributing

Contributions, suggestions, and improvements are welcome.

See [CONTRIBUTING.md](CONTRIBUTING.md) for guidance on proposing changes and maintaining shared standards.

## Philosophy

Project Foundation is intended to be a practical development resource, not a rigid framework or corporate standard.

Its purpose is simple:

**Build things well. Make them understandable. Leave them better than you found them.**
