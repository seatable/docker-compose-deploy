## SeaTable Docker Compose Releases
This repository contains a docker compose project to deploy SeaTable Server and addtional services like the Python Pipeline or Only Office. Releases are be referenced in the [SeaTable Admin Manual](https://admin.seatable.io/). Distribution Method is a release tar download from github.

### Releases

Releases are named after the SeaTable version they're based on. The `latest` tag always points to the most recent release, including pre-releases.)

### Preparing a New Release

1. Checkout a commit from the main branch.
2. Create a lightweight tag on the commit in the format `v*.*.*` (full release) or `pre-v*.*.*` (pre-release) and push the tag to origin.
3. All files in the 'compose/' directory will be uploaded to the release as a tarball (`seatable-compose.tar.gz`), and the release will be tagged with the version number from the git tag.

```bash
git tag v*.*.*
git push origin v*.*.*
```
### Reference Releases

This `latest` url and api call will point to the ***latest full, non-prerelease, non-draft release release.***
These are the methods to get the latest stable, tested SeaTable release.
```bash
curl -s https://api.github.com/repos/seatable/seatable-release/releases/latest | jq -r '.assets[0].browser_download_url'
```
https://github.com/seatable/seatable-release/releases/latest/download/seatable-compose.tar.gz
---
To download a specific release you can use these types of urls (example):\
https://github.com/seatable/seatable-release/releases/download/v4.3.10/seatable-compose.tar.gz
https://github.com/seatable/seatable-release/releases/download/pre-v4.4.4/seatable-compose.tar.gz

#### Development/Test Installation from Main Branch
This method is not recommended for production use as the main branch is for development and may contain untested or broken code.
```bash
mkdir -p /opt/seatable-compose && cd /opt/seatable-compose && \
git clone https://github.com/seatable/seatable-release.git && \
mv seatable-release/compose/* seatable-release/compose/.* -t . && rm -r seatable-release/ && \
cp -n .env-release .env
```
