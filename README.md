# Zed for Golang

Production-ready Zed editor configuration optimized for Go development, with comprehensive linting, debugging, profiling, and AI integration.

A complete alternative to GoLand with native debugging UI, GPT-4o integration, and industry-standard tools.

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
- Inline documentation

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

### 🛠️ Helper Scripts
Included in `.go-helpers/`:
- `go-debug` - Interactive debugging
- `go-profile` - CPU/Memory profiling
- `go-bench` - Benchmark runner
- `go-coverage` - Coverage reports
- `go-godoc` - Documentation server
- `go-swagger` - API documentation

## Installation

### 1. Copy Settings
```bash
cp settings.json ~/.config/zed/settings.json
```

### 2. Copy Keybindings (Optional)
```bash
cp keymap.json ~/.config/zed/keymap.json
```

### 3. Install Required Tools

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

### 4. Linting Configuration
Copy the golangci-lint config:
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
- Text auto-fills search box (like JetBrains!)

## Configuration

### Key Settings
```json
"autosave": "on_window_change",          // Save on window switch
"seed_search_query_from_cursor": "always", // Auto-fill search
"use_smartcase_search": true,            // Smart case matching
"vertical_scroll_margin": 10,            // Context lines while scrolling
```

### LSP Settings
gopls is configured with:
- Error checking (errorsAs, httpResponse, lostcancel, printf, unreachable)
- Performance analysis (fieldalignment, nilness)
- Code generation support
- Comprehensive hints (types, parameters, ranges)

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

| Tool | Version | Purpose |
|------|---------|---------|
| dlv | Latest | Debugging |
| gopls | Bundled | Language server |
| golangci-lint | v1.64.8+ | Linting |
| gotestsum | Latest | Test formatting |
| goimports | Latest | Import management |

## Performance Tips

1. **Faster linting**: golangci-lint runs on save
2. **Better completion**: Fuzzy matching + deep completion enabled
3. **Reduced noise**: File scanning excludes node_modules, .git, etc.
4. **Semantic highlighting**: Enables better code understanding

## Comparison with GoLand

| Feature | GoLand | Zed |
|---------|--------|-----|
| Debugging UI | ✅ Excellent | ✅ Native DAP |
| Code Quality | ✅ Great | ✅ golangci-lint (100+ checks) |
| Refactoring | ✅✅ Advanced | ✅ gopls basic |
| Performance | Good | ✅✅ Excellent |
| AI Assistant | Claude (paid) | ✅ GPT-4o |
| Cost | $$$$ | Free |

## Troubleshooting

**Breakpoints not working?**
- Ensure you're in a Go file
- F4 might need a second press
- Check `~/.config/zed/settings.json` has debugger config

**gopls not analyzing?**
- Run: `cd your-project && go list ./...`
- gopls needs to index the module

**Profiling tool missing?**
- Install: `go install github.com/go-delve/delve/cmd/dlv@latest`

## Resources

- [Zed Documentation](https://zed.dev/docs)
- [gopls Documentation](https://github.com/golang/tools/tree/master/gopls)
- [golangci-lint Linters](https://golangci-lint.run/usage/linters/)
- [Delve Debugger](https://github.com/go-delve/delve)

## License

MIT - Use freely, modify, distribute

## Contributing

Found a better setting? Improved the config? PRs welcome!

## Author

Created for professional Go development in Zed.

---

**Questions?** Check the `.go-helpers/` directory for detailed guides and helper scripts.
