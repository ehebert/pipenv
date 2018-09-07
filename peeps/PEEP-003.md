# PEEP-003: Support Minimal Version Selection

Pipenv will provide optional support for minimal version selection.

☤

As an alternative to the existing version selection strategy, which finds
the maximal dependency that satisifes the dependency constraints, Pipenv
will provide optional support for minimal version selection.

## Comparison of Strategies

Consider a project `spam` which has defined the following dependencies:
- `ham>=1.1`
- `eggs>1.0<3.0`

The available versions for `ham` are `[1.0, 1.1, 1.2]`
The available versions for `eggs` ar `[1.0, 2.0, 2.5, 3.0]`

### Maximal

Maximal version selection would choose the greatest available, which satisifies
constraints, for each dependency:
- `ham` :: `1.2`
- `eggs` :: `2.5`

### Minimal

Minimal version selection would choose the least available for each project, which
satisifies constraints, for each dependency.
- `ham` :: `1.1`
- `eggs` :: `2.0`

## Configuration

The version selection strategy will be set by an environment variable,
`PIPENV_SELECTION_STRATEGY`.

The options for `PIPENV_SELECT_STRATEGY` will be:
- `maximal`, the existing dependency resoultion. This will be the default value.
- `minimal`
