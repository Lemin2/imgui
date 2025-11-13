# imgui (ESP-IDF Component)

This is a template for a GitHub repository that mirrors Dear ImGui core files as an ESP-IDF component and auto-syncs to upstream releases via GitHub Actions.

What you get:
- Core sources: `imgui*.{h,cpp}`, `imstb_*.h`, `imconfig.h`, `imgui_internal.h`, `LICENSE.txt`.
- `misc/` directory from upstream (helpers/tools/fonts utils, etc.).
- `imgui_demo.cpp` included by default (you can set `include_demo=false` when manually dispatching the workflow to exclude it).
- Auto-generated `CMakeLists.txt` and `idf_component.yml` (version equals upstream tag), plus a Git tag `idf-<tag>`.

## How to use this template in your repo (Lemin2/imgui)

1. Create a new GitHub repository named `Lemin2/imgui` (or use the existing one).
2. Copy the files from this `misc/idf_component_repo_template/` directory into the root of your repo, preserving the `.github/workflows/sync-imgui.yml` path.
3. Commit and push.
4. Go to GitHub → Actions → "sync-upstream-imgui" → Run workflow. Demo is included by default; you can set `include_demo=false` if you want to exclude it.
5. The workflow will replace the repo contents (keeps `.git` and `.github`), stage upstream core files, generate build files, commit, and push a tag `idf-<upstreamTag>`.

## Use in an ESP-IDF app

In your app's `CMakeLists.txt`:

```cmake
idf_component_register(SRCS main.c REQUIRES imgui)
```

In code:

```c
#include "imgui.h"
```

Then add your own rendering backend (e.g., your existing hardware or the standalone software renderer you built earlier) as another component and link it.
The `misc/` directory is mirrored for convenience; if you don't need it in your final firmware image, exclude it at packaging stage.

## Notes
- The workflow is designed to run on `ubuntu-latest` and uses `curl`/`jq`.
- It pushes to `main` (or `master` if `main` doesn't exist). Adjust the branch logic if needed.
- The license is MIT from the upstream `LICENSE.txt`.
- This mirror does not restrict chip targets (`idf_component.yml` has no `targets` field by default).
- You can edit other metadata in `idf_component.yml` as needed; on each sync the `version` will be set to the upstream tag.
