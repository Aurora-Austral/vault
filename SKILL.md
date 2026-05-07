# Skill: Aurora Vault Package Creation

This skill enables an agent to architect, implement, and validate a new secure package for the Aurora Vault ecosystem using Austral 0.2.0.

## Objective
Create a standardized, linear-typed, and memory-safe package that follows the Aurora Austral architectural patterns.

## Execution Steps

### 1. Initialization
- Create a directory in `packages/vault/[package-name]`.
- Identify the core linear resource and its lifecycle (Creation -> Usage -> Destruction).

### 2. Interface Definition (`.aui`)
- Define the module: `module [name] is ... end.`.
- Declare linear types: `type [Resource]: Linear`.
- Use correct reference syntax: `&[Type, Region]`.

### 3. Implementation (`.aum`)
- Implement constructors and destructors.
- Use the `->` operator for field access via references.
- Use `let { field as local: Type } := value` for destructuring.
- Ensure all linear resources are consumed exactly once.

### 4. Validation (`.test.aum`)
- Create a `main` function that requests `RootCapability`.
- Perform lifecycle tests (Create, Use, Destroy).
- **Mandatory**: Call `surrenderRoot(root)` before exiting.
- Print test results using `printLn`.

### 5. Automation (`Makefile`)
- Implement a `test` target using the comma-separated module syntax:
  `austral compile interface.aui,body.aum test.aum --entrypoint=mod_test:main --output=test_exec`

### 6. Documentation
- Create `README.md` in English following the project template.
- Create `docs/pt.md` with detailed Portuguese documentation.

## Success Criteria
- The package compiles without linearity or region errors.
- `make test` executes successfully.
- Documentation strictly follows the Aurora standards.
