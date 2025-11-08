# dazzle-filekit

**Cross-platform file operations with verification and metadata preservation**

[![PyPI](https://img.shields.io/pypi/v/dazzle-filekit)](https://pypi.org/project/dazzle-filekit/)
[![GitHub](https://img.shields.io/badge/GitHub-DazzleLib/dazzle--filekit-blue?logo=github)](https://github.com/DazzleLib/dazzle-filekit)

## Installation

```bash
pip install dazzle-filekit

# With UNC path support for Windows
pip install dazzle-filekit[unctools]
```

## Features

- **File Operations**: Copy, move, and verify files with metadata preservation
- **Hash Calculation**: MD5, SHA1, SHA256, SHA512 support
- **Cross-Platform Paths**: Handles Windows UNC paths and Unix paths seamlessly
- **Directory Comparison**: Compare and synchronize directory contents
- **Safe Operations**: Conflict resolution and error handling
- **Metadata Preservation**: Preserve timestamps, permissions, and attributes

## Quick Start

```python
from dazzle_filekit import copy_file, calculate_file_hash, verify_copied_files

# Copy with metadata preservation
copy_file("source.txt", "dest.txt", preserve_metadata=True)

# Calculate and verify hashes
hash_value = calculate_file_hash("file.txt", algorithm="sha256")

# Verify copies
is_valid = verify_copied_files("source_dir", "backup_dir")
```

## Usage Examples

### Basic File Operations

```python
from dazzle_filekit import copy_file, move_file

# Simple copy
copy_file("input.txt", "output.txt")

# Copy with options
copy_file("source.txt", "backup/dest.txt",
          preserve_metadata=True,
          overwrite=False)

# Move file
move_file("old_location.txt", "new_location.txt")
```

### Hash Calculation and Verification

```python
from dazzle_filekit import calculate_file_hash, verify_file_hash

# Calculate hash
sha256_hash = calculate_file_hash("file.txt", algorithm="sha256")
print(f"SHA256: {sha256_hash}")

# Verify against known hash
is_valid = verify_file_hash("file.txt", expected_hash, algorithm="sha256")
if not is_valid:
    print("File has been modified!")
```

### Cross-Platform Path Handling

```python
from dazzle_filekit import normalize_path, is_same_file

# Normalize paths (handles .. and .)
path = normalize_path("/some/path/../file.txt")
# Result: /some/file.txt

# Compare paths reliably across platforms
if is_same_file(path1, path2):
    print("Same file!")
```

### Directory Synchronization

```python
from dazzle_filekit import sync_directories, compare_directories

# Compare directories
differences = compare_directories("source_dir", "backup_dir")
print(f"Files only in source: {differences.source_only}")
print(f"Files only in backup: {differences.backup_only}")
print(f"Modified files: {differences.modified}")

# Synchronize directories
sync_directories("source_dir", "backup_dir",
                 verify_hashes=True,
                 preserve_metadata=True)
```

## API Reference

### File Operations

- `copy_file(source, dest, preserve_metadata=True, overwrite=False)`
- `move_file(source, dest, preserve_metadata=True, overwrite=False)`
- `verify_copied_files(source_dir, dest_dir, algorithm="sha256")`

### Hash Functions

- `calculate_file_hash(filepath, algorithm="sha256")`
- `verify_file_hash(filepath, expected_hash, algorithm="sha256")`
- `calculate_directory_hash(dirpath, algorithm="sha256")`

### Path Operations

- `normalize_path(path)`
- `is_same_file(path1, path2)`
- `is_unc_path(path)` (Windows-specific)
- `parse_unc_path(path)` (Windows-specific)

## Used By

**dazzle-filekit** powers these DazzleTools:
- **preserve**: Verified file backups with hash checking
- **dazzlelink**: File reference management
- **relinker** (future): Intelligent file organization

## Platform Support

| Platform | Status | Notes |
|----------|--------|-------|
| Windows | ✅ Full Support | Including UNC paths |
| Linux | ✅ Full Support | All features available |
| macOS | ✅ Full Support | All features available |
| Python | 3.8+ | Tested on 3.8-3.12 |

## Contributing

See the [main repository](https://github.com/DazzleLib/dazzle-filekit) for contribution guidelines.

## License

MIT License - See [LICENSE](https://github.com/DazzleLib/dazzle-filekit/blob/main/LICENSE) for details.
