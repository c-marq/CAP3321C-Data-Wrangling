# Getting Started Guide

Welcome to CAP3321C Data Wrangling! This guide will help you set up everything you need for the course.

---

## ✅ What You Need

- A Google account (for Google Colab)
- A modern web browser (Chrome recommended)
- Access to Canvas (for submissions and grades)

That's it. No software installation required.

---

## 🔧 Setting Up Google Colab

### Step 1: Access Google Colab

1. Go to [colab.research.google.com](https://colab.research.google.com)
2. Sign in with your Google account
3. You should see the Colab welcome screen

### Step 2: Open a Notebook from GitHub

When you click on a `.ipynb` file in this repository, you'll see an "Open in Colab" badge at the top. Click it to open the notebook directly in Colab.

**Alternative method:**
1. In Colab, click **File → Open notebook**
2. Select the **GitHub** tab
3. Enter this repository URL: `[YOUR-REPO-URL-HERE]`
4. Select the notebook you want to open

### Step 3: Save Your Work

Colab notebooks don't auto-save to your computer. To keep your work:

1. **Save to Google Drive:** File → Save a copy in Drive
2. **Download:** File → Download → Download .ipynb

**Always save a copy before making changes to course notebooks!**

---

## 🧪 Test Your Setup

Let's make sure everything works. Open a new Colab notebook and run this code:

```python
# Test 1: Python is working
print("Hello, Data Wrangling!")

# Test 2: Pandas is available
import pandas as pd
print(f"Pandas version: {pd.__version__}")

# Test 3: Create a simple DataFrame
data = {'Name': ['Alice', 'Bob', 'Carlos'], 
        'Score': [85, 92, 78]}
df = pd.DataFrame(data)
print(df)
```

If you see output without errors, you're ready to go!

---

## 📂 Working with Course Notebooks

### Opening Notebooks

1. Navigate to the appropriate folder in this repository (e.g., `demos/chapter-02/`)
2. Click on the `.ipynb` file
3. Click the "Open in Colab" badge, or copy the URL and open in Colab via File → Open notebook → GitHub

### The Colab Interface

| Area | Purpose |
|------|---------|
| **Menu bar** | File operations, runtime controls, tools |
| **Toolbar** | Quick actions (+ Code, + Text, Run) |
| **Cells** | Where you write and run code or text |
| **Output** | Results appear below each code cell |

### Running Cells

- **Run one cell:** Click the play button (▶) or press `Shift + Enter`
- **Run all cells:** Runtime → Run all
- **Stop execution:** Runtime → Interrupt execution

### Cell Types

- **Code cells:** Python code that executes
- **Text cells:** Markdown-formatted explanations (double-click to edit)

---

## ⌨️ Keyboard Shortcuts

| Action | Shortcut |
|--------|----------|
| Run cell and move to next | `Shift + Enter` |
| Run cell and stay | `Ctrl + Enter` |
| Add code cell below | `Ctrl + M` then `B` |
| Add text cell below | `Ctrl + M` then `M` (for Markdown) |
| Delete cell | `Ctrl + M` then `D` |
| Undo | `Ctrl + Z` |

---

## 🔌 Connecting to a Runtime

When you first run code, Colab connects to a "runtime" — a virtual computer that executes your Python code.

- **Green checkmark** = Connected and ready
- **Connecting...** = Setting up (wait a few seconds)
- **Reconnect** = Session expired; click to reconnect

**Note:** Free Colab sessions disconnect after ~90 minutes of inactivity. Your code is saved, but you'll need to re-run cells from the beginning.

---

## 📤 Submitting Assignments

All assignments are submitted through **Canvas**, not GitHub.

### For Notebooks (.ipynb files):

1. Complete the assignment in Colab
2. Run all cells to show your output: Runtime → Run all
3. Download: File → Download → Download .ipynb
4. Upload the `.ipynb` file to the Canvas assignment

### Submission Checklist:

- [ ] All cells have been run (output is visible)
- [ ] Your name is in the first cell
- [ ] File is saved as `.ipynb` format
- [ ] Uploaded to correct Canvas assignment before deadline

---

## ❓ Troubleshooting

### "ModuleNotFoundError: No module named 'pandas'"

Pandas is pre-installed in Colab, so this shouldn't happen. Try:
1. Runtime → Restart runtime
2. Run your import cell again

### "Your session crashed"

This usually means you ran out of memory. Try:
1. Runtime → Restart runtime
2. Don't load excessively large datasets
3. Clear outputs: Edit → Clear all outputs

### Notebook won't open from GitHub

1. Make sure you're signed into Google
2. Try refreshing the GitHub page
3. Copy the notebook URL and paste it in Colab's GitHub tab

### Code runs forever (spinning circle)

1. Click Runtime → Interrupt execution
2. Check for infinite loops in your code
3. If stuck, Runtime → Restart runtime

---

## 🆘 Still Stuck?

1. **Check Canvas Discussions** — Someone may have asked the same question
2. **Post your question** — Include error messages and what you tried
3. **Come to office hours** — See Canvas for schedule

---

## ✨ You're Ready!

Once you've completed the setup test above, you're ready for class. See you there!

---

[← Back to Main README](README.md)
