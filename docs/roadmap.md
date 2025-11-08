# DazzleLib Roadmap

**Library roadmap and planned features**

---

## Current Status (2025)

### ✅ Stable Libraries

#### dazzle-filekit
**Status**: Stable, published on PyPI

Cross-platform file operations with verification and metadata preservation.

- ✅ File copy/move with metadata preservation
- ✅ Hash calculation (MD5, SHA1, SHA256, SHA512)
- ✅ Directory comparison and synchronization
- ✅ Cross-platform path handling
- ✅ Windows UNC path support (optional)

**Install**: `pip install dazzle-filekit`

---

#### dazzle-tree-lib
**Status**: Stable, published on PyPI

Tree structure utilities for hierarchical data.

- ✅ Generic tree data structures
- ✅ Traversal algorithms (DFS, BFS, iterative)
- ✅ Tree visualization and pretty-printing
- ✅ Path operations on trees
- ✅ Node manipulation and queries

**Install**: `pip install dazzle-tree-lib`

---

### 🚧 In Progress

#### UNCtools
**Status**: Migrating to DazzleLib organization

Windows UNC path handling and network drive utilities.

- ✅ UNC path parsing and validation
- ✅ Network drive detection
- ✅ Drive letter to UNC conversion
- ✅ Long path support (>260 characters)
- ✅ Cross-platform safety (no-op on Unix)
- 🚧 Moving repository to DazzleLib organization
- 🚧 PyPI publication under DazzleLib

**Planned Install**: `pip install unctools`

---

## Planned Libraries

New libraries are added based on common patterns identified across Dazzle tools. Each planned library addresses recurring needs in the ecosystem.

### dazzle-config-lib
**Configuration file handling (YAML, TOML, JSON)**

**Problem**: Every tool needs to load/save configuration, but handling different formats with validation is repetitive.

**Planned Features**:
- Unified API for YAML, TOML, JSON config files
- Schema validation with helpful error messages
- Environment variable interpolation
- Configuration merging (defaults + user config)
- Type-safe configuration classes
- Migration utilities for config format changes

**Use Cases**:
- Application settings files
- Tool configuration
- Project configuration
- Environment-specific configs

**Status**: Research phase

---

### dazzle-cli-lib
**Command-line interface building blocks**

**Problem**: Building robust CLIs requires argument parsing, help text, subcommands, and consistent error handling.

**Planned Features**:
- Enhanced argument parsing (builds on argparse)
- Automatic help generation from docstrings
- Subcommand management
- Progress bars and status updates
- Interactive prompts with validation
- Colorized output (with fallbacks)
- Shell completion generation

**Use Cases**:
- DazzleTools command-line applications
- Script argument handling
- Interactive utilities

**Status**: Research phase

---

### dazzle-log-lib
**Structured logging utilities**

**Problem**: Consistent, structured logging across tools is essential for debugging and monitoring.

**Planned Features**:
- Structured logging (JSON/text formats)
- Log level configuration
- Contextual logging (request IDs, user context)
- Log rotation and archival
- Performance-optimized logging
- Integration with monitoring tools

**Use Cases**:
- Application logging
- Debugging complex operations
- Audit trails
- Performance monitoring

**Status**: Research phase

---

### dazzle-test-lib
**Testing utilities and fixtures**

**Problem**: Writing tests for file operations, CLI tools, and cross-platform code requires common test utilities.

**Planned Features**:
- Temporary directory fixtures
- Mock file systems
- Test data generators
- Cross-platform test helpers
- Performance benchmarking utilities
- Integration test helpers

**Use Cases**:
- Testing DazzleTools
- Testing file operations
- Cross-platform test coverage
- Regression testing

**Status**: Research phase

---

## Feature Roadmap for Existing Libraries

### dazzle-filekit

#### Near-term (2025 Q2-Q3)
- Enhanced directory synchronization with conflict resolution strategies
- Parallel file operations for large directories
- Incremental backup support
- File deduplication utilities

#### Long-term (2025 Q4+)
- Cloud storage integration (S3, Azure Blob, GCS)
- Compression utilities (zip, tar, 7z)
- File watch/monitor capabilities
- Advanced metadata preservation (extended attributes, ACLs)

---

### dazzle-tree-lib

#### Near-term (2025 Q2-Q3)
- Tree serialization formats (JSON, YAML)
- Tree diffing and merging
- Performance optimizations for large trees
- Additional traversal strategies

#### Long-term (2025 Q4+)
- Database-backed trees for very large hierarchies
- Concurrent tree modifications
- Tree visualization export (GraphViz, Mermaid)
- Tree transformation utilities

---

### UNCtools

#### Near-term (2025 Q2-Q3)
- Complete migration to DazzleLib organization
- PyPI publication
- Enhanced network drive utilities
- Share access permission queries

#### Long-term (2025 Q4+)
- Network path availability checking
- SMB protocol integration
- Network drive mounting/unmounting utilities

---

## How New Libraries Are Chosen

DazzleLib follows a **needs-driven approach** for new libraries:

### 1. Pattern Recognition
When we see the same code patterns across 3+ DazzleTools, we extract them into a library.

### 2. Community Requests
Feature requests and discussions help identify gaps in the ecosystem.

### 3. Architectural Fit
New libraries must fit DazzleLib's philosophy:
- Composable and focused
- Cross-platform by default
- Minimal dependencies
- MIT licensed

### 4. Maintenance Capacity
We only add libraries we can properly maintain and support.

---

## Library Lifecycle

### 1. Research Phase
- Identify common patterns
- Design API
- Review similar libraries
- Validate use cases

### 2. Alpha Release
- Initial implementation
- Basic tests
- Documentation
- Private testing

### 3. Beta Release
- Public testing
- Gather feedback
- API refinement
- Documentation improvements

### 4. Stable Release
- 1.0.0 release on PyPI
- Full documentation
- Comprehensive tests (80%+ coverage)
- Commitment to semantic versioning

### 5. Maintenance
- Bug fixes
- Performance improvements
- Feature additions (minor versions)
- Security updates

---

## Contributing to the Roadmap

Have ideas for new libraries or features? We'd love to hear them!

### How to Suggest a Library

1. **Check existing discussions**: Search [GitHub Discussions](https://github.com/DazzleLib/discussions)
2. **Describe the problem**: What problem does this library solve?
3. **Show examples**: Provide code examples of how it would be used
4. **Identify patterns**: Where do you see this pattern repeating?
5. **Consider alternatives**: Why not use an existing library?

### Feature Requests for Existing Libraries

1. **Use repository-specific issues**: File issues in the library's repository
2. **Describe the use case**: What are you trying to accomplish?
3. **Provide examples**: Show what the API might look like
4. **Consider cross-platform impact**: Will this work on all platforms?

---

## Roadmap Updates

This roadmap is updated quarterly based on:
- Community feedback
- DazzleTools development needs
- Industry trends
- Available maintenance capacity

**Last Updated**: January 2025

**Next Review**: April 2025

---

## Sponsorship Impact on Roadmap

Sponsorship directly influences development priorities:

- **$25/month**: Vote on library priorities
- **$100/month**: Influence feature roadmap
- **$500/month**: Priority support for requested features
- **$1000/month**: Dedicated development time for custom libraries

**[Sponsor DazzleProj on GitHub](https://github.com/sponsors/djdarcy)**

---

**Part of [DazzleProj](https://github.com/DazzleProj) - The Dazzle Ecosystem**
