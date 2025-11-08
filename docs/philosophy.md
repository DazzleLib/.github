# DazzleLib Philosophy

**Design principles and architectural decisions behind DazzleLib**

---

## Core Philosophy

DazzleLib libraries are designed as **composable building blocks**, not monolithic frameworks. This fundamental principle guides every architectural decision.

### Building Blocks
Libraries are composable primitives that can work independently or together. Each library solves a specific problem domain without requiring the entire ecosystem.

### Cross-Platform First
Work seamlessly on Windows, Linux, and macOS. Platform-specific features are clearly marked and gracefully degrade on unsupported platforms.

### MIT Licensed
Maximum compatibility for both open source and commercial use. No licensing barriers to adoption.

### Zero Magic
Clear, predictable APIs with explicit behavior. No hidden side effects, no automatic configuration, no surprises.

### Well Tested
Test coverage ensures reliability. All libraries maintain minimum 80% code coverage with comprehensive test suites.

---

## Design Principles

### 1. Minimal Dependencies

**Principle**: Libraries have minimal external dependencies to reduce installation complexity and potential conflicts.

**Why**:
- Reduces dependency hell for users
- Faster installation times
- Lower risk of version conflicts
- Easier to audit and maintain

**In Practice**:
- Prefer standard library when possible
- Optional dependencies for advanced features
- Clear documentation of all dependencies

### 2. Cross-Platform by Default

**Principle**: All APIs work consistently across Windows, Linux, and macOS. Platform-specific features are clearly marked and gracefully degrade.

**Why**:
- Users shouldn't need to worry about platform differences
- Code written once should run anywhere
- Platform-specific code is a maintenance burden

**In Practice**:
- Test on all three major platforms
- Platform-specific features return safe defaults on unsupported platforms
- Clear documentation of platform limitations

**Example**:
```python
# UNCtools on Windows: Full UNC path parsing
from unctools import is_unc_path
is_unc_path(r"\\server\share")  # Returns True

# UNCtools on Linux/macOS: Safe no-op
from unctools import is_unc_path
is_unc_path(r"\\server\share")  # Returns False (no exception)
```

### 3. Explicit over Implicit

**Principle**: Function behavior is predictable and well-documented. No magic, no surprises.

**Why**:
- Reduces cognitive load for users
- Makes debugging easier
- Prevents unexpected side effects
- Code is self-documenting

**In Practice**:
- Require explicit parameters instead of defaults when behavior is ambiguous
- No automatic file system modifications without explicit permission
- Clear error messages that explain what went wrong
- Type hints for all public APIs

**Example**:
```python
# GOOD: Explicit behavior
copy_file("source.txt", "dest.txt", preserve_metadata=True, overwrite=False)

# BAD: Implicit magic
copy_file("source.txt", "dest.txt")  # What happens? Overwrite? Preserve metadata?
```

### 4. Composability

**Principle**: Libraries are designed to work together but don't require each other. Use what you need.

**Why**:
- Users only install what they need
- Libraries can evolve independently
- No vendor lock-in to entire ecosystem
- Easier to understand and maintain smaller libraries

**In Practice**:
- No circular dependencies between libraries
- Optional integration points between libraries
- Each library has a clear, focused purpose

### 5. Backward Compatibility

**Principle**: We follow semantic versioning strictly. Breaking changes are rare and well-documented.

**Why**:
- Users can upgrade with confidence
- Reduces maintenance burden for dependent projects
- Builds trust in the ecosystem

**In Practice**:
- Semantic versioning (MAJOR.MINOR.PATCH)
- Deprecation warnings before removal
- Migration guides for breaking changes
- Long-term support for stable APIs

---

## Dependencies Between Libraries

DazzleLib libraries form a **directed acyclic graph** - no circular dependencies.

### Dependency Graph

```
UNCtools (standalone)
    ↓ (optional)
dazzle-filekit (uses UNCtools for Windows paths)
    ↓
dazzle-tree-lib (standalone, but often used with filekit)
```

### Dependency Guidelines

#### No Circular Dependencies
Libraries form a directed acyclic graph. If Library A depends on Library B, Library B cannot depend on Library A.

**Why**: Circular dependencies make libraries impossible to install or upgrade independently.

#### Optional Dependencies
Advanced features can require additional installs using extras syntax.

**Example**:
```bash
# Basic installation
pip install dazzle-filekit

# With UNC path support
pip install dazzle-filekit[unctools]
```

#### Explicit Imports
Import exactly what you need. No `import *`, no automatic namespace pollution.

**Example**:
```python
# GOOD: Explicit imports
from dazzle_filekit import copy_file, calculate_file_hash

# BAD: Namespace pollution
from dazzle_filekit import *
```

---

## Code Quality Standards

All DazzleLib libraries maintain these quality standards:

### Type Hints
Use type annotations for all public APIs to enable static analysis and IDE support.

```python
def copy_file(source: str, dest: str, preserve_metadata: bool = True) -> None:
    """Copy file with optional metadata preservation."""
    ...
```

### Docstrings
Google-style docstrings for all public functions and classes.

```python
def calculate_file_hash(filepath: str, algorithm: str = "sha256") -> str:
    """Calculate hash of file contents.

    Args:
        filepath: Path to file to hash
        algorithm: Hash algorithm (sha256, md5, sha1, sha512)

    Returns:
        Hex digest string of file hash

    Raises:
        FileNotFoundError: If filepath does not exist
        ValueError: If algorithm is not supported
    """
    ...
```

### Test Coverage
Minimum 80% code coverage with comprehensive test suites.

### Code Formatting
Black + Flake8 compliant for consistent code style.

---

## API Design Philosophy

### Function Names Should Be Clear
Prefer `calculate_file_hash()` over `hash()` - clarity over brevity.

### Return Values Should Be Obvious
Functions should return what users expect. No surprising tuple unpacking.

### Errors Should Be Helpful
Error messages should explain what went wrong and how to fix it:

```python
# GOOD
raise ValueError(
    f"Algorithm '{algorithm}' not supported. "
    f"Choose from: sha256, md5, sha1, sha512"
)

# BAD
raise ValueError("Invalid algorithm")
```

### Parameters Should Have Safe Defaults
When in doubt, choose the safest default behavior:
- `overwrite=False` (don't destroy data by default)
- `preserve_metadata=True` (preserve information by default)
- `verify=True` (verify operations when possible)

---

## Future Principles

As DazzleLib grows, we're considering additional principles:

### Performance by Default
Optimize common operations without sacrificing clarity.

### Async Support
Consider async variants for I/O-heavy operations.

### Extensibility
Provide hook points for users to extend behavior without forking.

---

## Contributing to DazzleLib Philosophy

These principles are not set in stone. If you have ideas for improving DazzleLib's design philosophy, we'd love to hear them:

- **GitHub Discussions**: [DazzleLib Discussions](https://github.com/DazzleLib/discussions)
- **Philosophy Issues**: Tag issues with `philosophy` label for architectural discussions

---

**Part of [DazzleProj](https://github.com/DazzleProj) - The Dazzle Ecosystem**
