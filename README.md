# EnvoyProxy

- https://hub.docker.com/r/envoyproxy/envoy-build-windows2019
- https://github.com/envoyproxy/envoy/blob/v1.20.7/ci/README.md

## alternative yaml 

```yaml
name: build envoy proxy on windows

on:
  push

jobs:
  build-job:
    runs-on: windows-2022

    steps:
      - name: Log in to Docker Hub
        uses: docker/login-action@v3
        with:
          username: ${{ vars.DOCKER_USERNAME }}
          password: ${{ secrets.DOCKER_PASSWORD }}
          
      - name: Pull and Run command inside container
        shell: powershell
        run: |
          docker pull envoyproxy/envoy-build-windows2019:8a4d6f993e7b93d466cf26a09466d320c62398e2
          docker run --name envoybuild --rm envoyproxy/envoy-build-windows2019:8a4d6f993e7b93d466cf26a09466d320c62398e2
          
          -Command "Write-Output 'Hello from inside the Windows container!'"
```
