# Contributing to Project Foundation

## Purpose

Project Foundation is intended to evolve through practical experience.

Contributions should improve the quality, consistency, usability, and maintainability of the shared development ecosystem.

This document describes how changes should be proposed, reviewed, and incorporated.

## Contribution Principles

Contributions should follow these principles:

- Solve a real problem or provide a clear improvement.
- Favor simplicity over unnecessary complexity.
- Preserve flexibility across different project types.
- Include documentation when introducing or changing standards.
- Avoid introducing dependencies without a clear justification.
- Consider backward compatibility when changing shared resources.
- Prefer reusable solutions when multiple projects can benefit.

## Privacy and Sensitive Information

Project Foundation and its associated resources are intended for public reuse. Contributors must ensure that private, confidential, and sensitive information is never introduced into public repository history.

This requirement applies to all commits, branches, tags, releases, pull requests, and other published repository artifacts.

### Never commit

Examples of information that must not be committed include:

- Passwords, API keys, access tokens, private keys, and certificates.
- Personal information, account identifiers, and private email addresses.
- Internal hostnames, private network details, and production infrastructure information.
- Private URLs, internal service endpoints, and organization-specific configuration.
- Database exports, logs, screenshots, or diagnostic output containing sensitive information.
- Usernames, home-directory paths, or other identifying local system details when they are not intended for publication.

### Use safe examples

Contributors should use placeholders or synthetic values in examples and templates.

Examples:

- `YOUR_DEVICE_ADDRESS`
- `REPLACE_WITH_LOCAL_VALUE`
- `user@example.invalid`
- `https://example.invalid`
- `192.0.2.10`

Use environment variables, ignored local configuration files, or other appropriate mechanisms for values that must remain private.

### Git history requirements

Removing sensitive information in a later commit does not remove it from earlier commits.

Contributors must review changes before publication and ensure sensitive information is not introduced into repository history.

If sensitive information is accidentally committed or published:

1. Immediately revoke or rotate affected credentials.
2. Assess what information was exposed and where it may have been published.
3. Remove the sensitive information from affected files and repository history as appropriate.
4. Review branches, tags, releases, pull requests, and other published artifacts.
5. Document the incident without reproducing the exposed information.

History rewriting is a cleanup measure, not a substitute for rotating exposed credentials.

### Prevention

Contributors should use:

- Appropriate `.gitignore` rules.
- Safe example configuration files.
- Secret scanning and automated checks where available.
- Diff and commit review before pushing.
- Sanitization of logs, screenshots, exports, and diagnostic material.

Automated scanning is an additional safeguard, not a replacement for human review.

**When in doubt, do not commit or publish the information.**

## Types of Contributions

Contributions may include:

- New or revised development standards.
- Repository and technology templates.
- GitHub Actions workflows.
- Documentation and examples.
- Testing improvements.
- Security recommendations.
- Corrections to existing guidance.
- Lessons learned from individual projects.

## Proposed Change Process

### 1. Identify the Need

Before introducing a new standard or shared resource, identify:

- What problem does it solve?
- Which projects benefit?
- Is it universally applicable or technology-specific?
- Does an existing standard already address it?
- What maintenance responsibilities will it introduce?

### 2. Propose the Change

Significant changes should be documented in an issue or pull request.

Include:

- The problem or opportunity.
- The proposed solution.
- Expected benefits.
- Potential drawbacks or compatibility concerns.
- Projects that may be affected.

Small corrections and straightforward improvements do not require extensive proposals.

### 3. Implement the Change

Changes should be:

- Focused and appropriately scoped.
- Consistent with established standards.
- Documented where necessary.
- Tested when executable functionality is involved.

For reusable workflows, templates, and scripts, include examples or validation where practical.

### 4. Review and Validate

Before accepting a change, consider:

- Does it solve the identified problem?
- Is it understandable to someone unfamiliar with the project?
- Does it introduce unnecessary complexity?
- Is it compatible with existing projects?
- Does the documentation accurately describe its behavior?
- Are security implications understood?

### 5. Incorporate Lessons Learned

Changes developed while working on individual projects should be evaluated for broader applicability.

Not every project-specific solution belongs in Project Foundation.

Promote a solution to a shared standard or reusable resource when it has demonstrated value beyond its original project.

## Standards and Exceptions

Standards are classified as either Required or Recommended.

Projects may need to deviate from shared guidance because of technical limitations, security requirements, deployment environments, or other legitimate constraints.

Exceptions should:

- Have a clear justification.
- Identify the affected standard.
- Document relevant risks or trade-offs.
- Be revisited if circumstances change.

An exception should not automatically become a new shared standard.

## Versioning Shared Resources

Changes to shared resources should consider their impact on consuming projects.

Where compatibility matters:

- Use versioned releases or tags.
- Document breaking changes.
- Avoid silently changing the behavior of established reusable workflows.
- Allow consuming projects to adopt updates deliberately.

## Documentation Expectations

Documentation should be:

- Clear and practical.
- Written for its intended audience.
- Updated alongside the functionality or standard it describes.
- Consistent with the actual implementation.

Prefer examples that demonstrate real usage over abstract descriptions.

## Licensing Contributions

By submitting a contribution, you confirm that you have the right to submit the material and that it does not knowingly violate another party's intellectual property rights.

Unless a contribution explicitly identifies different licensing terms and those terms are accepted by the project maintainer, contributions will be distributed under the license applicable to the contributed material:

- Software, scripts, workflows, and executable resources: MIT License.
- Documentation, written standards, and educational material: CC BY 4.0.

Contributions must preserve applicable third-party copyright and licensing notices.

If you are unsure which license applies to a contribution, discuss it with the maintainer before submitting it.

## Final Principle

Project Foundation should grow through demonstrated experience.

**A good standard makes development easier, not harder.**
