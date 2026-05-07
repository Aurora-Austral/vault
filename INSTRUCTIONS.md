# AI Development Instructions for Aurora Vault

To maintain the security and architectural integrity of the Aurora Vault, all AI agents must follow these strict rules when working on or creating packages.

## 1. Syntax Compliance (Austral 0.2.0)
The Austral compiler is strict. Do not use outdated syntax.
- **References**: Must be `&[Type, Region]`.
- **Dereferencing**: Use `->` for field access on references (e.g., `ref->value`). Do not use `!` for record fields.
- **Destructuring**: Use the `as` keyword: `let { field as local: Type } := record;`.
- **Records**: Close with `end;` (not `end record;`).
- **Unit**: Functions returning `Unit` must explicitly `return nil;`.

## 2. Linearity & Capabilities
- **No Leaks**: Every linear type created must be consumed (destroyed or moved).
- **Root Capability**: Tests must always surrender the root capability: `surrenderRoot(root)`.
- **Explicitness**: Be explicit about state transitions.

## 3. Project Structure
- Always work within the `packages/vault/` directory.
- Every package **MUST** have a `Makefile` with a `test` target.
- Documentation in the package root must be in **English**.
- Detailed technical docs or translations go into the `docs/` folder.

## 4. Compilation Workflow
Always use the comma-delimited module list:
`austral compile interface.aui,implementation.aum test_file.aum ...`

## 5. Prohibited Actions
- Do not use `String` for payloads in tests unless verified (use `Nat64` as a stable fallback).
- Do not use dots in module names (e.g., use `module dpop` instead of `module DPoP.Token`).
- Do not ignore build artifacts (ensure they are covered by `.gitignore`).
