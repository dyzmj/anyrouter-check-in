```markdown
# anyrouter-check-in Development Patterns

> Auto-generated skill from repository analysis

## Overview

This skill teaches you how to contribute to the `anyrouter-check-in` Python project, which automates check-in processes across platforms, with support for browser automation, authentication, proxy configuration, and CI integration. You'll learn the project's coding conventions, how to implement new features or fixes, and how to follow established workflows for maintainable, testable, and well-documented code.

## Coding Conventions

- **Language:** Python (no framework)
- **File Naming:** Use `camelCase` for file names.
  - Example: `checkin.py`, `utils/browser.py`, `utils/popups.py`
- **Import Style:** Use relative imports within the package.
  - Example:
    ```python
    from .browser import launch_browser
    from .config import get_config
    ```
- **Export Style:** Use named exports (explicitly define what is exported).
  - Example:
    ```python
    # utils/browser.py
    def launch_browser(...):
        ...

    __all__ = ['launch_browser']
    ```
- **Commit Messages:** Follow [Conventional Commits](https://www.conventionalcommits.org/).
  - Prefixes: `fix`, `feat`, `chore`, `refactor`, `perf`, `docs`
  - Example: `feat: add support for OAuth login method`
- **Configuration:** Use `.env.example` to document environment variables.

## Workflows

### Add or Enhance Login Method
**Trigger:** When adding a new authentication method or improving login flows.
**Command:** `/add-login-method`

1. Update `checkin.py` to implement or modify login logic.
2. Modify `utils/browser.py` and/or `utils/popups.py` to handle new UI flows, selectors, or dialogs.
3. Adjust `utils/config.py` if new config options are needed (e.g., toggling login methods, proxy usage).
4. Update `.env.example` to document new config variables.
5. Edit `.github/workflows/checkin.yml` if CI needs to support the new login method (e.g., secrets, env vars).
6. Update `README.md` or documentation for user-facing changes.

**Example:**
```python
# checkin.py
from .utils.browser import launch_browser
from .utils.popups import handle_login_popup

def login_with_email_password(email, password):
    browser = launch_browser()
    handle_login_popup(browser, email, password)
```

---

### CI Workflow Improvement or Debug Artifact
**Trigger:** When making CI more robust, enabling debugging, or adding artifact uploads.
**Command:** `/improve-ci`

1. Edit `.github/workflows/checkin.yml` to change steps, add artifact upload, or tweak environment variables.
2. Update `.gitignore` if new artifact directories are created.
3. Modify `checkin.py` and/or `utils/browser.py` to generate and save debug artifacts (e.g., screenshots) or enable verbose logging.
4. Add or update scripts (e.g., `setup_mihomo_proxy.sh`) if new setup steps are required for CI.
5. Optionally update `.env.example` and `README.md` to document new debug or CI options.

**Example:**
```yaml
# .github/workflows/checkin.yml
- name: Upload screenshots
  uses: actions/upload-artifact@v2
  with:
    name: screenshots
    path: ./artifacts/screenshots/
```

---

### Proxy Support or Enhancement
**Trigger:** When adding or improving proxy support for browser or API connections.
**Command:** `/add-proxy-support`

1. Update `utils/proxy.py` and/or `scripts/setup_mihomo_proxy.sh` to implement or improve proxy logic.
2. Modify `checkin.py` and `utils/browser.py` to use proxy settings as needed.
3. Edit `.env.example` to document new proxy-related environment variables.
4. Update `.github/workflows/checkin.yml` to set up proxy in CI.
5. Update `README.md` to document proxy usage.

**Example:**
```python
# utils/proxy.py
def setup_proxy(proxy_url):
    # Configure browser or requests to use proxy_url
    ...
```

---

### Modularize or Refactor Browser Utilities
**Trigger:** When cleaning up, modularizing, or extending browser-related code.
**Command:** `/refactor-browser-utils`

1. Move or refactor code in `checkin.py` into `utils/browser.py` and/or `utils/popups.py`.
2. Update imports and logic in `checkin.py` to use new utility functions.
3. Optionally update `utils/config.py` if configuration is affected.

**Example:**
```python
# utils/browser.py
def login_flow(browser, credentials):
    # Encapsulate login steps here
    ...

# checkin.py
from .utils.browser import login_flow
```

---

### Documentation Update for New Feature or Config
**Trigger:** When adding a new feature or config option that users need to know about.
**Command:** `/update-docs`

1. Edit `README.md` to describe the new feature or config.
2. Update `.env.example` to show new environment variables.
3. Optionally update `CONTRIBUTING.md` if contribution workflow changes.

**Example:**
```markdown
# README.md
## New Feature: Proxy Support
Set `PROXY_URL` in your `.env` to enable proxy routing.
```

## Testing Patterns

- **Test File Naming:** Use `*.test.*` pattern (e.g., `browser.test.py`).
- **Framework:** Not explicitly specified—use standard Python `unittest` or `pytest` as appropriate.
- **Example:**
  ```python
  # browser.test.py
  import unittest
  from .browser import launch_browser

  class BrowserTestCase(unittest.TestCase):
      def test_launch(self):
          browser = launch_browser()
          self.assertIsNotNone(browser)
  ```

## Commands

| Command              | Purpose                                                |
|----------------------|--------------------------------------------------------|
| /add-login-method    | Add or enhance a login/authentication method           |
| /improve-ci          | Improve CI workflow or add debug artifact support      |
| /add-proxy-support   | Add or enhance proxy support                           |
| /refactor-browser-utils | Refactor or modularize browser automation utilities |
| /update-docs         | Update documentation for new features or config        |
```
