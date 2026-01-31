# Actuarial Quiz Questions - Development Setup

## Python Notebook Stack

This project uses Jupyter notebooks for actuarial calculations and visualizations.

### Required Packages
- `jupyter` - Notebook environment
- `numpy` - Numerical computations
- `scipy` - Statistical functions and integration
- `matplotlib` - Plotting and visualization

## Virtual Environment

All packages should be installed in the virtual environment `.venv`.

### Setup

```bash
python -m venv .venv
source .venv/bin/activate  # Linux/macOS
pip install jupyter numpy scipy matplotlib
```

### Automatic Activation on Folder Entry

Add the following to your shell configuration to auto-activate the venv when entering this folder:

**For bash (~/.bashrc):**
```bash
cd() {
    builtin cd "$@"
    if [[ -f .venv/bin/activate ]]; then
        source .venv/bin/activate
    fi
}
```

**For zsh (~/.zshrc):**
```zsh
cd() {
    builtin cd "$@"
    if [[ -f .venv/bin/activate ]]; then
        source .venv/bin/activate
    fi
}
```

**Alternative - using direnv:**
1. Install direnv: `sudo apt install direnv` (or equivalent)
2. Add to shell config: `eval "$(direnv hook bash)"` or `eval "$(direnv hook zsh)"`
3. Create `.envrc` file in project root with: `source .venv/bin/activate`
4. Run `direnv allow` in the project directory
