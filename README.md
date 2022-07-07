# .github/workflows/push-to-registry.yaml

A ready-to-use Github action workflow for pushing container images to ghcr.io


- builds a multi-architecture image for amd64 and arm64 
- pushes into the container registry corresponding to the repository
- uses `git describe --tags HEAD` to generate a semver tag for the image

# how to use it?

Assuming you have a github repository for a single docker image, type the following commands:

```bash
# ensure that the repository has relevant tags
$ [[ -n $(git tag) ]] || git tag 0.0.0 

# add the workflow
$ mkdir -p .github/workflows/
$ curl -sS -L -o .github/workflows/push-to-registry.yaml \
     https://raw.githubusercontent.com/binxio/push-to-registry-gh-action-workflow/main/push-to-registry.yaml
$ git add .
$ git commit -m 'added push to ghcr.io workflow'
$ git push 
```

To make a beautiful semver release of your image, type:

```bash
$ read NEW_SEMVER
$ git tag $NEW_SEMVER
$ git push --tags
```

Checkout your github action push!


