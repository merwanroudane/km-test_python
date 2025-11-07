# 📋 kmtest Python Package - Quick Reference Card

## Dr. Merwan Roudane | merwanroudane920@gmail.com

---

## ⚡ 30-Second Overview

✅ **R package successfully converted to Python**  
✅ **All 4 tests implemented: V1, V2, U1, U2**  
✅ **Production-ready, tested, documented**  
✅ **Ready to publish to PyPI**

---

## 🚀 Quick Start (Copy & Paste)

### Test It Works (5 minutes):
```bash
cd kmtest_python

python3 -c "import sys; sys.path.insert(0, '.'); \
from kmtest import km_test_suite; \
import numpy as np; \
np.random.seed(123); \
y = np.cumsum(np.random.normal(0.5, 1, 200)) + 100; \
result = km_test_suite(y, verbose=False); \
print(f'✅ Success! Recommendation: {result.recommendation}')"
```

### Run Examples:
```bash
export PYTHONPATH="${PWD}:${PYTHONPATH}"
python3 examples/basic_examples.py
```

---

## 📦 Publish to PyPI (30 minutes)

### 1. Install Tools:
```bash
pip install build twine
```

### 2. Build Package:
```bash
cd kmtest_python
python -m build
```

### 3. Upload to PyPI:
```bash
twine upload dist/*
# (Enter PyPI credentials)
```

### 4. Done!
```bash
pip install kmtest  # Works worldwide!
```

**Detailed steps:** See `PUBLISHING_GUIDE.md`

---

## 💻 Usage Examples

### Basic Usage:
```python
from kmtest import km_test_suite
import numpy as np

y = np.array([100.2, 102.5, 101.8, ...])  # Your data
result = km_test_suite(y)
print(result.recommendation)  # "LEVELS" or "LOGARITHMS"
```

### Individual Tests:
```python
from kmtest import km_v1_test, km_v2_test

v1 = km_v1_test(y)  # Linear vs Log (with drift)
v2 = km_v2_test(y)  # Log vs Linear (with drift)

print(f"V1: {v1.statistic:.4f}, p={v1.p_value:.4f}")
```

---

## 📚 Key Documents

| Document | Purpose | Time |
|----------|---------|------|
| `INDEX.md` | File navigation | 2 min |
| `PACKAGE_SUMMARY.md` | Complete overview | 10 min |
| `GETTING_STARTED.md` | Quick start guide | 5 min |
| `PUBLISHING_GUIDE.md` | PyPI publishing | 30 min |
| `README.md` | Full documentation | 15 min |

**👉 Start with `INDEX.md` or `PACKAGE_SUMMARY.md`**

---

## 🎯 What's Included

✅ 4 test functions (V1, V2, U1, U2)  
✅ Test suite with auto drift detection  
✅ Helper functions (lag selection, etc.)  
✅ Result classes with rich output  
✅ 25+ unit tests  
✅ 5 working examples  
✅ Complete documentation  
✅ PyPI-ready packaging  
✅ GPL v3 license

---

## 📁 Package Structure

```
kmtest_python/
├── 📄 Documentation (read these!)
│   ├── INDEX.md                ⭐ Start here
│   ├── PACKAGE_SUMMARY.md      ⭐ Overview
│   ├── GETTING_STARTED.md      ⭐ Quick start
│   ├── PUBLISHING_GUIDE.md     ⭐ Publishing
│   └── README.md               ⭐ Full docs
│
├── 📦 kmtest/                  Main package code
│   ├── km_tests.py            4 test functions
│   ├── helpers.py             Utilities
│   ├── results.py             Result classes
│   └── test_suite.py          Test suite
│
├── 🧪 tests/                   Unit tests
└── 💡 examples/                Usage examples
```

---

## 🔬 Test Functions

| Function | Null Hypothesis | Alternative | Distribution |
|----------|----------------|-------------|--------------|
| `km_v1_test` | Linear (drift) | Logarithmic | N(0,1) |
| `km_v2_test` | Log (drift) | Linear | N(0,1) |
| `km_u1_test` | Linear (no drift) | Logarithmic | Nonstandard |
| `km_u2_test` | Log (no drift) | Linear | Nonstandard |

**Test Suite:** `km_test_suite()` - Runs appropriate tests automatically

---

## ✅ Quality Checklist

- ✅ Matches R package exactly
- ✅ All formulas from paper implemented
- ✅ Critical values from Table 1 included
- ✅ Comprehensive tests (all pass)
- ✅ Complete documentation
- ✅ Type hints & docstrings
- ✅ Input validation
- ✅ PyPI-ready packaging

---

## 🎓 Learning Path

### Beginner (15 min):
1. Read `PACKAGE_SUMMARY.md`
2. Run examples
3. Test basic usage

### Intermediate (1 hour):
1. Read `README.md`
2. Understand test logic
3. Review implementation

### Advanced (2 hours):
1. Study `km_tests.py`
2. Review test suite
3. Prepare for publishing

---

## 📞 Need Help?

- **Quick Questions:** See `GETTING_STARTED.md`
- **Publishing Help:** See `PUBLISHING_GUIDE.md`
- **API Reference:** See `README.md`
- **Code Details:** Read docstrings in `kmtest/`

---

## 🎉 Next Steps

1. ✅ Read `PACKAGE_SUMMARY.md` (10 min)
2. ✅ Test locally (5 min)
3. 📦 Publish to PyPI (30 min)
4. 🎊 Announce release!

---

## 📊 By the Numbers

- **8** Python source files
- **~1,200** lines of code
- **25+** unit tests
- **5** usage examples
- **4** core test functions
- **2** dependencies (numpy, scipy)
- **100%** functional parity with R

---

## 🌟 Key Features

✨ **Easy to Use:** Simple API, clear outputs  
✨ **Well-Tested:** Comprehensive test suite  
✨ **Documented:** Extensive docs & examples  
✨ **Professional:** Proper packaging & licensing  
✨ **Faithful:** Exact match to R version  

---

## 📖 Citation

```bibtex
@software{roudane2024kmtest,
  author = {Roudane, Merwan},
  title = {kmtest: Kobayashi-McAleer Tests for Python},
  year = {2024},
  url = {https://github.com/merwanroudane/kmtest-python}
}

@article{kobayashi1999tests,
  title={Tests of linear and logarithmic transformations 
         for integrated processes},
  author={Kobayashi, Masahito and McAleer, Michael},
  journal={Journal of the American Statistical Association},
  volume={94}, number={447}, pages={860--868},
  year={1999}, doi={10.1080/01621459.1999.10474191}
}
```

---

## 🚀 One-Line Install (After Publishing)

```bash
pip install kmtest
```

---

**Your Python package is ready! Start with `PACKAGE_SUMMARY.md`** 📚

**Questions?** Email: merwanroudane920@gmail.com

---

*Version 1.0.0 | November 2024*
