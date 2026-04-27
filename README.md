# incus-spawn-templates

Community template images and tool definitions for [incus-spawn](https://github.com/Sanne/incus-spawn).

These extend the built-in image chain (`tpl-minimal` → `tpl-dev` → `tpl-java`) with project-specific environments that include pre-cloned repositories, build tools, and primed dependency caches.

## Setup

Add this directory as a search path in `~/.config/incus-spawn/config.yaml`:

```yaml
searchPaths:
  - /path/to/incus-spawn-templates
```

Then build and branch:

```shell
isx build tpl-quarkus
isx branch tpl-quarkus my-feature
```

## Templates

| Template | Parent | Description                                                          |
|----------|--------|----------------------------------------------------------------------|
| `tpl-quarkus` | `tpl-java` | Quarkus + quickstarts source, Podman, Gradle                         |
| `tpl-hibernate-orm` | `tpl-java` | Hibernate ORM source, Podman, Gradle                                 |
| `tpl-hibernate-reactive` | `tpl-hibernate-orm` | Hibernate Reactive source (includes ORM)                             |
| `tpl-tamboui` | `tpl-java` | Tamboui TUI framework source, Gradle, selected skills                |
| `tpl-incus-spawn` | `tpl-java` | incus-spawn itself — recursive development with Incus and COPR tools |

All templates inherit the `tpl-java` chain, which provides JDK 25, Maven, Claude Code, GitHub CLI, and tmux.

## Tools

| Tool | Description |
|------|-------------|
| `podman` | Podman with Docker socket compatibility, configured for Testcontainers |
| `gradle` | Gradle 9.4.1 (installed to `/opt`, symlinked to PATH) |
| `graalvm` | Oracle GraalVM for JDK 25 (installed to `/opt`, `native-image` on PATH) |

## Contributing

To add a new template, create a YAML file in `images/` — see the [incus-spawn documentation](https://github.com/Sanne/incus-spawn) for the image definition format. Custom tools go in `tools/`.
