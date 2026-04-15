# incus-spawn-templates

Template images and tool definitions for [incus-spawn](https://github.com/Sanne/incus-spawn).

## Templates

| Template | Parent | Description |
|----------|--------|-------------|
| `tpl-quarkus` | `tpl-java` | Podman, Gradle, Quarkus source from GitHub |
| `tpl-hibernate-reactive` | `tpl-java` | Podman, Gradle, Hibernate Reactive source from GitHub |

Both templates inherit the full `tpl-java` chain (`tpl-minimal` → `tpl-dev` → `tpl-java`), which provides JDK 25, Maven, Claude Code, GitHub CLI, and tmux.

## Tools

| Tool | Description |
|------|-------------|
| `podman` | Podman configured for Testcontainers (DOCKER_HOST, Ryuk disabled) |
| `gradle` | Gradle build tool (latest release, installed to /opt) |
| `quarkus-src` | Clones `quarkusio/quarkus` into ~/quarkus |
| `hibernate-reactive-src` | Clones `hibernate/hibernate-reactive` into ~/hibernate-reactive |

## Setup

Add this directory as a search path in `~/.config/incus-spawn/config.yaml`:

```yaml
searchPaths:
  - /path/to/incus-spawn-templates
```

Then build a template:

```shell
isx build tpl-quarkus
```
