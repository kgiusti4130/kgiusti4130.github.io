---
hide:
  - navigation
  - toc
---

# BGP Builder

## Prerequistes

- Docker Desktop
- Vscode

## Steps

1. Clone repository
2. Once prompted reopen in container
3. Edit variables in **bgp_builder.yml** playbook.
4. Run the playbook.
5. Output will be written to **bgp_output.txt**

### Running BGP building playbook

```text
root@docker-desktop:/workspace# cd bgp-builder/
root@docker-desktop:/workspace# make bgp
```

## Folder descriptions/info

### .devcontainer

**requirements.txt** - python packages to install when container is built

**requirements.yml** - Ansible Collections to install when container is built

**Dockerfile** - Info to build the container

**devcontainer.json** - Points to Docker Compose file and tells when extensions to install along with other required packages

### .vscode

**settings.json** - Color code your VScode window to avoid mixing them up with other projects.

## Pre-commit

This is used to ensure code quality

```text
root@docker-desktop:/workspace# pre-commit install
```

Once installed pre-commit to automatically run when you push to your GIT repository.

You can also manually run it:

```text
root@docker-desktop:/workspace/bgp-builder# pre-commit run --all
trim trailing whitespace.................................................Passed
fix end of files.........................................................Passed
check yaml...............................................................Passed
Check for Linting errors on MarkDown files...............................Passed
```
