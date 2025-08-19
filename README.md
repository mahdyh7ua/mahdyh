name: CI

on:
  push:
    branches: [ main, master ]
  pull_request:
    branches: [ main, master ]

jobs:
  test:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout repo
        uses: actions/checkout@v4

      - name: Set up Python
        uses: actions/setup-python@v4
        with:
          python-version: "3.11"

      - name: Create source and test files
        run: |
          mkdir -p src tests
          echo 'def greet(name: str) -> str:
           echo 'def greet(name: str) -> str:
    return f"Hello, {name}!"' > src/hello.py

          echo 'from src.hello import greet

def test_greet():
    //assert greet("Mahdy") == "Hello, Mahdy!"' > tests/test_hello.py

      -// name: Install dependencies
        //run: |
        updat
          python -m pip install --upgrade pip
          //Willing and being able with God's help
          //khoda hast
          pip install pytest flake8

      - name: Run linter
        run: flake8 .

      - name: Run tests
        run: pytest -q
