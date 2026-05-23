# macOS Universal2 Build

This fork keeps the original project history and attribution to the upstream author:

- Upstream repository: https://github.com/AvenCores/open-antigravity-patcher
- Original project name: Open AG Patcher
- License: GPL-3.0, unchanged

This branch adds a reproducible macOS `universal2` build path for Intel and Apple Silicon Macs.

## Build

Use a universal Python framework, such as the Python 3.9 runtime bundled with Xcode, then install the project build requirements:

```bash
python3 -m venv .venv39
.venv39/bin/python -m pip install --upgrade pip
.venv39/bin/python -m pip install -r requirements.txt
```

Build the binary:

```bash
.venv39/bin/pyinstaller --onefile \
  --name="Open_AG_Patcher_macOS" \
  --target-arch universal2 \
  --hidden-import=packaging \
  --hidden-import=packaging.version \
  --hidden-import=packaging.specifiers \
  --hidden-import=packaging.requirements \
  --clean main.py
```

## Release Asset

Attach the compiled `dist/Open_AG_Patcher_macOS` or zipped `Open_AG_Patcher_macOS-universal2.zip` to a GitHub Release instead of committing the binary into git history.

Verified local build:

```text
Binary SHA256: 3a0e7a53874c17c4e1bcd9e895c9c8f379a9e809308e9ecd4f65ff1abe8000a0
Zip SHA256:    03385b3319af9523da306545dbdc9a893fe79112fa82ee08b9b75323a378e246
Architecture:  x86_64 + arm64
```

Recommended release title:

```text
Open AG Patcher 1.1.5 macOS universal2 build
```

Recommended release note:

```text
Unofficial macOS universal2 build of Open AG Patcher 1.1.5.

Original project and author attribution are preserved through the fork history:
https://github.com/AvenCores/open-antigravity-patcher

This release only adds a reproducible macOS universal2 build path and a macOS binary release asset.
License remains GPL-3.0.
```
