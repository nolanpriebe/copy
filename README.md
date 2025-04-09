# Copy - WSL Clipboard File Manager for LLMs

A powerful clipboard utility for WSL that makes it easy to copy file contents and project structures to your clipboard, optimized for sharing with Large Language Models like Claude, ChatGPT, and GitHub Copilot.

## Features

- **Copy File Contents**: Easily capture the contents of multiple files at once
- **LLM-Optimized Formats**: Format output as markdown with proper language highlighting
- **Project Context**: Generate directory trees, project summaries, and git info
- **Smart Filtering**: Target specific file types or exclude test files
- **Token Optimization**: Compress whitespace and track token usage for LLM context windows
- **Ignore Patterns**: Powerful .gitignore-style file filtering with defaults for common project files

## Installation

1. **Save the script**:
   ```bash
   mkdir -p ~/bin
   nano ~/bin/copy
   # Paste the script content, then save (Ctrl+X, Y, Enter)
   ```

2. **Make it executable**:
   ```bash
   chmod +x ~/bin/copy
   ```

3. **Add to your PATH** (if not already there):
   ```bash
   echo 'export PATH="$HOME/bin:$PATH"' >> ~/.bashrc
   source ~/.bashrc
   ```

4. **Create default ignore file** (optional):
   ```bash
   copy --create-ignore
   ```

## Basic Usage

```bash
# Copy contents of all files in current directory (recursive)
copy

# Copy only file paths instead of contents
copy --paths-only

# Only copy files in the current directory (non-recursive)
copy --flat

# Get help
copy --help
```

## LLM-Optimized Features

```bash
# Generate a markdown-formatted output (great for code sharing in LLMs)
copy --format markdown

# Show directory structure
copy --tree

# Get project summary and stats
copy --summary

# Include git info (branch, recent commits, changes)
copy --git-info

# Focus on important files only (README, main.*, etc.)
copy --important

# Show estimated token count for LLM context windows
copy
# Output will include: "Estimated tokens: 1,234"
```

## Advanced Usage

```bash
# Only include Python files
copy --filter "*.py"

# Exclude test files
copy --exclude "test_*"

# Limit directory depth
copy --max-depth 2

# Include line numbers in source code
copy --line-numbers

# Perfect for LLM: markdown format with important files only and git info
copy --format markdown --important --git-info

# Optimize token usage for large projects
copy --compress-whitespace --format markdown
```

## Ignore File (.copyignore)

The tool uses a `.copyignore` file similar to `.gitignore`. Create a default one with common patterns:

```bash
copy --create-ignore
```

Then customize it by editing `.copyignore` in your project directory.

## Options Reference

| Option | Description |
|--------|-------------|
| `--paths-only` | Copy file paths instead of contents |
| `--flat` | Only process current directory (non-recursive) |
| `--format` | Output format: plain, markdown, or json |
| `--tree` | Generate directory structure tree |
| `--summary` | Generate project summary |
| `--important` | Include only important files |
| `--filter "*.ext"` | Include only files matching patterns |
| `--exclude "pattern"` | Exclude files matching patterns |
| `--git-info` | Include git repository information |
| `--line-numbers` | Include line numbers in source code |
| `--max-depth N` | Limit directory traversal depth |
| `--max-size N` | Maximum file size in MB (default: 10) |
| `--compress-whitespace` | Reduce tokens by compressing blank lines |
| `-i, --ignore-file` | Specify a custom ignore file |
| `-d, --directory` | Specify source directory |

## Requirements

- WSL (Windows Subsystem for Linux)
- Python 3.x

## License

MIT

## Acknowledgements

Created to streamline sharing code with AI assistants.
