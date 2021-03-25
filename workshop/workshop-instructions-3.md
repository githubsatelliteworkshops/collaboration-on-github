## GitHub Actions to Push Docker Images to GitHub Packages

### GitHub Actions to build Docker Images

```yml
name: Docker Build for NodeJS
on:
  push
  
jobs:
  dockerize:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v2

      - name: Create Docker Image for Development Environment
        run: |
          cd frontend/
          docker build -t node .
```

### GitHub Actions to Push Docker Images

```
name: Docker Build for React
on:
  push
env:
  IMAGE_NAME: react
  
jobs:
  dockerize:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v2

      - name: Create Docker Image for Development Environment
        run: |
          cd backend/
          docker build -t react .
      
      - name: Log into registry
        run: echo "${{ secrets.GH_TOKEN }}" | docker login ghcr.io -u ${{ github.actor }} --password-stdin

      - name: Push image
        run: |
          IMAGE_ID=ghcr.io/${{ github.repository }}/$IMAGE_NAME
          IMAGE_ID=$(echo $IMAGE_ID | tr '[A-Z]' '[a-z]')
          docker tag $IMAGE_NAME $IMAGE_ID
          docker push $IMAGE_ID
```