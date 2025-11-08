# DazzleLib

**Foundation Libraries for the Dazzle Ecosystem**

[![GitHub](https://img.shields.io/badge/GitHub-DazzleLib-blue?logo=github)](https://github.com/DazzleLib)
[![PyPI](https://img.shields.io/badge/PyPI-dazzle--*-blue?logo=pypi)](https://pypi.org/search/?q=dazzle-)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Sponsor](https://img.shields.io/badge/Sponsor-GitHub-ea4aaa?logo=github-sponsors)](https://github.com/sponsors/djdarcy)

> High-quality, reusable Python libraries that power [DazzleTools](https://github.com/DazzleTools), [DazzleML](https://github.com/DazzleML), and [DazzleNodes](https://github.com/DazzleNodes).

---

## What is DazzleLib?

**DazzleLib** is a collection of foundational Python libraries designed to solve common development challenges with cross-platform compatibility, robust error handling, and minimal dependencies. Built on principles of composability and clarity, these libraries are the building blocks powering the entire Dazzle ecosystem.

**[Read our design philosophy →](docs/philosophy.md)**

---

## Libraries

### 📁 [dazzle-filekit](https://github.com/DazzleLib/dazzle-filekit)
**Cross-platform file operations with verification and metadata preservation**

[![PyPI](https://img.shields.io/pypi/v/dazzle-filekit)](https://pypi.org/project/dazzle-filekit/)

```bash
pip install dazzle-filekit
```

File operations (copy, move, verify) with hash calculation, metadata preservation, and cross-platform path handling including Windows UNC paths.

**[Full documentation →](docs/libraries/dazzle-filekit.md)** | **[Repository →](https://github.com/DazzleLib/dazzle-filekit)**

---

### 🌳 [dazzle-tree-lib](https://github.com/DazzleLib/dazzle-tree-lib)
**Tree structure utilities for hierarchical data**

[![PyPI](https://img.shields.io/pypi/v/dazzle-tree-lib)](https://pypi.org/project/dazzle-tree-lib/)

```bash
pip install dazzle-tree-lib
```

Generic tree data structures with traversal algorithms (DFS, BFS), visualization tools, and path-based operations.

**[Full documentation →](docs/libraries/dazzle-tree-lib.md)** | **[Repository →](https://github.com/DazzleLib/dazzle-tree-lib)**

---

### 🔗 [UNCtools](https://github.com/DazzleLib/UNCtools)
**Windows UNC path handling and network drive utilities**

[![PyPI](https://img.shields.io/pypi/v/unctools)](https://pypi.org/project/unctools/)

```bash
pip install unctools
```

Parse UNC paths, detect network drives, convert between drive letters and UNC paths, and handle long path names (>260 characters). Cross-platform safe with graceful no-ops on Unix systems.

**[Full documentation →](docs/libraries/unctools.md)** | **[Repository →](https://github.com/DazzleLib/UNCtools)**

---

## Quick Start

```python
# File operations with verification
from dazzle_filekit import copy_file, calculate_file_hash

copy_file("source.txt", "dest.txt", preserve_metadata=True)
hash_value = calculate_file_hash("file.txt", algorithm="sha256")

# Tree structures
from dazzle_tree_lib import TreeNode

root = TreeNode("root")
child = root.add_child("child1")

# Windows UNC paths
from unctools import is_unc_path, parse_unc_path

if is_unc_path(r"\\server\share\file.txt"):
    server, share, path = parse_unc_path(r"\\server\share\file.txt")
```

---

## Documentation

- **[Design Philosophy](docs/philosophy.md)** - Principles and architectural decisions
- **[Library Roadmap](docs/roadmap.md)** - Current status and planned libraries
- **[dazzle-filekit Documentation](docs/libraries/dazzle-filekit.md)** - File operations
- **[dazzle-tree-lib Documentation](docs/libraries/dazzle-tree-lib.md)** - Tree structures
- **[UNCtools Documentation](docs/libraries/unctools.md)** - UNC path handling

---

## Used By

DazzleLib powers these projects in the Dazzle ecosystem:

**[DazzleTools](https://github.com/DazzleTools)**: preserve, dazzlelink, relinker (future)
**[DazzleML](https://github.com/DazzleML)**: File organization and training data management
**[DazzleNodes](https://github.com/DazzleNodes)**: ComfyUI custom nodes file operations

---

## Platform Support

| Library | Windows | Linux | macOS | Python |
|---------|---------|-------|-------|--------|
| dazzle-filekit | ✅ Full | ✅ Full | ✅ Full | 3.8+ |
| dazzle-tree-lib | ✅ Full | ✅ Full | ✅ Full | 3.8+ |
| UNCtools | ✅ Full | ⚠️ No-op | ⚠️ No-op | 3.8+ |

---

## Contributing

Contributions are welcome! Each library has its own repository with contribution guidelines.

**General Process**:
1. Fork the library repository
2. Create a feature branch
3. Add tests for new functionality
4. Ensure all tests pass (`pytest`)
5. Submit a pull request

**[Read full contributing guidelines →](CONTRIBUTING.md)**

---

## 💰 Sustainability

DazzleLib is part of the [DazzleProj](https://github.com/DazzleProj) ecosystem.

**Current sponsorship: $0/month | Goal: $1,000/month**

If you're using DazzleLib in commercial projects, these libraries save you weeks of development time. Contributing $25-100/month is a fraction of that value.

**[Sponsor DazzleProj on GitHub](https://github.com/sponsors/djdarcy)** ☕

**Sponsorship Benefits**:
- Priority support for library issues
- Influence roadmap and feature priorities
- Early access to new libraries
- Recognition in README and website

Like the project?

[!["Buy Me A Coffee"](https://camo.githubusercontent.com/0b448aabee402aaf7b3b256ae471e7dc66bcf174fad7d6bb52b27138b2364e47/68747470733a2f2f7777772e6275796d6561636f666665652e636f6d2f6173736574732f696d672f637573746f6d5f696d616765732f6f72616e67655f696d672e706e67)](https://www.buymeacoffee.com/djdarcy)

---

## Part of DazzleProj

DazzleLib is one of five organizations in the Dazzle ecosystem:

- **[DazzleProj](https://github.com/DazzleProj)** - Ecosystem coordination
- **[DazzleLib](https://github.com/DazzleLib)** - Foundation libraries ← *You are here*
- **[DazzleTools](https://github.com/DazzleTools)** - Command-line tools
- **[DazzleNodes](https://github.com/DazzleNodes)** - ComfyUI custom nodes
- **[DazzleML](https://github.com/DazzleML)** - AI development tools

---

## License

All DazzleLib libraries are released under the **MIT License** for maximum compatibility with both open source and commercial projects.

See individual library repositories for specific license files.

---

## Contact

- **Issues**: Use repository-specific issue trackers
- **Discussions**: [GitHub Discussions](https://github.com/DazzleLib/discussions)
- **Sponsorship**: [GitHub Sponsors](https://github.com/sponsors/djdarcy)
- **Website**: [DazzleProj.com](https://dazzleproj.com) *(coming soon)*

---

**Build better tools with DazzleLib** 🛠️
