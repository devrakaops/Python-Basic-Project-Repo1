# Python + GitHub Actions CI Demo
This is a simple **Python project** to demonstrate how to set up **GitHub Actions** for Continuous Integration (CI).  
The workflow automatically runs tests whenever code is pushed to the `main` branch or a Pull Request is created.

---
## 🎯 Goal
- Create a simple Python program
- Write unit tests using `pytest`
- Run tests automatically using **GitHub Actions**


-------------------------------------------------------
---
## 📂 Project Structure
hello-python/
│
├── hello.py # Main Python file
├── test_hello.py # Unit tests
└── .github/
└── workflows/
└── python-app.yml # GitHub Actions workflow

------------------------------------------------------
# vim hello.py
def add(a, b):
    return a + b

if __name__ == "__main__":
    print("Hello GitHub Actions!")
    print("2 + 3 =", add(2, 3))

---------------------------------------------------
# vim test_hello.py
from hello import add
def test_add():
    assert add(2, 3) == 5
    assert add(-1, 1) == 0

---------------------------------------------------------------
⚙️ GitHub Actions Workflow
.github/workflows/python-app.yml

name: Python CI
on: 
  push:
    branches: 
      - main
  workflow_dispatch:
jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout repository
        uses: actions/checkout@v4

      - name: Set up Python
        uses: actions/setup-python@v5
        with:
          python-version: '3.13'

      - name: Install Dependencies
        run: |
          python -m pip install --upgrade pip
          pip install pytest

      - name: Run the Test
        run: pytest

---------------------------------------------------------------------------------------

How It Works: ???????????/
Push code to main branch OR create a Pull Request.

GitHub Actions workflow will:
- Checkout the repository
- Set up Python 3.13
- Install dependencies (pytest)
- Run tests
- Workflow status (✅ success / ❌ fail) will appear in GitHub Actions tab.
