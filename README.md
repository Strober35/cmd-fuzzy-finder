# Command Fuzzy Finder (cmd)

[![License: GPLv3](https://img.shields.io/badge/License-GPLv3-blue.svg)](https://www.gnu.org/licenses/gpl-3.0)
![Bash Version](https://img.shields.io/badge/Bash-4.0%2B-brightgreen)
![Platform](https://img.shields.io/badge/Platform-Linux%20%7C%20macOS-lightgrey)
![Multilingual](https://img.shields.io/badge/Multilingual-EN%20%7C%20PT-blue)

A powerful and intuitive command-line tool for fuzzy searching PATH commands, written purely in Bash with no external dependencies.

<p align="center">
  <img src="https://raw.githubusercontent.com/felipefacundes/cmd-fuzzy-finder/main/screenshot.png" alt="cmd demonstration" width="800">
</p>

## ✨ Key Features

- 🔍 **Real-time fuzzy search** - Find commands as you type
- 🎨 **Colorful and intuitive interface** - Clear and pleasant visualization
- ⚡ **No external dependencies** - Pure Bash only
- 🌍 **Multilingual support** - English and Portuguese (auto-detected)
- 📋 **Execution history** - Keeps track of used commands
- 🎯 **Quick navigation** - Arrow keys for navigation
- 📁 **Multiple usage modes** - Interactive, initial search, and simple list

## 🚀 Installation

### Quick Method (Recommended)
```bash
# Download the script
curl -L -o cmd https://raw.githubusercontent.com/felipefacundes/cmd-fuzzy-finder/main/cmd

# Make it executable
chmod +x cmd

# Move to PATH (optional but recommended)
sudo mv cmd /usr/local/bin/
```

### Repository Clone Method
```bash
git clone https://github.com/felipefacundes/cmd-fuzzy-finder.git
cd cmd-fuzzy-finder
chmod +x cmd
sudo cp cmd /usr/local/bin/
```

### Package Installation (Future)
```bash
# Coming soon to repositories
```

## 📖 Usage

### Full Interactive Mode
```bash
# Empty interface for interactive search
cmd

# Interface with initial search term
cmd snap
```

### Simple List Mode
```bash
# Non-interactive list of commands
cmd --list fire
cmd -l python
```

### Other Modes
```bash
# Show execution history
cmd --history
cmd -H

# Show complete documentation
cmd --docs
cmd -d

# Show help
cmd --help
cmd -h
```

## 🎮 Shortcuts and Navigation

| Key | Action |
|-------|------|
| `↑ ↓` | Navigate between commands |
| `Enter` | Execute selected command |
| `Backspace` | Delete search character |
| `Ctrl+C` | Exit program |
| `Home` | Go to first result |
| `End` | Go to last result |

## 🌍 Internationalization

The script automatically detects the system language based on the `$LANG` variable:

- **Portuguese**: Activated when `LANG` contains `pt_` (e.g., `pt_BR.UTF-8`)
- **English**: Default language (fallback)

To force a specific language:
```bash
# Force Portuguese
LANG=pt_BR.UTF-8 cmd

# Force English
LANG=en_US.UTF-8 cmd
```

## ⚙️ Configuration

### Configuration Variables
The following variables can be adjusted in the code:

```bash
# Maximum number of results displayed
MAX_RESULTS=35

# Number of commands visible in the interface
SHOW_COUNT=10

# History file
HISTORY_FILE="$HOME/.cmd_history"

# Maximum history size
HISTORY_MAX=1000
```

### Custom Colors
The script uses ANSI codes for colors. You can customize:

```bash
RED='\033[0;31m'      # Selected command
GREEN='\033[0;32m'    # Highlighted search text
YELLOW='\033[1;33m'   # Search text
BLUE='\033[0;34m'     # Counters and information
MAGENTA='\033[0;35m'  # Instructions
CYAN='\033[0;36m'     # Title
```

## 🔧 How It Works

### Search Algorithm
1. **Collection**: Gets all executable commands from PATH
2. **Indexing**: Removes duplicates and sorts alphabetically
3. **Filtering**: Case-insensitive substring search in real-time
4. **Presentation**: Displays results with highlighted matches

### Program Flow
```
Start → Check mode → Collect commands → Main loop
     ↓                            ↑
  Execution ← User selection ← Interface
```

## 📊 Performance

- **Initialization**: < 0.1s (PATH commands cache)
- **Search**: Instantaneous (in-memory filtering)
- **Memory**: < 5MB (depends on number of commands in PATH)

## 🛠️ Development

### Code Structure
```
cmd-fuzzy-finder/
├── cmd                    # Main script
├── README.md             # This documentation
├── LICENSE               # GPLv3 License
└── examples/             # Usage examples
```

### Adding New Languages
To add support for a new language:

1. Add a new condition in `$LANG` detection:
```bash
elif [[ "${LANG,,}" =~ es_ ]]; then
    # Spanish messages
    MESSAGES=(
        [title]="=== Buscador Difuso de Comandos ==="
        # ... remaining messages
    )
```

2. Translate all keys of the `MESSAGES` array

### Testing
```bash
# Basic test
./cmd --help

# Functionality test
./cmd --list bash

# Internationalization test
LANG=pt_BR.UTF-8 ./cmd
LANG=en_US.UTF-8 ./cmd
```

## 🤝 Contributing

Contributions are welcome! Please:

1. Fork the repository
2. Create a branch for your feature (`git checkout -b feature/amazing`)
3. Commit your changes (`git commit -am 'Add amazing feature'`)
4. Push to the branch (`git push origin feature/amazing`)
5. Open a Pull Request

### Areas for Contribution
- ✅ Add new languages
- ✅ Improve performance
- ✅ New features
- ✅ Bug fixes
- ✅ Better documentation

## 📝 License

This project is licensed under the **GPLv3**. See the [LICENSE](LICENSE) file for details.

```
Copyright (C) 2024 Felipe Facundes

This program is free software: you can redistribute it and/or modify
it under the terms of the GNU General Public License as published by
the Free Software Foundation, either version 3 of the License, or
(at your option) any later version.
```

## 🙏 Credits

- **Author**: [Felipe Facundes](https://github.com/felipefacundes)
- **Inspiration**: Tools like `fzf`, `rofi`, and `dmenu`
- **Contributors**: [Contributors list](https://github.com/felipefacundes/cmd-fuzzy-finder/graphs/contributors)

## 🐛 Reporting Bugs

Found a bug? Please:

1. Check if there's already an open issue
2. Use the bug report template
3. Include system information:
   ```bash
   echo "System: $(uname -a)"
   echo "Bash: $(bash --version | head -1)"
   echo "PATH: $(echo $PATH | tr ':' '\n' | wc -l) directories"
   ```

## 🌟 Stars

If you found this tool useful, consider giving it a ⭐ on the repository!

## 📞 Support

- **Issues**: [GitHub Issues](https://github.com/felipefacundes/cmd-fuzzy-finder/issues)
- **Discussions**: [GitHub Discussions](https://github.com/felipefacundes/cmd-fuzzy-finder/discussions)
- **Email**: [felipe.facundes@gmail.com](mailto:felipe.facundes@gmail.com)

## 📈 Roadmap

- [ ] Plugin support
- [ ] Persistent command cache
- [ ] ZSH/Fish integration
- [ ] Enhanced TUI interface
- [ ] Batch mode for scripts
- [ ] More languages (ES, FR, DE, etc.)

---

<p align="center">
  <em>Find commands faster, work smarter 🚀</em>
</p>