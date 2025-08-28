
```markdown
# 🐍 Python + GitHub Actions CI Demo

A simple **Python project** to demonstrate how to use **GitHub Actions** for Continuous Integration (CI).  
The workflow automatically runs tests whenever code is pushed to the `main` branch or a Pull Request is created.  

---

## 🎯 Project Goals
- ✅ Learn how to write a simple Python program
- ✅ Add unit tests using `pytest`
- ✅ Automate test execution with GitHub Actions

---

## 📂 Project Structure
```

<img width="438" height="162" alt="image" src="https://github.com/user-attachments/assets/252a0e77-9be9-4611-91b9-92efb52ce9f6" />


````

---

def add(a, b):
    return a + b

if __name__ == "__main__":
    print("Hello GitHub Actions!")
    print("2 + 3 =", add(2, 3))
````

### `test_hello.py`

```python
from hello import add

def test_add():
    assert add(2, 3) == 5
    assert add(-1, 1) == 0
```

---

## ⚙️ GitHub Actions Workflow

### `.github/workflows/python-app.yml`

```yaml
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
```

---

## 🚀 How It Works

1. Push code to the `main` branch OR create a Pull Request.
2. GitHub Actions workflow will:

   * Checkout the repository
   * Set up Python 3.13
   * Install dependencies (`pytest`)
   * Run tests automatically
3. Workflow status will appear in:

   * **Actions tab** (detailed logs)
   * **Pull Requests tab** (✅ success / ❌ fail badge)

---

## 📸 Example Workflow Run

* ✅ Passing build will show a green checkmark
* ❌ Failing build will show a red cross

![GitHub Actions Example](https://user-images.githubusercontent.com/000000/0000000-example.png)

---

## 🙌 Contribution

1. Fork this repository
2. Create your feature branch (`git checkout -b feature/awesome-feature`)
3. Commit your changes (`git commit -m 'Add awesome feature'`)
4. Push to the branch (`git push origin feature/awesome-feature`)
5. Open a Pull Request

```

