name: Build Info Generator


vcnkfdcxnv
njvjkdxfnv 
kvfnmkfldv

miresam be arezom 
mahajerat mikonm 
khanvadm mibarm
      - name: Commit & push build info
        run: |
          git config user.name "github-actions[bot]"
          git config user.email "41898282+github-actions[bot]@users.noreply.github.com"
          git add build_info.txt
          fjkvnfjd
          mitonma
          mitonm
          git commit -m "Update build info [skip ci]" || echo "No changes to commit"
          git push
kam nayari ha miresi bedast miyari
name: Node CI

on:
  push:
  jbjhb
  gfcfgc
  jhbhjbj
  bbjhbj
  fvnfjdkvn
  jcbdhjcvf
  bnvjhfdbv
    branches: [ main, master ]
  pull_request:
    branches: [ main, master ]

jobs:
  build:
    runs-on: ubuntu-latest

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
