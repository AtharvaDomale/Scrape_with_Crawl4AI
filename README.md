# Scrape_with_Crawl4AI

## 🚀 Installation & Setup (2023 Edition)

### 1. Basic Installation

To install the core Crawl4AI library:

```bash
pip install crawl4ai
```

This installs the core **Crawl4AI** library along with essential dependencies.  
*Note: Advanced features (like transformers or PyTorch) are **not** included yet.*

---

### 2. Initial Setup & Diagnostics

#### 2.1 Run the Setup Command

After installing, run:

```bash
crawl4ai-setup
```

**What does it do?**

- Installs or updates required **Playwright browsers** (Chromium, Firefox, etc.)
- Performs **OS-level checks** (e.g., missing libs on Linux)
- Confirms your environment is **ready to crawl**

---

#### 2.2 Diagnostics (Optional)

You can run diagnostics to confirm everything is functioning properly:

```bash
crawl4ai-doctor
```

**This command attempts to:**

- Check **Python version compatibility**
- Verify **Playwright installation**
- Inspect **environment variables** or library conflicts

> ⚠️ If any issues arise, follow the suggestions (e.g., installing additional system packages), then re-run `crawl4ai-setup`.

---

### 3. Verifying Installation: A Simple Crawl  
(*Skip this step if you've already run `crawl4ai-doctor`*)

Below is a minimal Python script that demonstrates a basic crawl using `BrowserConfig` and `CrawlerRunConfig`:

```python
import asyncio
from crawl4ai import AsyncWebCrawler, BrowserConfig, CrawlerRunConfig

async def main():
    async with AsyncWebCrawler() as crawler:
        result = await crawler.arun(
            url="https://www.example.com",
        )
        print(result.markdown[:300])  # Show the first 300 characters of extracted text

if __name__ == "__main__":
    asyncio.run(main())
```

**Expected Outcome:**

- A headless browser session loads `example.com`
- Crawl4AI returns ~300 characters of markdown

> ❗ If errors occur, re-run `crawl4ai-doctor` or manually ensure **Playwright** is installed correctly.

---

### 4. Common Error and Fix

If you see an error like this:

```
Error: BrowserType.launch: Executable doesn't exist at /home/codespace/.cache/ms-playwright/chromium-1179/chrome-linux/chrome
╔════════════════════════════════════════════════════════════╗
║ Looks like Playwright was just installed or updated.       ║
║ Please run the following command to download new browsers: ║
║                                                            ║
║     playwright install                                     ║
║                                                            ║
║ <3 Playwright Team                                         ║
╚════════════════════════════════════════════════════════════╝
```

This means Playwright's browser binaries are missing. To fix it, run:

```bash
playwright install
```

This will download the necessary browsers so Playwright can launch them properly.

---

### 5. Playwright Dependency Warning on Linux

When downloading browsers, you might see a warning like this:

```
Playwright Host validation warning: 
╔══════════════════════════════════════════════════════╗
║ Host system is missing dependencies to run browsers. ║
║ Please install them with the following command:      ║
║                                                      ║
║     sudo playwright install-deps                     ║
║                                                      ║
║ Alternatively, use apt:                              ║
║     sudo apt-get install libatk1.0-0t64\             ║
║         libatk-bridge2.0-0t64\                       ║
║         libcups2t64\                                 ║
║         libxkbcommon0\                               ║
║         libatspi2.0-0t64\                            ║
║         libxcomposite1\                              ║
║         libxdamage1\                                 ║
║         libxfixes3\                                  ║
║         libxrandr2\                                  ║
║         libgbm1\                                     ║
║         libasound2t64                                ║
║                                                      ║
║ <3 Playwright Team                                   ║
╚══════════════════════════════════════════════════════╝
```

This means your system is missing some libraries required by Playwright browsers.

**How to fix:**

Run the following command to install all necessary dependencies:

```bash
sudo playwright install-deps
```

Alternatively, you can install the listed libraries manually with:

```bash
sudo apt-get install libatk1.0-0 libatk-bridge2.0-0 libcups2 libxkbcommon0 libatspi2.0-0 libxcomposite1 libxdamage1 libxfixes3 libxrandr2 libgbm1 libasound2
```

> ⚠️ Make sure to have the appropriate permissions (sudo) and that you are running this on a compatible Linux distribution.

---
