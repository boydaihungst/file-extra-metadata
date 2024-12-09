# file-extra-metadata

<!--toc:start-->

- [file-extra-metadata](#file-extra-metadata)
  - [Preview](#preview)
    - [Before:](#before)
    - [After:](#after)
  - [Requirements](#requirements)
  - [Installation](#installation)
  - [For developer](#for-developer)
  <!--toc:end-->

This is a Yazi plugin that replaces the default file previewer and spotter with extra information.

## Preview

### Before:

- Previewer

  ![Before preview](statics/2024-11-17-12-06-24.png)

- Spotter (yazi >= v0.4 after 21/11/2024)

  ![Before spot](statics/2024-11-21-04-19-01.png)

### After:

- Previewer

![After previewer](statics/2024-11-21-05-27-48.png)

- Spotter (yazi >= v0.4 after 21/11/2024)

![After spotter](statics/2024-11-21-05-29-50.png)

## Requirements

- [yazi >=0.4](https://github.com/sxyazi/yazi)
- Tested on Linux. For MacOS, Windows: some fields will shows empty values.

## Installation

Install the plugin:

```sh
ya pack -a boydaihungst/file-extra-metadata
```

Create `~/.config/yazi/yazi.toml` and add:

```toml
[plugin]
  append_previewers = [
    { name = "*", run = "file-extra-metadata" },
  ]
  # yazi v0.4 after 21/11/2024
  # Setup keybind for spotter: https://github.com/sxyazi/yazi/pull/1802
  append_spotters = [
    { name = "*", run = "file-extra-metadata" },
  ]
```

or

```toml
[plugin]
  previewers = [
    # ... the rest
    # disable default file plugin { name = "*", run = "file" },
    { name = "*", run = "file-extra-metadata" },
  ]
  # yazi v0.4 after 21/11/2024
  # Setup keybind for spotter: https://github.com/sxyazi/yazi/pull/1802
  spotters = [
    # ... the rest
    # Fallback
    # { name = "*", run = "file" },
    { name = "*", run = "file-extra-metadata" },
  ]
```

## For developer

If you want to compile this with other spotter/previewer:

```lua
require("file-extra-metadata"):render_table(job, { show_plugins_section = true })
```
