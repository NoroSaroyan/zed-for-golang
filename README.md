# Zed for Golang

My personal Zed editor configuration optimized for Go development.

Production-ready setup with comprehensive linting, debugging, profiling, and AI integration.

## Features

### 🎯 Go Development
- **gopls** with 13+ advanced analyses (nilness, error checking, unused code detection)
- **golangci-lint** with 100+ linters for code quality, security, and performance
- **goimports** automatic import formatting
- **Delve** native visual debugger (F4 to start)
- Code lenses for test running, vulnerability checks, code generation

### 🔍 Debugging & Profiling
- F4: Start visual debugging with breakpoints
- F10/F11: Step over/into code
- CPU/Memory profiling with pprof
- Benchmark running with gotestsum
- Test coverage visualization

### 🤖 AI Integration
- **GPT-4o** as default AI model
- Code completion and suggestions

### 🔧 Editor Experience
- Auto-save on window change
- Smart case search with seed from cursor
- 10-line scroll margin for context
- Inline git blame with commit summaries
- File scanning with smart exclusions

### 📝 Language Support
- Go (primary)
- TypeScript/TSX with Prettier
- Rust with clippy checks
- JSON, YAML, Java, Markdown

## Installation

### 1. Copy Settings
```bash
cp settings.json ~/.config/zed/settings.json
```

### 2. Install Required Tools

**Essential:**
```bash
# Delve debugger
go install github.com/go-delve/delve/cmd/dlv@latest

# golangci-lint
go install github.com/golangci/golangci-lint/cmd/golangci-lint@latest

# gotestsum
go install gotest.tools/gotestsum@latest
```

**Optional:**
```bash
# Documentation server
go install golang.org/x/tools/cmd/godoc@latest

# API documentation
go install github.com/swaggo/swag/cmd/swag@latest

# Benchmark comparison
go install golang.org/x/perf/cmd/benchstat@latest
```

### 3. Linting Configuration (Optional)
```bash
cp .golangci.yml ~/.golangci.yml
```

## Quick Start

### Debugging
1. Open a Go file
2. Press **F4** to start debugging
3. Click line numbers to set breakpoints
4. F10/F11 to step through code

### Profiling
```bash
go-profile cpu      # CPU profiling
go-profile mem      # Memory profiling
# Opens pprof at localhost:8080
```

### Testing & Coverage
```bash
go-coverage ./...   # Generates HTML coverage report
```

### Search
- Select text or position cursor on a word
- Press **Cmd+F**
- Text auto-fills search box

## Configuration

### Key Settings
```json
"autosave": "on_window_change",
"seed_search_query_from_cursor": "always",
"use_smartcase_search": true,
"vertical_scroll_margin": 10
```

### Go-Specific
```json
"tab_size": 4,
"hard_tabs": true,
"formatter": { "external": { "command": "goimports" } }
```

## Keyboard Shortcuts

| Shortcut | Action |
|----------|--------|
| F4 | Start/Open debugger |
| F10 | Step over |
| F11 | Step into |
| Shift+F11 | Step out |
| F9 | Continue to breakpoint |
| Cmd+Shift+D | Toggle breakpoint |
| Cmd+F | Find (auto-fills from cursor) |
| Cmd+. | Quick actions/refactoring |

## Tools & Dependencies

| Tool | Purpose |
|------|---------|
| dlv | Debugging |
| gopls | Language server |
| golangci-lint | Linting |
| gotestsum | Test formatting |
| goimports | Import management |
