---
name: microsoft-device-login-automation
description: Use when seeing Microsoft device login prompts with token_expired errors - automatically opens devicelogin URL, extracts code, and optionally automates form submission
---

# Microsoft Device Login Automation

## Overview

Automate the Microsoft device login flow when tokens expire. Detects the prompt, extracts the code, opens the URL, and optionally automates the full authentication flow.

## When to Use

- See "token_expired" error from Microsoft services
- Terminal shows "navigate to https://microsoft.com/devicelogin"
- Prompted to "enter code: XXXXXXXX"
- Any LinkedIn internal tool requiring LNKDPROD authentication

## The Problem

```
Common error pattern:
suberror":"token_expired"}. Kicking off a full authorization flow and
deleting old credentials.
To Authenticate, navigate in a browser to the following URL:
https://microsoft.com/devicelogin
and enter code: FMQ6V7RV3
[IMPORTANT] Please use your LNKDPROD account to login
```

**Manual process:**
1. Copy URL
2. Open browser
3. Navigate to URL
4. Type code
5. Click Next
6. Authenticate

**Time wasted:** 30-60 seconds, multiple times per day

## Automation Levels

### Level 1: Semi-Automated (Always Available) ✅

Claude Code automatically:
1. Detects the device login prompt
2. Extracts the code
3. Opens the URL in browser
4. Copies code to clipboard

**You manually:**
- Paste code (Cmd+V)
- Click Next
- Authenticate

**Time saved:** ~20 seconds

### Level 2: Fully Automated (Requires Setup) ⭐

Script automatically:
1. Opens URL
2. Types code
3. Clicks Next
4. Waits for authentication

**Time saved:** ~50 seconds

## Level 1: Semi-Automated (Claude Code)

### Detection Pattern

When terminal output contains:
```
navigate.*https://microsoft.com/devicelogin
enter code.*([A-Z0-9]{8,})
```

### Automatic Actions

```bash
# 1. Extract code
code=$(echo "$output" | grep -oE '[A-Z0-9]{8,}' | head -1)

# 2. Open URL
open "https://microsoft.com/devicelogin"

# 3. Copy code to clipboard
echo "$code" | pbcopy

# 4. Notify user
echo "✅ Opened devicelogin, code '$code' copied to clipboard"
echo "👉 Paste with Cmd+V and click Next"
```

## Level 2: Full Automation Setup

### Option A: AppleScript (macOS) ⚡ Fastest

Create `~/.claude/scripts/ms-device-login.sh`:

```bash
#!/bin/bash
set -e

CODE="$1"
URL="https://microsoft.com/devicelogin"

if [ -z "$CODE" ]; then
    echo "Usage: $0 <device-code>"
    exit 1
fi

# Open URL in default browser
open "$URL"

# Wait for page to load
sleep 2

# Use AppleScript to type code and submit
osascript <<EOF
tell application "System Events"
    -- Wait for browser to be frontmost
    delay 1

    -- Type the code
    keystroke "$CODE"
    delay 0.5

    -- Press Tab to move to Next button (or Enter if form auto-submits)
    keystroke tab
    delay 0.3

    -- Press Enter/Return to click Next
    keystroke return
end tell
EOF

echo "✅ Code entered and submitted automatically"
echo "👉 Complete authentication in browser"
```

Make executable:
```bash
chmod +x ~/.claude/scripts/ms-device-login.sh
```

### Option B: Playwright (Cross-Platform) 🌐

Create `~/.claude/scripts/ms-device-login.js`:

```javascript
const { chromium } = require('playwright');

async function autoLogin(code) {
    const browser = await chromium.launch({ headless: false });
    const context = await browser.newContext();
    const page = await context.newPage();

    // Navigate to device login
    await page.goto('https://microsoft.com/devicelogin');

    // Wait for code input field
    await page.waitForSelector('input[name="otc"], input[type="text"]', { timeout: 5000 });

    // Type code
    await page.fill('input[name="otc"], input[type="text"]', code);

    // Click Next button
    await page.click('button[type="submit"], input[type="submit"]');

    console.log('✅ Code entered and submitted');
    console.log('👉 Complete authentication in browser');

    // Keep browser open for authentication
    // User will close after authenticating
}

const code = process.argv[2];
if (!code) {
    console.error('Usage: node ms-device-login.js <code>');
    process.exit(1);
}

autoLogin(code);
```

Install dependencies:
```bash
npm install -g playwright
playwright install chromium
```

### Option C: Browser Extension

For maximum convenience, create a browser extension that:
1. Listens for clipboard changes
2. Detects device codes (8+ alphanumeric)
3. Auto-fills on microsoft.com/devicelogin

## Usage Workflow

### When Error Appears

**Claude Code automatically:**
```bash
# Detects pattern in terminal output
# Executes:
open "https://microsoft.com/devicelogin"
echo "FMQ6V7RV3" | pbcopy
```

**You see:**
```
✅ Opened devicelogin, code 'FMQ6V7RV3' copied to clipboard
👉 Paste with Cmd+V and click Next
```

### With Full Automation

**Claude Code executes:**
```bash
~/.claude/scripts/ms-device-login.sh FMQ6V7RV3
```

**Result:**
- Browser opens
- Code typed
- Form submitted
- You just authenticate

## Implementation in Claude Code

When Claude Code sees the device login prompt:

```python
import re
import subprocess

def handle_device_login(terminal_output):
    # Detect pattern
    if 'microsoft.com/devicelogin' in terminal_output:
        # Extract code
        match = re.search(r'enter code[:\s]+([A-Z0-9]{8,})', terminal_output, re.IGNORECASE)
        if match:
            code = match.group(1)

            # Open URL
            subprocess.run(['open', 'https://microsoft.com/devicelogin'])

            # Copy code to clipboard
            subprocess.run(['pbcopy'], input=code.encode())

            print(f"✅ Opened devicelogin, code '{code}' copied to clipboard")
            print("👉 Paste with Cmd+V and click Next")

            # Optional: Full automation if script exists
            script_path = os.path.expanduser('~/.claude/scripts/ms-device-login.sh')
            if os.path.exists(script_path):
                response = input("Run full automation? (y/n): ")
                if response.lower() == 'y':
                    subprocess.run([script_path, code])
```

## Quick Setup Guide

### Minimal Setup (30 seconds)

Nothing to do! Claude Code handles it automatically.

### Full Automation Setup (5 minutes)

```bash
# 1. Create scripts directory
mkdir -p ~/.claude/scripts

# 2. Create automation script (choose AppleScript or Playwright)

# For AppleScript (macOS):
cat > ~/.claude/scripts/ms-device-login.sh << 'EOF'
#!/bin/bash
CODE="$1"
open "https://microsoft.com/devicelogin"
sleep 2
osascript -e "tell application \"System Events\" to keystroke \"$CODE\""
osascript -e "tell application \"System Events\" to keystroke return"
EOF

chmod +x ~/.claude/scripts/ms-device-login.sh

# 3. Test it
~/.claude/scripts/ms-device-login.sh TEST1234
```

## Troubleshooting

### Browser Doesn't Auto-Fill

**Problem:** AppleScript types but field is empty

**Solutions:**
1. Increase `delay` in AppleScript (slow page load)
2. Click into the input field manually first time
3. Try Playwright instead (more reliable)

### Clipboard Not Working

**Problem:** pbcopy fails

**Solution:**
```bash
# Alternative clipboard command
echo "$code" | xclip -selection clipboard  # Linux
echo "$code" | clip  # Windows (WSL)
```

### Code Extraction Fails

**Problem:** Regex doesn't match code format

**Update pattern:**
```bash
# More flexible pattern
grep -oE '[A-Z0-9]{6,12}' | tail -1
```

## Security Considerations

**Safe:**
- Opening URLs
- Copying to clipboard
- Typing into browser forms

**No concerns:**
- No credentials stored
- No keylogging
- No data exfiltration
- Just automation of manual process

## Frequency & Impact

**How often:**
- Multiple times per day for LinkedIn engineers
- Tokens expire frequently
- Each instance wastes 30-60 seconds

**Annual impact:**
```
Assuming:
- 3 logins per day
- 30 seconds each
- 250 working days/year

Manual: 3 × 30 × 250 = 22,500 seconds = 6.25 hours/year
Automated: 3 × 5 × 250 = 3,750 seconds = 1 hour/year

Time saved: 5.25 hours per engineer per year
```

**For a team of 100 engineers:**
- 525 hours saved per year
- ~$50,000 in productivity (at $100/hr)

## Remember

**Level 1 (Auto):** Claude Code does this automatically. No setup needed.

**Level 2 (Full):** 5 minutes setup, saves hours over time.

**The best automation is the one you don't have to think about.**

Set it up once, save time forever.
