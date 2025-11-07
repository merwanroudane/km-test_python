# Quick Reference: Line-by-Line Changes

## Summary
All changes involve wrapping numpy boolean comparisons with `bool()` to ensure Python native boolean types are returned.

---

## File: kmtest/helpers.py

### Line 159
```python
# OLD
return p_value < alpha

# NEW
return bool(p_value < alpha)
```

---

## File: kmtest/km_tests.py

### Line 81 (in km_v1_test function)
```python
# OLD
reject = abs(V1) > stats.norm.ppf(0.975)

# NEW
reject = bool(abs(V1) > stats.norm.ppf(0.975))
```

### Lines 154-156 (in km_u1_test function)
```python
# OLD
reject_dict = {
    '0.10': abs(U1) > critical_values['0.10'],
    '0.05': abs(U1) > critical_values['0.05'],
    '0.01': abs(U1) > critical_values['0.01']
}

# NEW
reject_dict = {
    '0.10': bool(abs(U1) > critical_values['0.10']),
    '0.05': bool(abs(U1) > critical_values['0.05']),
    '0.01': bool(abs(U1) > critical_values['0.01'])
}
```

### Line 233 (in km_v2_test function)
```python
# OLD
reject = abs(V2) > stats.norm.ppf(0.975)

# NEW
reject = bool(abs(V2) > stats.norm.ppf(0.975))
```

### Lines 308-310 (in km_u2_test function)
```python
# OLD
reject_dict = {
    '0.10': abs(U2) > critical_values['0.10'],
    '0.05': abs(U2) > critical_values['0.05'],
    '0.01': abs(U2) > critical_values['0.01']
}

# NEW
reject_dict = {
    '0.10': bool(abs(U2) > critical_values['0.10']),
    '0.05': bool(abs(U2) > critical_values['0.05']),
    '0.01': bool(abs(U2) > critical_values['0.01'])
}
```

---

## File: kmtest/test_suite.py

### Lines 61-68 (in km_test_suite function)
```python
# OLD
# Detect drift if not specified
if has_drift is None:
    has_drift = detect_drift(y, alpha=alpha)
    if verbose:
        drift_msg = "WITH drift detected" if has_drift else "WITHOUT drift detected"
        print(f"\nAutomatic drift detection: {drift_msg}")

# NEW
# Detect drift if not specified
if has_drift is None:
    has_drift = detect_drift(y, alpha=alpha)
    if verbose:
        drift_msg = "WITH drift detected" if has_drift else "WITHOUT drift detected"
        print(f"\nAutomatic drift detection: {drift_msg}")
else:
    # Ensure has_drift is a Python bool (in case user passes numpy bool)
    has_drift = bool(has_drift)
```

---

## Testing Command

```bash
cd /path/to/kmtest_python
python -m pytest tests/ -v
```

Expected: All 16 tests pass (4 previously failing tests now fixed)
