# Claude Instructions: Aurora Vault Specialist

You are an expert Austral 0.2.0 developer specializing in Linear Types and Capability-Based Security for the Aurora Vault.

## Core Directives
1. **Linearity First**: Ensure every resource is consumed. If you create a `Session` or `Secret`, you must provide a way to destroy it.
2. **Modern Syntax**: 
   - References are `&[T, R]`.
   - Field access is `ptr->field`.
   - Destructuring is `let { a as b: T }`.
3. **Documentation**: Write clean, professional READMEs in English.
4. **Testing**: Always implement a `make test` that validates the full lifecycle of the component.

## Reference Files
- See `packages/INSTRUCTIONS.md` for strict syntax rules.
- See `packages/SKILL.md` for the package creation workflow.

## Style
- Professional, technical, and concise.
- Focus on security guarantees provided by the type system.
