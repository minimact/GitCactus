# 🤝 Contributing to Cactus Browser

First off, thank you for considering contributing to Cactus Browser! 🌵

We're building the future of desktop applications - a world where GitHub is the CDN, git push is the deployment, and servers are optional. Your contributions help make this vision a reality.

## 🌟 Ways to Contribute

### 🐛 Report Bugs
Found a bug? Help us squash it!

**Before submitting:**
- Check if the issue already exists in [Issues](https://github.com/minimact/GitCactus/issues)
- Collect information about the bug (OS, browser version, steps to reproduce)

**Submit a bug report:**
1. Go to [Issues](https://github.com/minimact/GitCactus/issues/new)
2. Use the "Bug Report" template
3. Include:
   - Clear description of the problem
   - Steps to reproduce
   - Expected vs actual behavior
   - Screenshots/error messages if applicable
   - Environment details (OS, Cactus version)

### 💡 Suggest Features
Have an idea to make Cactus Browser even better?

**Feature requests should include:**
- Clear description of the feature
- Use cases (why is this valuable?)
- Proposed implementation (if you have ideas)
- Examples from other tools (if applicable)

### 📝 Improve Documentation
Documentation is crucial for adoption!

**Areas needing help:**
- Typo fixes and clarifications
- More examples and tutorials
- API documentation
- Video tutorials
- Translation to other languages

### 🔧 Submit Code Changes
Ready to write some code? Awesome!

**Areas needing development:**
- 🍎 **macOS support** - Port Tauri build to macOS
- 🐧 **Linux support** - Port Tauri build to Linux
- 📱 **Mobile support** - Explore Tauri mobile preview
- 🎨 **UI/UX improvements** - Better address bar, settings panel, etc.
- ⚡ **Performance** - Optimize compilation, caching, reconciliation
- 🧪 **Testing** - Unit tests, integration tests, E2E tests
- 🔌 **Extensions** - Plugin system for custom protocols

## 🚀 Development Setup

### Prerequisites

**Required:**
- **Rust** - Latest stable version
  ```bash
  curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh
  ```
- **.NET 8 SDK** - Download from [dotnet.microsoft.com](https://dotnet.microsoft.com/download/dotnet/8.0)
- **Node.js** (v18+) and **pnpm**
  ```bash
  npm install -g pnpm
  ```

**Optional (for contributors):**
- **Git** - For version control
- **VS Code** - Recommended editor with Rust Analyzer extension

### Getting Started

1. **Fork the repository**
   - Click "Fork" at the top right of [github.com/minimact/GitCactus](https://github.com/minimact/GitCactus)

2. **Clone your fork**
   ```bash
   git clone https://github.com/YOUR_USERNAME/GitCactus.git
   cd GitCactus
   ```

3. **Add upstream remote**
   ```bash
   git remote add upstream https://github.com/minimact/GitCactus.git
   ```

4. **Install dependencies**
   ```bash
   pnpm install
   ```

5. **Build the C# runtime**
   ```bash
   # Windows
   ./build-runtime.bat

   # macOS/Linux (coming soon)
   ./build-runtime.sh
   ```

6. **Run in development mode**
   ```bash
   pnpm tauri dev
   ```

### Project Structure

```
GitCactus/
├── src/                          # Tauri frontend (React + Vite)
│   ├── core/
│   │   ├── github-loader.ts      # Load TSX from GitHub
│   │   ├── gh-protocol.ts        # gh:// URL parsing
│   │   └── signalm/
│   │       └── TauriTransport.ts # SignalM² Tauri transport
│   ├── App-phase3.tsx            # Main UI
│   └── main.tsx                  # Entry point
├── src-tauri/                    # Tauri backend (Rust)
│   └── src/
│       ├── main.rs               # Tauri setup
│       ├── runtime.rs            # C# runtime execution
│       └── signalm.rs            # SignalM² hub (component registry)
├── minimact-runtime/             # C# runtime (Native AOT)
│   ├── ComponentExecutor.cs      # Execute components
│   ├── DynamicCompiler.cs        # Roslyn compilation
│   ├── VNodeSerializer.cs        # VNode → JSON
│   └── Program.cs                # Entry point
├── public/
│   └── minimact-client-runtime.js # Client-runtime bundle
└── docs/                         # Documentation
    └── CACTUS_BROWSER_CLIENT_RUNTIME_INTEGRATION.md
```

## 📋 Contribution Workflow

### 1. Create a Branch

Always create a new branch for your changes:

```bash
git checkout -b feature/your-feature-name
# or
git checkout -b fix/bug-description
```

**Branch naming conventions:**
- `feature/` - New features
- `fix/` - Bug fixes
- `docs/` - Documentation updates
- `refactor/` - Code refactoring
- `test/` - Adding or updating tests

### 2. Make Your Changes

**Code Style:**
- **Rust**: Follow `rustfmt` formatting (run `cargo fmt`)
- **TypeScript**: Follow project's ESLint/Prettier config
- **C#**: Follow standard C# conventions

**Commit Messages:**
Use clear, descriptive commit messages:

```
<type>: <short summary>

<optional detailed description>

<optional footer>
```

**Types:**
- `feat:` - New feature
- `fix:` - Bug fix
- `docs:` - Documentation changes
- `style:` - Formatting, missing semicolons, etc.
- `refactor:` - Code restructuring
- `test:` - Adding tests
- `chore:` - Maintenance tasks

**Examples:**
```
feat: add macOS support for Tauri build

- Update tauri.conf.json for macOS target
- Add macOS-specific runtime path resolution
- Test on macOS 13.0+

Closes #42
```

```
fix: resolve component state persistence bug

Components were being garbage collected after initial render.
Now stored in component registry to enable re-renders.

Fixes #15
```

### 3. Test Your Changes

**Manual Testing:**
1. Run the app: `pnpm tauri dev`
2. Test your changes thoroughly
3. Test edge cases
4. Verify no regressions

**Automated Testing (when available):**
```bash
# Run Rust tests
cargo test

# Run TypeScript tests
pnpm test

# Run C# tests
dotnet test
```

### 4. Keep Your Branch Updated

Regularly sync with upstream:

```bash
git fetch upstream
git rebase upstream/main
```

### 5. Submit a Pull Request

**Before submitting:**
- [ ] Code follows project style
- [ ] Changes are tested
- [ ] Documentation is updated (if needed)
- [ ] Commit messages are clear
- [ ] Branch is up to date with `main`

**Submit PR:**
1. Push your branch: `git push origin feature/your-feature-name`
2. Go to [github.com/minimact/GitCactus/pulls](https://github.com/minimact/GitCactus/pulls)
3. Click "New Pull Request"
4. Select your branch
5. Fill out the PR template:
   - Clear title
   - Description of changes
   - Related issues (e.g., "Closes #42")
   - Screenshots (if UI changes)
   - Testing done

**PR Template:**
```markdown
## Description
Brief description of what this PR does.

## Type of Change
- [ ] Bug fix
- [ ] New feature
- [ ] Documentation update
- [ ] Refactoring
- [ ] Other (describe)

## Related Issues
Closes #XXX

## How Has This Been Tested?
Describe the testing you've done.

## Screenshots (if applicable)
Add screenshots for UI changes.

## Checklist
- [ ] Code follows project style
- [ ] Self-review completed
- [ ] Documentation updated
- [ ] No new warnings
- [ ] Tests added/updated
```

### 6. Code Review

**What to expect:**
- Maintainers will review your PR
- You may be asked to make changes
- Discussion may happen in PR comments
- Be patient - we're all volunteers!

**Responding to feedback:**
- Be respectful and constructive
- Ask questions if unclear
- Make requested changes
- Push updates to the same branch

## 🎯 Good First Issues

Looking for a place to start? Check out issues labeled:
- [`good first issue`](https://github.com/minimact/GitCactus/labels/good%20first%20issue) - Great for newcomers
- [`help wanted`](https://github.com/minimact/GitCactus/labels/help%20wanted) - We need help here
- [`documentation`](https://github.com/minimact/GitCactus/labels/documentation) - Improve docs

## 🐛 Debugging Tips

### Rust Backend
```bash
# View Tauri logs
RUST_LOG=debug pnpm tauri dev

# Tauri logs are in src-tauri/target/debug/
```

### C# Runtime
```bash
# Runtime logs go to console
# Check temp files: %TEMP%\cactus-request-*.json
```

### Frontend
```bash
# Open DevTools in Tauri window (Ctrl+Shift+I or Cmd+Option+I)
# Check console for client-runtime logs
```

## 📜 Code of Conduct

### Our Pledge

We are committed to providing a welcoming and inspiring community for all.

**We pledge to:**
- Be respectful and inclusive
- Welcome newcomers
- Accept constructive criticism
- Focus on what's best for the community
- Show empathy towards others

**Unacceptable behavior:**
- Harassment or discrimination
- Trolling or inflammatory comments
- Personal or political attacks
- Publishing others' private information
- Any conduct inappropriate in a professional setting

**Enforcement:**
Instances of unacceptable behavior may be reported to the project maintainers. All complaints will be reviewed and investigated promptly and fairly.

## 🏆 Recognition

Contributors who make significant contributions will be:
- Added to the README contributors section
- Recognized in release notes
- Given credit in documentation

## 💬 Questions?

- **GitHub Discussions** - [Ask questions](https://github.com/minimact/GitCactus/discussions)
- **Discord** - Join our community (link coming soon)
- **Email** - Reach out to maintainers (contact info in repo)

## 📖 Additional Resources

- [Tauri Documentation](https://tauri.app/)
- [Minimact Documentation](https://github.com/minimact/minimact)
- [Rust Book](https://doc.rust-lang.org/book/)
- [TypeScript Handbook](https://www.typescriptlang.org/docs/)
- [C# Documentation](https://docs.microsoft.com/en-us/dotnet/csharp/)

## 🌵 Philosophy

Remember, we're building something wild and free - like the web used to be. We value:
- **Simplicity** over complexity
- **Local-first** over cloud-dependent
- **Open source** over proprietary
- **Fun** over seriousness (but quality code is serious!)

Welcome to the frontier, partner. Let's build something amazing together! 🤠

---

**Thank you for contributing to Cactus Browser!** 🌵

If you like what we're building, don't forget to [⭐ star the repo](https://github.com/minimact/GitCactus)!
