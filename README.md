# Skills

Colección personal de skills para Claude Code.

| Skill | Invocación | Descripción |
|---|---|---|
| [spec-generator](spec-generator/SKILL.md) | `/spec-generator` (solo manual) | Entrevista iterativa que genera especificaciones funcionales `specs/REQ-NNN-slug/spec.md` agnósticas a la tecnología (EARS + Dado/Cuando/Entonces). |

## Instalación (a nivel de usuario)

Copia la carpeta de la skill a `~/.claude/skills/`:

```bash
# Git Bash / macOS / Linux
mkdir -p ~/.claude/skills && cp -r spec-generator ~/.claude/skills/
```

```powershell
# PowerShell
New-Item -ItemType Directory -Force "$HOME\.claude\skills" | Out-Null
Copy-Item -Recurse -Force .\spec-generator "$HOME\.claude\skills\"
```

Vuelve a ejecutar el comando cada vez que modifiques la skill en este repo.
