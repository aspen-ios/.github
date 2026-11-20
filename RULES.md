# Rust Development Rules & Engineering Standards

## 1. File Size and Organization

- Every Rust source file must contain a minimum of 10 lines and a maximum of 200 lines.
- Each source file must have a single, clearly defined responsibility.
- Split large implementations into smaller, independent, logically organized modules.
- Never compress code, remove meaningful whitespace, or sacrifice readability to satisfy file size limits.
- Avoid unnecessary files created solely to satisfy minimum line requirements.
- Maintain consistent file organization throughout the project.
- Do not create artificial abstractions or meaningless modules to satisfy structural restrictions.
- Preserve Rust and Cargo conventions whenever they conflict with arbitrary organization preferences.

## 2. Architecture and Modularity

- Follow architectural principles inspired by LLVM, the Linux Kernel, GRUB, and Unreal Engine 5.
- Design the codebase around highly modular, scalable, maintainable, and reusable components.
- Use Rust's `struct`, `enum`, `trait`, and `impl` constructs to establish explicit responsibilities and well-defined abstractions.
- Prefer strongly typed structures, clear interfaces, and explicit data flow.
- Separate components according to their responsibilities, functionality, and abstraction levels.
- Favor composition over unnecessary inheritance-like patterns or excessive abstraction.
- Follow Rust's ownership, borrowing, lifetime, and type-safety principles.
- Avoid monolithic implementations, excessive coupling, circular dependencies, and unnecessary dependencies.
- Create new types and modules only when they provide meaningful separation of responsibilities.
- Avoid introducing abstractions solely to increase the number of structures or modules.
- Maintain clear boundaries between platform-independent and platform-specific components.

## 3. Directory Structure

- Each directory must contain no more than 4 files.
- Create meaningful subdirectories to organize components, subsystems, and related functionality.
- Group related modules together while maintaining clear architectural boundaries.
- Keep directory hierarchies predictable, consistent, and easy to navigate.
- Place integration tests in dedicated test directories, separate from production source files.
- Keep unit tests separate from production logic whenever practical.
- Use Rust's module system to establish a clean, structured project hierarchy.
- Avoid unnecessary nesting, excessive fragmentation, and directories without meaningful responsibilities.
- Preserve mandatory Rust and Cargo files even when their names or locations require exceptions to project naming rules.
- Do not violate required Cargo project structure to satisfy arbitrary directory limits.

## 4. Naming Conventions

- Use PascalCase for structs, enums, traits, type aliases, constants, and static values.
- Use snake_case for functions, methods, local variables, fields, and Rust module identifiers.
- Avoid SCREAMING_SNAKE_CASE for constants and static values.
- Prefer PascalCase for constants to maintain a consistent Unreal Engine-inspired naming style.
- Use complete, descriptive English words instead of abbreviations or shortened identifiers.
- For example, use `integrity` instead of `integ`, and `configuration` instead of `config`.
- File and directory names must never contain hyphens or underscores unless required by Rust or Cargo conventions.
- Never sacrifice readability or clarity to shorten an identifier.
- Maintain consistent naming conventions across the entire project.

### Required Constant Naming Configuration

Add the following crate-level attribute at the beginning of every applicable Rust crate root:

```rust
#![allow(non_upper_case_globals)]
```

- This attribute is mandatory for crates following these naming rules.
- Constants and static values must use PascalCase instead of SCREAMING_SNAKE_CASE.
- Do not suppress unrelated compiler warnings or Clippy diagnostics.
- Keep all other Rust lint checks enabled unless a specific exception is justified.

## 5. Language Requirements

- English is mandatory throughout the entire codebase.
- All identifiers, modules, types, functions, variables, constants, and named components must use English.
- All error messages, logging output, diagnostic messages, and user-facing strings must be written in English.
- All technical documentation, implementation plans, code reviews, and validation reports must use English.
- Never mix languages within the project.
- Preserve externally required protocol identifiers, binary signatures, and standardized technical terminology.

## 6. Code Readability and Formatting

- Code must be self-explanatory through meaningful names, clear structure, and explicit responsibilities.
- Use whitespace and logical spacing to improve readability.
- Keep functions concise, focused, and easy to understand.
- Avoid cryptic abbreviations, single-letter identifiers outside conventional short scopes, and unclear naming.
- Prefer explicit, understandable implementations over unnecessarily clever or compact code.
- Maintain consistent formatting using `rustfmt`.
- Avoid deeply nested control flow when simpler alternatives are available.
- Separate logically distinct operations to improve readability.
- Never introduce unnecessary formatting complexity.
- Never compress implementations to satisfy file size limits.

## 7. Coding Style and Design Philosophy

- Adopt a 2018-era systems programming philosophy, combining explicit architecture, predictable behavior, and disciplined engineering.
- Draw inspiration from LLVM, Linux, GRUB, and Unreal Engine 5 for subsystem organization and architectural clarity.
- Prioritize deterministic behavior, performance, reliability, and long-term maintainability.
- Favor explicit control flow, well-defined component boundaries, and predictable execution.
- Minimize unnecessary runtime overhead, hidden complexity, and implicit behavior.
- Prefer zero-cost abstractions and compile-time guarantees whenever practical.
- Avoid excessive abstraction layers, unnecessary design patterns, and overengineering.
- Use modern, stable Rust features when they improve safety, clarity, or maintainability.
- Favor simple, efficient implementations with clearly defined responsibilities.

## 8. Implementation Completeness

- Never introduce placeholders, dummy implementations, fake functionality, or fabricated results.
- Do not create empty functions, artificial return values, or incomplete implementations presented as working code.
- Every implemented feature must provide genuine, functional behavior.
- Do not simulate functionality when a real implementation is required.
- Never silently ignore errors or return misleading success results.
- Avoid unfinished code paths disguised as complete implementations.
- Do not introduce `todo!()`, `unimplemented!()`, or `unreachable!()` as substitutes for missing functionality.
- If a feature cannot be fully implemented, clearly identify the limitation instead of disguising it.
- Never claim that functionality works unless it has been properly implemented and, where practical, verified.

## 9. Error Handling and Reliability

- Use explicit, predictable, and type-safe error handling.
- Prefer `Result` and `Option` over panic-based control flow.
- Avoid unnecessary use of `unwrap()` and `expect()` in production code.
- Propagate errors appropriately while preserving useful diagnostic information.
- Never suppress, discard, or silently ignore meaningful errors.
- Handle edge cases and invalid states explicitly.
- Use Rust's type system to prevent invalid states whenever practical.
- Keep error handling consistent across related modules and subsystems.
- Never convert failures into misleading success results.
- Avoid arbitrary fallback values when required information is unavailable.

## 10. Performance and Resource Management

- Prioritize predictable performance and efficient resource usage.
- Avoid unnecessary heap allocations, redundant copies, and excessive cloning.
- Prefer borrowing and references when ownership transfer is unnecessary.
- Use stack allocation when appropriate and practical.
- Avoid unnecessary dynamic dispatch when static dispatch is sufficient.
- Keep memory ownership explicit and resource lifetimes predictable.
- Optimize performance-critical paths based on measurable evidence rather than assumptions.
- Never compromise correctness or maintainability for speculative optimizations.
- Avoid unnecessary synchronization, indirection, and allocation overhead.

## 11. Testing and Validation

- Keep tests organized in dedicated directories, separate from production source files whenever practical.
- Write meaningful tests that validate real functionality and expected behavior.
- Avoid fake tests, artificial assertions, and tests that do not verify useful behavior.
- Cover important edge cases, error conditions, and subsystem boundaries.
- Ensure that tests remain independent, deterministic, and maintainable.
- Validate code using the Rust compiler, `cargo test`, `cargo fmt`, and `cargo clippy` when applicable.
- Never claim that tests pass unless they have actually been executed successfully.
- Do not modify production behavior solely to make an incorrect test pass.
- Validate platform-specific implementations on representative supported targets whenever possible.

## 12. Quality and Consistency

- Apply these rules consistently across the entire project.
- Maintain strict architectural boundaries between components and subsystems.
- Prefer production-ready implementations over temporary shortcuts.
- Ensure every module, type, function, and abstraction has a clear purpose.
- Avoid duplicated implementations, unnecessary dependencies, and redundant logic.
- Preserve compatibility with Rust's compiler, Cargo, and module system.
- Treat warnings, errors, and unexpected behavior as issues to investigate rather than suppress.
- Keep the codebase structurally consistent as it grows.
- Prioritize correctness, readability, modularity, and maintainability in every implementation.

## 13. Core Engineering Principle

Build every component as if it were part of a long-term, production-grade systems software project.

The entire codebase must remain:

- Modular and architecturally consistent.
- Explicit and strongly typed.
- Readable and self-explanatory.
- Efficient and resource-conscious.
- Reliable and functionally complete.
- Maintainable, scalable, and easy to extend.

Architectural clarity, functional correctness, predictable behavior, and long-term maintainability must always take priority over unnecessary complexity, artificial abstraction, or temporary shortcuts.

## 14. Exhaustive Pattern Matching and State Handling

- Every `match` expression must correctly handle every relevant state and variant.
- Prefer explicit exhaustive matching over wildcard branches.
- Never use `_` to silently ignore unhandled enum variants, protocol states, instruction types, or error conditions.
- For project-controlled enums, explicitly enumerate all variants whenever practical.
- Never introduce default branches that return fabricated success, arbitrary values, or misleading results.
- Unexpected, unsupported, or invalid input must produce an explicit, meaningful error when it cannot be handled correctly.
- For external input domains that cannot be fully enumerated, use explicit validation and error handling.
- Never use wildcard branches merely to avoid updating a match expression when new variants are introduced.
- Prefer compiler-enforced exhaustiveness so newly introduced enum variants trigger compilation errors.
- Distinguish valid states, invalid states, unsupported operations, and recoverable errors through explicit types.
- Use `Result`, `Option`, and strongly typed enums to represent meaningful outcomes.
- Never silently discard errors or bypass required validation.

### Correct Example

```rust
enum ProcessorState {
    Ready,
    Running,
    Halted,
}

fn state_name(state: ProcessorState) -> &'static str {
    match state {
        ProcessorState::Ready => "ready",
        ProcessorState::Running => "running",
        ProcessorState::Halted => "halted",
    }
}
```

### Invalid Example

```rust
fn state_name(state: ProcessorState) -> &'static str {
    match state {
        ProcessorState::Ready => "ready",
        _ => "unknown",
    }
}
```

- Wildcard branches are acceptable only when the domain is genuinely open-ended or externally defined and the branch performs deliberate, correct handling.
- Exhaustive matching must be used as a correctness mechanism, not merely as a stylistic preference.

## 15. Unsafe Rust and Memory Safety

- Prefer safe Rust whenever it can provide the required behavior and performance.
- Never introduce `unsafe` merely for convenience or speculative optimization.
- Every unsafe operation must have a concrete technical justification.
- Keep unsafe blocks as small and localized as possible.
- Encapsulate unsafe implementation details behind safe interfaces only when their invariants can be guaranteed.
- Explicitly identify and maintain the invariants required by unsafe operations.
- Never introduce `SAFETY` comments.
- Validate pointer alignment, allocation boundaries, initialization state, lifetimes, aliasing requirements, and memory ownership.
- Prevent use-after-free, double-free, invalid dereferences, data races, and undefined behavior.
- Treat foreign function interfaces, inline assembly, raw pointers, memory-mapped hardware, and manual allocation as safety-critical boundaries.
- Use appropriate synchronization primitives for shared mutable state.
- Avoid unsafe abstractions that expose invalid states to otherwise safe code.
- Never assume an unsafe operation is correct merely because it compiles or passes ordinary tests.
- Audit existing unsafe code whenever surrounding types, ownership rules, memory layouts, or calling conventions change.
- Use appropriate validation tools, including Miri and sanitizers where supported and applicable.
- If safety cannot be established, identify the unresolved invariant rather than presenting the implementation as verified.
- When external safety documentation requirements conflict with the no-comment policy, report the conflict instead of silently violating either requirement.

## 16. Compiler Warnings and Diagnostic Integrity

- Maintain a zero-warning objective for all project-owned code.
- Treat compiler warnings and Clippy diagnostics as actionable engineering issues.
- Fix the underlying cause of each warning rather than suppressing its diagnostic.
- Never introduce broad lint suppression to hide incomplete implementations or poor design.
- Do not use `allow(dead_code)`, `allow(unused_variables)`, `allow(unused_imports)`, or similar attributes as shortcuts.
- Preserve the mandatory crate-level `#![allow(non_upper_case_globals)]` exception.
- Additional lint exceptions require a specific technical justification and must have the narrowest practical scope.
- Remove unused imports, unreachable branches, obsolete code, unnecessary mutability, and redundant allocations.
- Investigate deprecated APIs and replace them with maintained alternatives when behavior and compatibility can be preserved.
- Do not ignore warnings originating from build scripts, tests, procedural macros, or project-owned dependencies.
- Distinguish actionable project warnings from diagnostics in external dependencies that cannot be modified directly.
- Never claim zero warnings unless the relevant validation commands have completed successfully.

### Required Validation

```bash
cargo fmt --all -- --check
cargo check --all-targets
cargo clippy --all-targets --all-features -- -D warnings
cargo test --all-targets
```

- Use workspace-wide validation when working in a Cargo workspace.
- Validate additional feature configurations when feature combinations are significant.
- Do not use `cargo fix` blindly without reviewing the resulting changes.
- Ensure automated fixes preserve behavior, public interfaces, and architectural boundaries.

## 17. Rust Modernization and Dependency Maintenance

- Prefer maintained, stable Rust features that improve correctness, readability, or performance.
- Keep the project compatible with its explicitly declared minimum supported Rust version.
- Upgrade deprecated APIs and obsolete implementation patterns when safe and appropriate.
- Maintain dependencies with attention to security advisories, compatibility, and actual project requirements.
- Avoid unnecessary dependencies and avoid replacing reliable implementations without measurable benefits.
- Review breaking changes before upgrading dependency major versions.
- Preserve deterministic builds and reproducible dependency resolution.
- Never perform broad dependency upgrades without validating compilation, tests, and affected interfaces.
- Use `cargo update` deliberately and review lockfile changes.
- Keep Rust edition choices explicit and migrate editions only after reviewing compatibility implications.
- Prefer supported compiler and standard-library functionality over unnecessary third-party abstractions.
- Do not introduce nightly-only features unless the project explicitly requires them.
- Never represent an untested migration or upgrade as complete.
- Verify that modernization does not introduce undefined behavior, performance regressions, or behavioral incompatibilities.

## 18. Complete Error and Edge-Case Coverage

- Identify all meaningful failure modes before implementing a feature.
- Handle invalid input, empty input, boundary values, overflow, underflow, recoverable allocation failure, and resource exhaustion where applicable.
- Use checked arithmetic when overflow is possible and must be handled.
- Validate conversions between integer types when truncation or overflow is possible.
- Distinguish recoverable errors from violated internal invariants.
- Never convert a failed operation into an apparent success.
- Never silently discard a `Result` containing a meaningful failure.
- Preserve useful error context across subsystem boundaries.
- Avoid broad fallback behavior that obscures the original failure.
- Ensure cleanup and resource release remain correct on success and failure paths.
- Validate binary formats, instruction encodings, protocol fields, and externally supplied values before using them.
- Handle unsupported architecture features and instruction variants explicitly.
- Prefer making invalid states unrepresentable through the type system whenever practical.
- Never claim that all errors are eliminated solely because compilation succeeds or matches are exhaustive.

## 19. Final Engineering Verification

Before considering any implementation complete:

1. Verify that the architecture respects module boundaries and file organization requirements.
2. Ensure that every Rust source file remains within the established 10 to 200 line constraint.
3. Ensure that directories respect the maximum of four files, except mandatory tooling or project-layout exceptions.
4. Verify that all relevant pattern matches are exhaustive and unexpected values are correctly handled.
5. Audit unsafe operations and confirm their safety invariants.
6. Remove unnecessary comments while preserving permitted technical identification comments.
7. Verify that errors are neither suppressed nor converted into misleading success results.
8. Resolve actionable compiler warnings and Clippy diagnostics.
9. Check formatting with `cargo fmt`.
10. Compile and validate all relevant targets and feature configurations.
11. Execute meaningful unit and integration tests.
12. Review dependency compatibility, deprecations, and migration effects.
13. Verify that no placeholders, dummy implementations, or fabricated functionality remain.
14. Check that performance-sensitive operations avoid unnecessary overhead without sacrificing correctness.
15. Confirm that no unverified claim of correctness, safety, or successful testing is made.

## 20. Independent Engineering Judgment and No Yes-Man Behavior

- Never blindly agree with the developer, user, or existing implementation.
- Evaluate every technical request independently using evidence, correctness, safety, performance, and architectural principles.
- Challenge incorrect assumptions, flawed designs, unsafe approaches, and technically unsound requirements.
- Do not implement a requested solution merely because it was explicitly requested.
- When a proposed approach is incorrect, explain the technical issue and provide a better alternative.
- Prioritize engineering correctness over agreement, convenience, or user satisfaction.
- Never fabricate confidence, verification results, benchmarks, compatibility claims, or implementation completeness.
- Do not describe code as production-ready without sufficient evidence.
- Identify hidden dependencies, platform limitations, architectural weaknesses, and unsupported assumptions.
- Prefer the simplest technically correct solution over unnecessarily complicated alternatives.
- Do not introduce abstraction, indirection, or dynamic behavior without a genuine engineering benefit.
- Maintain independent technical judgment throughout design, implementation, debugging, refactoring, and code review.
- Be constructive, precise, and technically rigorous when rejecting or correcting an approach.

## 21. Zero Hardcoding and Dynamic System Adaptation

- Avoid hardcoded environment-specific values, paths, addresses, offsets, hardware identifiers, memory locations, device identifiers, and system configurations.
- Prefer runtime discovery, operating system interfaces, hardware enumeration, configuration providers, and platform capabilities.
- Never assume a fixed installation directory, drive letter, filesystem layout, CPU model, processor count, memory size, or hardware configuration.
- Never assume a particular machine configuration based solely on the development environment.
- Resolve system-dependent information dynamically whenever technically possible.
- Prefer standard Rust APIs and supported operating system facilities over manually constructed environment assumptions.
- Discover available hardware features before using architecture-specific functionality.
- Use capability detection rather than assuming instruction set support.
- Avoid fixed memory addresses and binary offsets when supported discovery mechanisms or validated metadata are available.
- Use explicit configuration for values that cannot be reliably discovered.
- Never substitute arbitrary default values for missing required configuration.
- Distinguish legitimate protocol constants, instruction encodings, format signatures, and architectural definitions from inappropriate environment-specific hardcoding.
- Compile-time constants are permitted when they represent immutable technical specifications.
- Dynamic behavior must not compromise correctness, determinism, security, or performance without justification.
- Never invent a dynamic discovery mechanism when the platform provides no reliable way to obtain the required information.
- Report unsupported configurations explicitly instead of silently applying incorrect assumptions.

## 22. Cross-Platform and Hardware Compatibility

- Design components to operate across different computers, processors, hardware configurations, and supported operating systems.
- Prefer portable Rust implementations whenever practical.
- Isolate platform-specific functionality behind clearly defined interfaces.
- Keep architecture-specific assembly, hardware access, and operating system integrations separate from portable application logic.
- Use conditional compilation only when required by genuine platform differences.
- Detect runtime capabilities where supported and select compatible implementations.
- Never assume that all x86 or x86_64 processors support the same instruction set extensions.
- Never assume that virtualization features, privileged instructions, or hardware interfaces are universally available.
- Account for differences in pointer width, integer representation, alignment, endianness, and application binary interfaces.
- Use platform-defined APIs for memory management, process information, filesystem access, and system capabilities.
- Avoid assumptions about processor topology, cache hierarchy, page size, memory layout, and device availability.
- Ensure unsupported hardware features produce explicit, meaningful errors.
- Provide portable alternatives when feasible without compromising correctness.
- Do not claim universal compatibility when operating system permissions, hardware capabilities, or architecture constraints prevent it.
- Define and document the actual supported platform matrix outside source code.
- Validate compatibility across representative target configurations whenever the necessary environments are available.

## 23. Strict Technical Comment Policy

- Do not write explanatory comments inside source files.
- Comments are permitted exclusively for technical identification of patterns, opcodes, instruction encodings, virtual machine signatures, binary signatures, register semantics, hardware flags, and equivalent low-level identifiers.
- Comments must identify exact technical meanings rather than explain implementation behavior.
- Keep every permitted comment concise, factual, and directly adjacent to the relevant value or instruction.
- Never use comments to describe functions, control flow, algorithms, ownership, error handling, or implementation decisions.
- Never introduce `SAFETY` comments.
- Never use comments as substitutes for meaningful naming, explicit types, or clear interfaces.
- Avoid documentation comments, decorative comments, section markers, and redundant inline descriptions.
- Preserve technical accuracy when modifying patterns, signatures, instruction values, or hardware definitions.
- Never include uncertain or fabricated opcode descriptions or signature identifications.
- Express safety invariants through type design, encapsulation, validation, and enforceable interfaces wherever possible.
- Audit unsafe operations even when comments are prohibited.
- If a safety invariant cannot be established, reject or redesign the unsafe implementation rather than hiding the uncertainty.

### Permitted Comment Examples

```rust
let instruction = 0x90; // NOP
let breakpoint = 0xCC; // INT3
let halt = 0xF4; // HLT

let dos_signature = [0x4D, 0x5A]; // MZ
let portable_executable_signature = [0x50, 0x45, 0x00, 0x00]; // PE
```

- These constants are valid because they represent fixed technical specifications, not machine-dependent configuration.
- All other comments must be removed unless they belong to one of the explicitly permitted technical identification categories.

## 24. English-Only Source and Engineering Output

- English is mandatory throughout the entire codebase.
- All identifiers, types, functions, methods, variables, constants, modules, directories, and internal interfaces must use English.
- All error messages, diagnostics, logs, assertions, and user-facing strings must use English.
- All permitted technical comments must use English terminology.
- All generated implementation plans, technical explanations, code reviews, and validation reports must be written in English.
- Do not mix languages within source code, configuration files, technical documentation, or generated engineering artifacts.
- Preserve exact externally mandated identifiers, binary signatures, protocol tokens, and standard technical notation when required for interoperability.

## 25. Exhaustive Handling Without Silent Defaults

- Explicitly handle every variant of project-controlled enums.
- Prefer compiler-enforced exhaustive matching.
- Never use wildcard patterns to hide newly introduced variants.
- Never introduce fallback branches that silently return success.
- Unexpected values must be rejected with a meaningful error when no valid behavior exists.
- For open-ended numeric domains, binary inputs, and external protocol values, use validated catch-all handling.
- Never silently ignore unsupported instructions, processor states, virtual machine signatures, or hardware capabilities.
- Do not fabricate a result when an operation cannot be completed.
- Do not use `unwrap()`, `expect()`, `panic!()`, or unreachable-state assertions to replace proper recoverable error handling.
- Keep pattern matching explicit, deterministic, and maintainable.
- Ensure that new enum variants require deliberate handling rather than being absorbed by generic fallback behavior.

## 26. Zero-Warning and Unsafe Remediation Policy

- Maintain zero actionable compiler warnings and Clippy diagnostics in project-owned code.
- Fix diagnostics at their source rather than suppressing them.
- Do not introduce broad lint suppression attributes.
- Preserve only explicitly required and technically justified lint exceptions.
- Prefer safe Rust implementations.
- Eliminate unnecessary unsafe operations.
- Minimize unavoidable unsafe boundaries and enforce their invariants through implementation structure.
- Never remove necessary runtime validation merely to simplify unsafe code.
- Never assume that successful compilation proves memory safety.
- Investigate undefined behavior risks, aliasing violations, invalid pointer usage, alignment errors, and lifetime violations.
- Use Miri, sanitizers, and appropriate platform-specific validation tools when supported.
- Upgrade deprecated APIs and obsolete implementations when compatibility and correctness can be preserved.
- Never claim that warnings, unsafe defects, or compatibility issues have been resolved unless the relevant checks have actually been performed.
- If a requested no-comment policy conflicts with a mandatory toolchain, project, or external safety documentation requirement, report the conflict explicitly instead of silently violating either requirement.

## 27. Typography and Output Restrictions

- Never use em dash or en dash Unicode characters.
- Use ordinary ASCII punctuation instead.
- Prefer commas, periods, colons, semicolons, and parentheses.
- Use the standard ASCII hyphen only where grammatically or technically necessary.
- Never introduce decorative Unicode punctuation into source code, comments, documentation, logs, or generated technical explanations.
- Preserve required syntax and exact binary or protocol representations.

## 28. Final Engineering Principles

- Never blindly agree with technically incorrect requirements.
- Never introduce unnecessary environment-specific hardcoding.
- Prefer dynamic discovery and explicit configuration.
- Design for all explicitly supported platforms and hardware configurations.
- Never claim compatibility with untested or fundamentally unsupported systems.
- Keep technical comments restricted to low-level identification.
- Never write explanatory or `SAFETY` comments.
- Handle all relevant states explicitly.
- Never use silent success fallbacks for unsupported operations.
- Eliminate unnecessary unsafe code and validate unavoidable unsafe boundaries.
- Resolve compiler warnings without hiding defects.
- Keep all source code and engineering output in English.
- Avoid em dash and en dash characters completely.
- Never introduce fake functionality, artificial results, or unverified claims.
- Prioritize correctness, portability, security, deterministic behavior, performance, and long-term maintainability.

## 29. No Decorative Banners or Separators

- Never introduce decorative banners, ASCII art, or visual separators into source files.
- Never use repeated characters such as `=============================================`, `---------------------------------------------`, `#############################################`, or `*********************************************` as section markers.
- Never create comment banners around functions, modules, structures, constants, or implementation blocks.
- Never add generated file headers, decorative copyright banners, or unnecessary visual markers.
- Never replace proper module organization with visual separation inside large files.
- Use meaningful names, whitespace, and logical module boundaries instead.
- Keep source files visually clean, minimal, and consistent.
- Remove existing decorative banners when safely refactoring affected code.
- Preserve required license notices and externally mandated file headers when legally or technically necessary.
- Do not remove legitimate Markdown syntax or language syntax merely because it contains repeated punctuation.

## 30. Complete Memory and Resource Lifecycle Management

- Treat memory safety, resource ownership, and cleanup correctness as mandatory engineering requirements.
- Ensure every owned allocation has a clearly defined and correct release mechanism.
- Prefer Rust ownership and RAII to manage resource lifetimes automatically.
- Avoid manual allocation and deallocation when safe standard-library abstractions are sufficient.
- Prevent memory leaks, double frees, use-after-free, dangling pointers, invalid frees, and uninitialized memory access.
- Never free memory through an allocator incompatible with the allocator that created it.
- Ensure that custom allocation and deallocation layouts match exactly.
- Validate allocation size, alignment, capacity, initialization, and ownership requirements.
- Avoid unnecessary memory retention and unbounded growth.
- Ensure that failure paths correctly release all resources that are no longer required.
- Use appropriate cleanup mechanisms for files, sockets, handles, mappings, synchronization objects, and external resources.
- Never assume that process termination is an acceptable substitute for correct resource management.
- Audit ownership transfers across FFI boundaries and external libraries.
- Avoid reference cycles in reference-counted structures or break them explicitly when required.
- Ensure concurrent resource access does not introduce data races or invalid lifetime assumptions.
- Verify that destructors and cleanup paths do not introduce double releases or invalid state transitions.
- Use memory analysis tools, leak detectors, sanitizers, and Miri when applicable.
- Never claim that memory leaks or resource defects have been eliminated without appropriate verification.
- Report any unresolved memory safety or resource lifecycle limitation explicitly.

## 31. Mandatory Research and Technical Verification Before Coding

- Perform relevant technical research before implementing, modifying, or refactoring code.
- Use available web search tools before coding when web access is permitted.
- Prefer authoritative documentation, official specifications, upstream source code, and maintained technical references.
- Verify API signatures, platform requirements, instruction semantics, binary layouts, calling conventions, and compatibility constraints.
- Never rely on outdated assumptions when current authoritative information can be checked.
- Cross-check uncertain technical claims against reliable sources.
- Do not fabricate documentation, references, specifications, or research results.
- Distinguish confirmed facts from assumptions and unresolved uncertainties.
- Inspect the existing codebase before proposing structural changes.
- Understand relevant dependencies, ownership boundaries, execution paths, and external interfaces before modifying them.
- Use disassemblers and decompilers when working with existing binaries, instruction streams, machine code, executable formats, virtual machine implementations, or reverse engineering tasks.
- Verify instruction encodings, binary signatures, control flow, data layouts, and calling conventions using appropriate tools.
- Treat decompiler output as an interpretation rather than guaranteed original source code.
- Cross-check decompiled logic against disassembly, runtime behavior, and available specifications.
- Never claim complete understanding of a binary solely from a decompiler output.
- Use dynamic analysis, debugging, tracing, and controlled experiments when static analysis is insufficient.
- Do not perform unnecessary reverse engineering when authoritative source code or documentation already provides sufficient evidence.
- Respect applicable permissions, authorization boundaries, and legal requirements when analyzing software.
- If required research tools are unavailable, disclose the limitation and continue only when sufficient reliable information exists.
- Never claim that web research, disassembly, decompilation, or verification occurred unless it actually occurred.

## 32. Operator Clarification and Uncertainty Resolution

- Ask the operator when a requirement is ambiguous, contradictory, incomplete, or technically uncertain.
- Never invent missing requirements or silently choose behavior that could materially affect correctness.
- Request clarification before making irreversible architectural decisions based on unsupported assumptions.
- Ask the operator when multiple valid implementations have significantly different compatibility, security, performance, or maintenance implications.
- Ask for confirmation before changing externally visible behavior, public interfaces, persistent data formats, or critical compatibility guarantees when the intended behavior is unclear.
- Do not ask unnecessary questions when the answer is already established by the codebase, authoritative documentation, or explicit requirements.
- Investigate independently before escalating routine technical questions.
- Present the specific uncertainty, relevant evidence, and technically sound options.
- Never treat an operator's assumption as proof of technical correctness.
- Challenge incorrect operator assumptions respectfully and provide supporting reasoning.
- If the operator cannot resolve an essential uncertainty, clearly identify the limitation rather than fabricating an implementation.
- Never claim certainty when the available evidence is insufficient.
- Continue autonomously when requirements are clear and the implementation can be verified reliably.

## 33. Final Mandatory Engineering Standard

Every implementation must satisfy the following principles:

- Modular architecture with explicit subsystem boundaries.
- Strong typing and predictable ownership.
- Complete and meaningful functionality.
- No fabricated implementations or misleading results.
- No unnecessary environment-specific hardcoding.
- Dynamic capability discovery wherever technically appropriate.
- Explicit handling of unsupported hardware and operating system configurations.
- Exhaustive pattern matching for controlled state domains.
- Correct handling of invalid input and unexpected states.
- No silent error suppression or fabricated success.
- Minimal, justified, and carefully audited unsafe code.
- Correct memory ownership and resource cleanup.
- No avoidable memory leaks, double frees, or dangling references.
- Zero actionable compiler warnings under verified configurations.
- No decorative banners or repeated-character separators.
- Technical identification comments only.
- No explanatory comments or `SAFETY` comments.
- English-only source code and engineering artifacts.
- No em dash or en dash characters.
- Relevant research and verification before implementation.
- Disassembly and decompilation when technically necessary.
- Operator clarification when essential requirements remain uncertain.
- Independent engineering judgment rather than blind agreement.
- Honest reporting of validation results and remaining limitations.

**Final Principle**

Build every component as if it were part of a long-term, production-grade systems software project.

Architectural clarity, functional correctness, memory safety, explicit state handling, predictable behavior, portability, and maintainability must take priority over convenience, superficial cleanliness, unnecessary abstraction, and unsupported assumptions.

Never hide defects through fallback branches, warning suppression, unchecked assumptions, incomplete validation, fake implementations, or misleading claims of correctness.

Every implementation must be as safe, complete, portable, efficient, and verifiable as the actual technical constraints permit.