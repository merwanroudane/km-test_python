# Publishing kmtest to PyPI - Complete Guide

## 📦 Package Structure Overview

Your Python package is now ready for publishing! Here's what we've created:

```
kmtest_python/
├── kmtest/                      # Main package
│   ├── __init__.py             # Package initialization
│   ├── km_tests.py             # Main test functions (V1, V2, U1, U2)
│   ├── helpers.py              # Helper functions
│   ├── results.py              # Result classes
│   └── test_suite.py           # Test suite function
├── tests/                       # Unit tests
│   └── test_kmtest.py          # Comprehensive test suite
├── examples/                    # Usage examples
│   └── basic_examples.py       # Basic examples
├── docs/                        # Documentation (empty for now)
├── setup.py                     # Setup script
├── pyproject.toml              # Modern Python packaging config
├── requirements.txt            # Dependencies
├── MANIFEST.in                 # Files to include in distribution
├── LICENSE                     # GPL v3 License
└── README.md                   # Package documentation
```

## 🚀 Step-by-Step Publishing Instructions

### Step 1: Test Your Package Locally

```bash
cd kmtest_python

# Install in development mode
pip install -e .

# Run tests
pytest tests/ -v

# Test the examples
python examples/basic_examples.py
```

### Step 2: Set Up PyPI Accounts

1. **Create a PyPI account** (if you don't have one):
   - Go to https://pypi.org/account/register/
   - Verify your email

2. **Create a TestPyPI account** (for testing):
   - Go to https://test.pypi.org/account/register/
   - Verify your email

3. **Set up API tokens** (recommended over passwords):
   - PyPI: https://pypi.org/manage/account/token/
   - TestPyPI: https://test.pypi.org/manage/account/token/

### Step 3: Install Publishing Tools

```bash
pip install --upgrade pip setuptools wheel twine build
```

### Step 4: Build the Distribution

```bash
cd kmtest_python

# Clean old builds
rm -rf build/ dist/ *.egg-info

# Build the package
python -m build

# This creates:
# dist/kmtest-1.0.0-py3-none-any.whl
# dist/kmtest-1.0.0.tar.gz
```

### Step 5: Test on TestPyPI (Recommended)

```bash
# Upload to TestPyPI
twine upload --repository testpypi dist/*

# Enter your TestPyPI credentials or API token when prompted

# Test installation from TestPyPI
pip install --index-url https://test.pypi.org/simple/ --no-deps kmtest

# Test it works
python -c "from kmtest import km_test_suite; print('Success!')"
```

### Step 6: Upload to PyPI (Production)

```bash
# Upload to PyPI
twine upload dist/*

# Enter your PyPI credentials or API token when prompted
```

### Step 7: Verify Installation

```bash
# Install from PyPI
pip install kmtest

# Test it
python -c "from kmtest import km_test_suite; print('Success!')"
```

## 🔐 Using API Tokens (Recommended)

Create a `~/.pypirc` file:

```ini
[distutils]
index-servers =
    pypi
    testpypi

[pypi]
username = __token__
password = pypi-your-api-token-here

[testpypi]
username = __token__
password = pypi-your-test-api-token-here
```

Then uploading is simpler:
```bash
twine upload --repository testpypi dist/*
twine upload dist/*  # for PyPI
```

## 📋 Pre-Publishing Checklist

Before publishing, make sure:

- ✅ All tests pass: `pytest tests/ -v`
- ✅ Package installs locally: `pip install -e .`
- ✅ Examples run successfully
- ✅ README.md is complete and accurate
- ✅ Version number is correct in setup.py and pyproject.toml
- ✅ LICENSE file is present
- ✅ Author information is correct
- ✅ GitHub repository is created (optional but recommended)

## 🔄 Updating Your Package

When you need to release a new version:

1. **Update version number** in:
   - `setup.py`
   - `pyproject.toml`
   - `kmtest/__init__.py`

2. **Update changelog** (create CHANGELOG.md if needed)

3. **Rebuild and upload**:
```bash
rm -rf dist/ build/ *.egg-info
python -m build
twine upload dist/*
```

## 🐙 GitHub Integration (Optional but Recommended)

1. **Create GitHub repository**:
```bash
git init
git add .
git commit -m "Initial commit: kmtest package"
git branch -M main
git remote add origin https://github.com/merwanroudane/kmtest-python.git
git push -u origin main
```

2. **Add badges to README**:
   - PyPI version: `[![PyPI](https://img.shields.io/pypi/v/kmtest.svg)](https://pypi.org/project/kmtest/)`
   - License: `[![License](https://img.shields.io/badge/License-GPLv3-blue.svg)](https://www.gnu.org/licenses/gpl-3.0)`

3. **Set up GitHub Actions** for automated testing (optional)

## 📚 Documentation

Consider adding:

1. **Sphinx documentation** for comprehensive docs
2. **Jupyter notebooks** with examples
3. **ReadTheDocs** integration

## 🎯 Post-Publishing Tasks

After publishing:

1. **Announce** on relevant platforms:
   - Twitter/X
   - LinkedIn
   - Reddit (r/Python, r/econometrics)
   - Your personal website/blog

2. **Update R package** to mention Python version

3. **Create tutorial blog post**

4. **Add to package ecosystems**:
   - awesome-python lists
   - Relevant curated lists

## 🔧 Troubleshooting

### Common Issues:

**"Package already exists"**
- Version number already used. Increment version and rebuild.

**"Invalid distribution file"**
- Clean and rebuild: `rm -rf dist/ build/ *.egg-info && python -m build`

**Import errors after installation**
- Check package structure
- Verify `__init__.py` imports

**Tests fail**
- Ensure all dependencies are installed
- Check Python version compatibility

## 📞 Support

If you encounter issues:
1. Check PyPI packaging documentation: https://packaging.python.org/
2. Ask on Python Packaging Discourse: https://discuss.python.org/c/packaging/
3. Open an issue on GitHub

## ✅ Quick Command Reference

```bash
# Complete publishing workflow:

# 1. Test locally
pip install -e .
pytest tests/ -v

# 2. Build
python -m build

# 3. Test on TestPyPI
twine upload --repository testpypi dist/*
pip install --index-url https://test.pypi.org/simple/ kmtest

# 4. Upload to PyPI
twine upload dist/*

# 5. Verify
pip install kmtest
python -c "from kmtest import km_test_suite; print('Success!')"
```

## 🎉 Congratulations!

Your package is now published on PyPI and can be installed by anyone using:

```bash
pip install kmtest
```

**Author:** Dr. Merwan Roudane  
**Email:** merwanroudane920@gmail.com  
**GitHub:** https://github.com/merwanroudane

---

Good luck with your package! 🚀
