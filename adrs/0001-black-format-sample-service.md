# ADR-0001: Black-format sample_service code

## Name

ADR-0001: Black-format sample_service code

## Current Version

1 - Snapshot

## Current state

Idea

## Decision groups

Sample working group

## Problem/issue

Currently code within the sample_service is not formatted in any deterministic manner, but rather depending on each developer's whims. In addition, the current production version of `kb_sdk` generates improperly formatted code.

This leads to formatting conventions across the files.

For developers, lack of uniform formatting creates friction. Modern IDEs will show errors for source code which does not comply with at least the minimal formatting requirements, which makes it difficult to spot actual code errors.

For the service itself, this can lead to stealth bugs which slip through review since strict linting cannot be applied.

For working together, this can create unnecessarily large diffs in commits if users do format the code, since their formatting conventions may be different than other developers.

## Decision

> No decision yet

## Alternatives

### Use flake8 with configuration

The `flake8` Python library enforces `pep8` rules as well as formatting conventions. For consistent formatting across developers it requires a configuration, which chooses specific code and formatting rules. Since the flake8 default rules change over time, for consistent formatting one must use such a configuration ruleset.

## Arguments

The `black` Python library and tool is an "opinionated" set of coding practice and formatting rules. Underneath, it utilizes `flake8`. It has very few options to control those rules. That, in fact, is the point of `black` - to create a single ruleset that can be shared within and across projects in order to create uniform formatting.

Counter-arguments to using `black`:

- `black` formatting is not aesthetically pleasing to all KBase developers

An alternative, using `flake8` with a custom ruleset, would provide similar benefits.

Counter-arguments to using `flake8`:

- would require an effort to create an organization-wide ruleset
- would require support for providing it to all kbase developers (e.g. repo)
- would require enforcement in all codebases
- some codebases in KBase already enforce black-formatting

## Related Decisions

> At this time, there are no related decisions

## History

| Stakeholder  | Role      | Date       | Action    | Status    | Iteration |
|--------------|-----------|------------|-----------|-----------|-----------|
| Erik Pearson | Architect | 2022-01-26 | Formulate | Tentative | ??        |

## References

- [black](https://github.com/psf/black)
- [flake8](https://github.com/PyCQA/flake8)
- [pep8](https://pep8.org)