# Codaicli: AI-powered CLI assistant for code projects

Codaicli is an intelligent, terminal-based assistant for managing and editing software projects through natural language. It analyzes your project files and allows you to interact with them using natural language prompts, powered by multiple AI models like OpenAI, Google Gemini, and Anthropic Claude.

## Features

- **AI-powered code analysis** and improvement suggestions
- **Automatic or confirmed file changes** with difference highlighting
- **File creation, deletion, and editing** through natural language
- **Command execution** (with confirmation)
- **Support for multiple AI providers**:
  - OpenAI (default model: o4-mini)
  - Google Gemini (default model: gemini-2.5-flash-preview-04-17)
  - Anthropic Claude (default model: claude-3-7-sonnet-latest)
- **Terminal UI** with rich formatting and syntax highlighting
- **Interactive configuration** with profile support
- **Customizable model selection** for each provider

## Installation

### From PyPI (Recommended)

```bash
# Install the basic package
pip install codaicli

# Or install with all AI provider dependencies
pip install "codaicli[all]"
```

### From Source

```bash
# Clone the repository
git clone https://github.com/chafficui/codaicli.git
cd codaicli

# Install in development mode
pip install -e .

# Or install with all dependencies
pip install -e ".[all]"
```

## Usage

1. Navigate to your project directory
   ```bash
   cd your/project
   ```

2. Run Codaicli
   ```bash
   codaicli
   ```

3. On first run, you'll be prompted to configure your API keys and models

4. Ask questions or make requests in natural language:
   - "What does this code do?"
   - "How can I optimize this function?"
   - "Create a config file with these settings"
   - "Initialize a new git repository"

## Commands

- `use openai/gemini/claude` - Switch AI provider
- `help` - Show help information
- `clear` - Clear screen
- `exit` (or `quit`, `q`) - Exit Codaicli

## Configuration

### Interactive Configuration

Run the configuration wizard:
```bash
codaicli configure
```

This will show an interactive menu where you can:
- View current configuration
- Configure API keys
- Select models for each provider
- Set advanced options (tokens, temperature)
- Manage configuration profiles

### Configuration File

API keys and settings are stored in `~/.codaicli/config.json`. You can edit this file directly, but using the interactive configuration is recommended.

### Configuration Profiles

You can create and switch between different configuration profiles:
```bash
codaicli configure --profile development
```

## Ignored Files (.codaiignore)

Codaicli uses a `.codaiignore` file similar to `.gitignore` to specify files and directories to ignore. Create this file in your project root with patterns:

```
# Comments start with #
node_modules/    # Ignore directory
*.log            # Ignore by extension
/dist            # Ignore from repo root
build/           # Trailing slash for directories only
!important.log   # Exclude from ignore (include this file)
```

Pattern rules:
- `*` matches any string except `/`
- `**` matches any directory depth
- `?` matches a single character
- `/` at the start anchors to repo root
- `/` at the end matches directories only
- `!` at the start negates a pattern (include matching files)

If no `.codaiignore` file exists, default patterns are used, including common excludes like `.git/`, `node_modules/`, binary files, etc.

## Troubleshooting

### Common Issues

1. **API Key Errors**
   - Make sure your API keys are correctly configured
   - Check if you have the correct provider package installed
   - Verify your API key permissions and quotas

2. **Model Not Found**
   - The default models are suggestions - you can use any model name
   - Check the provider's documentation for available models
   - Make sure you have access to the model you're trying to use

3. **Installation Issues**
   - Make sure you have Python 3.7 or higher
   - Try installing with `--no-cache-dir` if you have dependency issues
   - Use `pip install -v` for verbose output during installation

4. **Permission Errors**
   - Check if you have write permissions in the project directory
   - Verify the configuration directory permissions (`~/.codaicli`)

### Getting Help

- Check the [GitHub Issues](https://github.com/yourusername/codaicli/issues) for known problems
- Open a new issue if you find a bug
- Join our [Discord community](https://discord.gg/your-server) for support

## Security Note

- **All changes and command executions require user confirmation**
- **No data is modified or transmitted without user interaction**
- **API keys are stored locally and never shared**
- **Use `.codaiignore` to prevent sensitive files from being analyzed**

## Dependencies

- Python 3.7+
- rich - for fancy CLI output
- click - for CLI commands
- openai/google-generativeai/anthropic - for AI provider access
- python-dotenv - for API key management

## License

MIT