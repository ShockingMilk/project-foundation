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

## Final Principle

Project Foundation should grow through demonstrated experience.

**A good standard makes development easier, not harder.**
