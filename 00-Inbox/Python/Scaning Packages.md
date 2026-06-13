## Package Safety Check

### Verdict for each package

|Package|Safe?|Notes|
|---|---|---|
|**imutils**|✅ Safe|Widely used OpenCV utility library by Adrian Rosebrock|
|**numpy**|✅ Safe|Industry standard, maintained by NumFy|
|**cv2 (opencv-python)**|✅ Safe|Industry standard computer vision library|
|**google.colab.patches**|✅ Safe|Built into Google Colab, not a separate install|
|**IPython.display**|✅ Safe|Built into IPython/Jupyter, not a separate install|
|**google.colab.output**|✅ Safe|Built into Google Colab, not a separate install|
|**base64**|✅ Safe|Python standard library, no install needed|

**All packages here are safe.** They are all well-known, widely used, and maintained by reputable organizations.

---

## How to Automatically Check Packages Before Installing with UV

### Option 1: Use `pip-audit` before installing

```bash
# Install pip-audit
uv pip install pip-audit

# Check a package before installing
pip-audit --dry-run numpy imutils opencv-python
```

### Option 2: Use `safety` CLI

```bash
# Install safety
uv pip install safety

# Scan your current environment
safety check

# Check a specific package
safety check -r requirements.txt
```

### Option 3: Check PyPI directly (quick manual check)

Before installing any package, verify:

1. **PyPI page exists** → `https://pypi.org/project/<package-name>`
2. **Download count is high** (millions = trusted)
3. **Source code on GitHub** is linked and active
4. **Last updated recently** (abandoned packages = risk)

### Option 4: Use `guarddog` (detects malicious packages)

```bash
# Install guarddog
uv pip install guarddog

# Scan a package before installing
guarddog pypi scan numpy
guarddog pypi scan imutils
```

This specifically looks for **typosquatting**, **suspicious code patterns**, and **known malware**.

---

## My Recommended Workflow

Before running `uv add <package>`, do this:

```bash
# 1. Check for known CVEs
pip-audit <package>

# 2. Scan for malicious patterns
guarddog pypi scan <package>

# 3. Only then install
uv add <package>
```

**Guarddog** is the most powerful for catching malicious code specifically — it was built by Datadog's security team for exactly this purpose.


