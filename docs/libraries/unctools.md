# UNCtools

**Windows UNC path handling and network drive utilities**

[![PyPI](https://img.shields.io/pypi/v/unctools)](https://pypi.org/project/unctools/)
[![GitHub](https://img.shields.io/badge/GitHub-DazzleLib/UNCtools-blue?logo=github)](https://github.com/DazzleLib/UNCtools)

## Installation

```bash
pip install unctools
```

## Features

- **Parse UNC Paths**: Extract server, share, and path components
- **Network Drive Detection**: Identify mapped network drives
- **Drive Letter Conversion**: Convert between drive letters and UNC paths
- **Long Path Support**: Handle Windows paths >260 characters
- **Cross-Platform Safe**: Graceful no-ops on Unix systems

## Quick Start

```python
from unctools import is_unc_path, parse_unc_path, get_unc_path

# Check if path is UNC
if is_unc_path(r"\\server\share\file.txt"):
    server, share, path = parse_unc_path(r"\\server\share\file.txt")
    print(f"Server: {server}, Share: {share}, Path: {path}")

# Convert drive letter to UNC path
unc_path = get_unc_path("Z:\\")
# Returns: \\server\share (if Z: is mapped to a network share)
```

## Usage Examples

### Parsing UNC Paths

```python
from unctools import parse_unc_path

# Parse a UNC path
path = r"\\fileserver\documents\projects\report.docx"
server, share, rel_path = parse_unc_path(path)

print(f"Server: {server}")       # fileserver
print(f"Share: {share}")         # documents
print(f"Path: {rel_path}")       # projects\report.docx
```

### Network Drive Detection

```python
from unctools import is_network_drive, get_network_drives

# Check if drive is network drive
if is_network_drive("Z:"):
    print("Z: is a network drive")

# Get all mapped network drives
network_drives = get_network_drives()
for drive, unc_path in network_drives.items():
    print(f"{drive} -> {unc_path}")
```

### Drive Letter Conversion

```python
from unctools import get_unc_path, get_drive_letter

# Convert drive letter to UNC
unc = get_unc_path("Z:\\folder\\file.txt")
# Returns: \\server\share\folder\file.txt

# Convert UNC to drive letter (if mapped)
drive = get_drive_letter(r"\\server\share")
# Returns: Z: (if that UNC is mapped to Z:)
```

### Long Path Handling

```python
from unctools import normalize_long_path

# Handle paths longer than 260 characters
long_path = "C:\\" + "a" * 300 + "\\file.txt"

# Normalize to use \\?\ prefix
normalized = normalize_long_path(long_path)
# Returns: \\?\C:\aaa...aaa\file.txt

# Now can use with Windows file operations
with open(normalized, 'r') as f:
    content = f.read()
```

## API Reference

### Path Analysis

- `is_unc_path(path)`: Check if path is a UNC path
- `parse_unc_path(path)`: Parse UNC path into components
- `is_network_drive(drive_letter)`: Check if drive is network-mapped

### Path Conversion

- `get_unc_path(path)`: Convert local path to UNC if possible
- `get_drive_letter(unc_path)`: Find drive letter for UNC path
- `normalize_long_path(path)`: Add \\?\ prefix for long paths

### Network Utilities

- `get_network_drives()`: Get dictionary of all network drives
- `get_drive_mapping(drive_letter)`: Get UNC path for specific drive

## Cross-Platform Behavior

**Windows**:
- Full functionality for all operations
- Handles UNC paths, network drives, long paths

**Linux/macOS**:
- All functions return safe defaults (no-op behavior)
- `is_unc_path()` always returns False
- `get_network_drives()` returns empty dictionary
- No exceptions raised, just graceful degradation

## Used By

**UNCtools** is used by:
- **dazzle-filekit**: Windows UNC path support
- Windows-focused file management tools
- Cross-platform applications that need Windows network path handling

## Platform Support

| Platform | Status | Notes |
|----------|--------|-------|
| Windows | ✅ Full Support | All features available |
| Linux | ⚠️ No-op | Returns safe defaults |
| macOS | ⚠️ No-op | Returns safe defaults |
| Python | 3.8+ | Tested on 3.8-3.12 |

## Why UNCtools?

Working with Windows network paths is surprisingly complex:
- UNC paths have special syntax (`\\server\share`)
- Drive letters can map to network shares
- Path length limits require special handling
- Need to detect and convert between formats

UNCtools handles all of this so you don't have to.

## Contributing

See the [main repository](https://github.com/DazzleLib/UNCtools) for contribution guidelines.

## License

MIT License - See [LICENSE](https://github.com/DazzleLib/UNCtools/blob/main/LICENSE) for details.
