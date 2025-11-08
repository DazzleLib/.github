# dazzle-tree-lib

**Tree structure utilities for hierarchical data**

[![PyPI](https://img.shields.io/pypi/v/dazzle-tree-lib)](https://pypi.org/project/dazzle-tree-lib/)
[![GitHub](https://img.shields.io/badge/GitHub-DazzleLib/dazzle--tree--lib-blue?logo=github)](https://github.com/DazzleLib/dazzle-tree-lib)

## Installation

```bash
pip install dazzle-tree-lib
```

## Features

- **Generic Tree Structures**: Flexible tree data structures for any hierarchical data
- **Traversal Algorithms**: DFS, BFS, and iterative traversal methods
- **Tree Visualization**: Pretty-printing and visualization tools
- **Path Operations**: Navigate tree structures with path-like syntax
- **Node Manipulation**: Add, remove, and query nodes efficiently
- **Serialization**: Save and load tree structures

## Quick Start

```python
from dazzle_tree_lib import Tree, TreeNode

# Create and manipulate tree structures
root = TreeNode("root")
child1 = root.add_child("child1")
child2 = root.add_child("child2")
grandchild = child1.add_child("grandchild")

# Traverse the tree
for node in root.traverse_dfs():
    print(node.value)
```

## Usage Examples

### Building Trees

```python
from dazzle_tree_lib import Tree

# Create a tree
tree = Tree()
root = tree.add_node("root", parent=None)
child1 = tree.add_node("child1", parent=root)
child2 = tree.add_node("child2", parent=root)
grandchild = tree.add_node("grandchild1", parent=child1)
```

### Tree Traversal

```python
# Depth-First Search (DFS)
for node in tree.traverse_dfs():
    print(f"DFS: {node.value}")

# Breadth-First Search (BFS)
for node in tree.traverse_bfs():
    print(f"BFS: {node.value}")

# Iterative traversal with level tracking
for node, level in tree.traverse_with_level():
    print(f"{'  ' * level}{node.value}")
```

### Tree Visualization

```python
# Print tree structure
tree.print_tree()
# Output:
# root
# ├── child1
# │   └── grandchild1
# └── child2

# Get tree as string
tree_str = tree.to_string()
```

### Path Operations

```python
# Find node by path
node = tree.find_path("/root/child1/grandchild1")

# Get path to node
path = tree.get_path(grandchild)
# Returns: "/root/child1/grandchild1"
```

### Node Queries

```python
# Get all children
children = node.get_children()

# Get parent
parent = node.get_parent()

# Check if leaf node
if node.is_leaf():
    print("This is a leaf node")

# Get all descendants
descendants = node.get_descendants()

# Get siblings
siblings = node.get_siblings()
```

## API Reference

### Tree Class

- `add_node(value, parent=None)`: Add a node to the tree
- `remove_node(node)`: Remove a node and its subtree
- `find_path(path)`: Find node by path string
- `get_path(node)`: Get path string to node
- `traverse_dfs()`: Depth-first traversal generator
- `traverse_bfs()`: Breadth-first traversal generator
- `traverse_with_level()`: Traversal with level information
- `print_tree()`: Pretty-print tree structure
- `to_string()`: Convert tree to string representation

### TreeNode Class

- `add_child(value)`: Add child node
- `remove_child(node)`: Remove child node
- `get_children()`: Get list of child nodes
- `get_parent()`: Get parent node
- `get_descendants()`: Get all descendant nodes
- `get_siblings()`: Get sibling nodes
- `is_leaf()`: Check if node is a leaf
- `is_root()`: Check if node is the root

## Use Cases

**dazzle-tree-lib** is used for:
- Directory tree representations
- Hierarchical data structures
- Menu and navigation systems
- Organization charts
- File system abstractions
- Decision trees
- DOM-like structures

## Used By

**dazzle-tree-lib** powers these DazzleTools:
- **listall**: Directory tree visualization
- Directory scanning and comparison tools
- Hierarchical data processing utilities

## Platform Support

| Platform | Status | Notes |
|----------|--------|-------|
| Windows | ✅ Full Support | All features available |
| Linux | ✅ Full Support | All features available |
| macOS | ✅ Full Support | All features available |
| Python | 3.8+ | Tested on 3.8-3.12 |

## Performance

Tree operations are optimized for:
- **Fast lookups**: O(log n) path-based searches
- **Efficient traversal**: Iterator-based traversal with minimal memory overhead
- **Memory efficient**: Lazy evaluation where possible

## Contributing

See the [main repository](https://github.com/DazzleLib/dazzle-tree-lib) for contribution guidelines.

## License

MIT License - See [LICENSE](https://github.com/DazzleLib/dazzle-tree-lib/blob/main/LICENSE) for details.
