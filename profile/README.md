# DazzleLib

**Foundation Libraries for the Dazzle Ecosystem**

[![GitHub](https://img.shields.io/badge/GitHub-DazzleLib-blue?logo=github)](https://github.com/DazzleLib)
[![PyPI](https://img.shields.io/badge/PyPI-dazzle--*-blue?logo=pypi)](https://pypi.org/search/?q=dazzle-)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Sponsor](https://img.shields.io/badge/Sponsor-GitHub-ea4aaa?logo=github-sponsors)](https://github.com/sponsors/djdarcy)

> High-quality, reusable Python libraries that power [DazzleTools](https://github.com/DazzleTools), [DazzleAI](https://github.com/DazzleAI), and [DazzleNodes](https://github.com/DazzleNodes).

---

## What is DazzleLib?

**DazzleLib** is a collection of foundational Python libraries designed to solve common development challenges with cross-platform compatibility, robust error handling, and minimal dependencies.

### Philosophy

- **Building Blocks** - Libraries are composable primitives, not monolithic frameworks
- **Cross-Platform** - Work seamlessly on Windows, Linux, and macOS
- **MIT Licensed** - Maximum compatibility for both open source and commercial use
- **Zero Magic** - Clear, predictable APIs with explicit behavior
- **Well Tested** - Test coverage for reliability

---

## Libraries

### 📁 [dazzle-filekit](https://github.com/DazzleLib/dazzle-filekit)
**Cross-platform file operations with verification and metadata preservation**

[![PyPI](https://img.shields.io/pypi/v/dazzle-filekit)](https://pypi.org/project/dazzle-filekit/)

```bash
pip install dazzle-filekit
```

**Features**:
- File operations (copy, move, verify) with metadata preservation
- Hash calculation and verification (MD5, SHA1, SHA256, SHA512)
- Cross-platform path handling including Windows UNC paths
- Directory comparison and synchronization
- Safe file operations with conflict resolution

**Used by**: preserve, relinker (future), and other file management tools

```python
from dazzle_filekit import copy_file, calculate_file_hash

# Copy with metadata preservation
copy_file("source.txt", "dest.txt", preserve_metadata=True)

# Calculate and verify hashes
hash_value = calculate_file_hash("file.txt", algorithm="sha256")
```

**Documentation**: [README](https://github.com/DazzleLib/dazzle-filekit#readme)

---

### 🌳 [dazzle-tree-lib](https://github.com/DazzleLib/dazzle-tree-lib)
**Tree structure utilities for hierarchical data**

[![PyPI](https://img.shields.io/pypi/v/dazzletreelib)](https://pypi.org/project/dazzletreelib/)

```bash
pip install dazzletreelib
```

**Features**:
- Generic tree data structures
- Tree traversal algorithms (DFS, BFS, iterative)
- Tree visualization and printing
- Path operations on tree structures
- Node manipulation and queries

**Used by**: Directory tree operations, hierarchical data processing

```python
from dazzle_tree_lib import Tree, TreeNode

# Create and manipulate tree structures
root = TreeNode("root")
child = root.add_child("child1")
```

**Documentation**: [README](https://github.com/DazzleLib/dazzle-tree-lib#readme)

---

### 🔗 [UNCtools](https://github.com/DazzleLib/UNCtools)
**Windows UNC path handling and network drive utilities**

[![PyPI](https://img.shields.io/pypi/v/unctools)](https://pypi.org/project/unctools/)

```bash
pip install unctools
```

**Features**:
- Parse and manipulate Windows UNC paths
- Network drive detection and mapping
- Convert between drive letters and UNC paths
- Handle long path names (>260 characters)
- Cross-platform compatibility (no-op on Unix)

**Used by**: dazzle-filekit, Windows-focused file tools

```python
from unctools import is_unc_path, parse_unc_path

# Work with UNC paths
if is_unc_path(r"\\server\share\file.txt"):
    server, share, path = parse_unc_path(r"\\server\share\file.txt")
```

**Documentation**: [README](https://github.com/DazzleLib/UNCtools#readme)

---

## Installation

### Install All Libraries

```bash
# Individual installation
pip install dazzle-filekit
pip install DazzleTreeLib
pip install unctools

# Or install with extras
pip install dazzle-filekit[unctools]  # Includes UNC path support
```

### Development Installation

```bash
# Clone and install in development mode
git clone https://github.com/DazzleLib/<library-name>
cd <library-name>
pip install -e ".[dev]"
```

---

## Usage Patterns

### File Operations with Verification

```python
from dazzle_filekit import copy_file, verify_copied_files

# Copy files with automatic verification
copy_file("source.txt", "backup/dest.txt",
          preserve_metadata=True)

# Verify copies
is_valid = verify_copied_files("source_dir", "backup_dir")
```

### Cross-Platform Path Handling

```python
from dazzle_filekit import normalize_path, is_same_file

# Normalize paths across platforms
path = normalize_path("/some/path/../file.txt")

# Compare paths reliably
if is_same_file(path1, path2):
    print("Same file!")
```

### Tree Operations

```python
from dazzle_tree_lib import Tree

# Build and traverse tree structures
tree = Tree()
root = tree.add_node("root")
child = tree.add_node("child", parent=root)

# Traverse
for node in tree.traverse_dfs():
    print(node.value)
```

---

## Design Principles

### 1. Minimal Dependencies
Libraries have minimal external dependencies to reduce installation complexity and potential conflicts.

### 2. Cross-Platform by Default
All APIs work consistently across Windows, Linux, and macOS. Platform-specific features are clearly marked and gracefully degrade.

### 3. Explicit over Implicit
Function behavior is predictable and well-documented. No magic, no surprises.

### 4. Composability
Libraries are designed to work together but don't require each other. Use what you need.

### 5. Backward Compatibility
We follow semantic versioning strictly. Breaking changes are rare and well-documented.

---

## Library Roadmap

### Current (2025)
- ✅ dazzle-filekit: Stable, published on PyPI
- ✅ dazzle-tree-lib: Stable, published on PyPI
- ✅ UNCtools: Stable, published on PyPI

### Planned Libraries
- **dazzle-config-lib**: Configuration file handling (YAML, TOML, JSON)
- **dazzle-cli-lib**: Command-line interface building blocks
- **dazzle-log-lib**: Structured logging utilities
- **dazzle-test-lib**: Testing utilities and fixtures

*New libraries are added based on common patterns across Dazzle tools.*

---

## Dependencies Between Libraries

```
UNCtools (standalone)
    ↓ (optional)
dazzle-filekit (uses UNCtools for Windows paths)
    ↓
dazzle-tree-lib (standalone, but often used with filekit)
```

### Dependency Guidelines
- **No circular dependencies**: Libraries form a directed acyclic graph
- **Optional dependencies**: Advanced features can require additional installs
- **Explicit imports**: Import exactly what you need

---

## Contributing

Contributions to DazzleLib are welcome! Each library has its own repository and contribution guidelines.

### Development Setup
```bash
# Clone the library
git clone https://github.com/DazzleLib/<library-name>
cd <library-name>

# Install in development mode with dev dependencies
pip install -e ".[dev]"

# Run tests
pytest tests/ -v --cov

# Format code
black dazzle_* tests/
flake8 dazzle_* tests/
```

### Code Quality Standards
- **Type hints**: Use type annotations for all public APIs
- **Docstrings**: Google-style docstrings for all public functions/classes
- **Tests**: Minimum 80% code coverage
- **Formatting**: Black + Flake8 compliant

---

## Used By

DazzleLib powers these projects in the Dazzle ecosystem:

### [DazzleTools](https://github.com/DazzleTools)
- **preserve**: Uses dazzle-filekit for file operations and verification
- **dazzlelink**: Uses dazzle-filekit for file references
- **relinker**: Heavy use of dazzle-filekit and dazzlelink

### [DazzleAI](https://github.com/DazzleAI)
- File organization and management tools use dazzle-filekit
- Training data management uses dazzle-tree-lib

### [DazzleNodes](https://github.com/DazzleNodes)
- ComfyUI nodes use dazzle-filekit for file operations where needed

### External Projects
If you're using DazzleLib in your project, let us know! We'd love to feature you here.

---

## Platform Support

| Library | Windows | Linux | macOS | Python Versions |
|---------|---------|-------|-------|-----------------|
| dazzle-filekit | ✅ Full | ✅ Full | ✅ Full | 3.8+ |
| dazzle-tree-lib | ✅ Full | ✅ Full | ✅ Full | 3.8+ |
| UNCtools | ✅ Full | ⚠️ No-op | ⚠️ No-op | 3.8+ |

**Notes**:
- UNCtools provides full functionality on Windows, graceful no-ops on Unix systems
- All libraries tested on Python 3.8, 3.9, 3.10, 3.11, 3.12

---

## Documentation

- **API Documentation**: See individual library repositories
- **Tutorials**: [DazzleProj.com](https://dazzleproj.com) *(coming soon)*
- **Examples**: Check `examples/` directory in each library
- **Discussions**: [GitHub Discussions](https://github.com/DazzleLib/discussions)

---

## Testing

All libraries maintain high test coverage:

```bash
# Run tests for a library
cd <library-name>
pytest tests/ -v --cov=<library_name>

# Run specific test file
pytest tests/test_file_operations.py -v

# Run with coverage report
pytest tests/ --cov=<library_name> --cov-report=html
```

---

## License

All DazzleLib libraries are released under the **MIT License** for maximum compatibility with both open source and commercial projects.

See individual library repositories for specific license files.

---

## Part of DazzleProj

DazzleLib is one of five organizations in the Dazzle ecosystem:

- **[DazzleProj](https://github.com/DazzleProj)** - Ecosystem coordination
- **[DazzleLib](https://github.com/DazzleLib)** - Foundation libraries ← *You are here*
- **[DazzleTools](https://github.com/DazzleTools)** - Command-line tools
- **[DazzleNodes](https://github.com/DazzleNodes)** - ComfyUI custom nodes
- **[DazzleAI](https://github.com/DazzleAI)** - AI development tools

---

## Contact

- **Issues**: Use repository-specific issue trackers
- **Discussions**: [GitHub Discussions](https://github.com/DazzleLib/discussions)
- **Sponsorship**: [GitHub Sponsors](https://github.com/sponsors/djdarcy)
- **Website**: [DazzleProj.com](https://dazzleproj.com) *(coming soon)*

---

**Build better tools with DazzleLib** 🛠️
