## GitHub Actions for CI/CD

### Setting up CI for React.JS Build

```yml
name: NodeJS Build CI
on:
  push:
jobs:
  build:
    runs-on: ubuntu-latest
    strategy:
      matrix:
        node-version: [14.x]
    steps:
    - uses: actions/checkout@v2
    - name: Use Node.js ${{ matrix.node-version }}
      uses: actions/setup-node@v1
      with:
        node-version: ${{ matrix.node-version }}
    - run: |
        cd frontend/
        npm ci
        npm test
```

### Setting up CI for Apache Maven Build

```yml
name: Java CI with Maven
on:
  push:
jobs:
  build:
    runs-on: ubuntu-latest
    steps:
    - uses: actions/checkout@v2
    - name: Set up JDK 1.8
      uses: actions/setup-java@v1
      with:
        java-version: 1.8
    - name: Build with Maven
      run: |
        cd backend/
        mvn clean install
```

### Next Step

- [Step 3: Writing Dockerfiles for setting up GitHub Packages](workshop-instructions-2.md)