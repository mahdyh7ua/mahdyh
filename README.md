name: Build Info Generator

on:
  push:
    branches: [ main, master ]
  pull_request:
    branches: [ main, master ]

jobs:
  generate-info:
    runs-on: ubuntu-latest

    steps:
      - name: Checkout repo
        uses: actions/checkout@v4

      - name: Generate build info file
        run: |
          echo "Build Date: $(date -u)" > build_info.txt
          echo "Commit SHA: $GITHUB_SHA" >> build_info.txt
          echo "Branch: $GITHUB_REF_NAME" >> build_info.txt
          echo "Actor: $GITHUB_ACTOR" >> build_info.txt

      - name: Commit & push build info
        run: |
          git config user.name "github-actions[bot]"
          git config user.email "41898282+github-actions[bot]@users.noreply.github.com"
          git add build_info.txt
          git commit -m "Update build info [skip ci]" || echo "No changes to commit"
          git push

name: Node CI

on:
  push:
    branches: [ main, master ]
  pull_request:
    branches: [ main, master ]

jobs:
  build:
    runs-on: ubuntu-latest

    steps:
      - name: Checkout repo
        uses: actions/checkout@v4

      - name: Set up Node.js
        uses: actions/setup-node@v4
        with:
          node-version: "20"

      - name: Create source and test files
        run: |
          mkdir -p src tests
          echo 'function greet(name) {
  return `Hello, ${name}!`;
}
module.exports = { greet };' > src/hello.js

          echo "const { greet } = require('../src/hello');
test('greet should return correct message', () => {
  expect(greet('Mahdy')).toBe('Hello, Mahdy!');
});" > tests/hello.test.js

      - name: Install dependencies
        run: |
          npm init -y
          npm install jest --save-dev

      - //name: Run tests
       //run: npx jest


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
    /yadt bashe mishe 
    natrs agar pat ham larzid ghadam aval bardar

          //echo 'from src.hello import greet

def test_greet():
    assert greet("Mahdy") == "Hello, Mahdy!"' > tests/test_hello.py

      name: Install dependencies
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
