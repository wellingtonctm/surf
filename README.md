# Customized Surf Browser

This repository contains my personalized build of [Surf](https://surf.suckless.org/), a minimalist web browser developed by the [suckless](https://suckless.org/) community. The primary modifications include:

- Integration of the [Web Search](https://surf.suckless.org/patches/web-search/) patch, customized to utilize Google as the default search engine.
- Adjustment of the default font size for improved readability.

## Features

### Web Search Integration

The [Web Search](https://surf.suckless.org/patches/web-search/) patch adds a convenient search functionality to Surf. In this build, it's configured to use Google Search by default. Press `MODKEY + s` to prompt a search input via `dmenu`.

**Configuration Snippet:**

```c
static char \*searchurl = "https://www.google.com/search?q=\%s";
```

*Note:* Ensure that `dmenu` is installed and properly configured to utilize this feature.

### Font Size Customization

To enhance readability, the default font size has been increased from 12 to 14.

**Configuration Snippet:**

```c
\[FontSize\] = \{ \{ .i = 14 \}, \},
```

This change is made in the `config.def.h` file before compiling the browser.

### Build Configuration

The `config.mk` file has been modified to use `webkit2gtk-4.0` instead of `webkit2gtk-4.1`, ensuring compatibility with systems where only version 4.0 is available.

**Modified `config.mk` Snippet:**

```make
GTKINC = \`pkg-config --cflags gtk+-3.0 gcr-3 webkit2gtk-4.0\`
GTKLIB = \`pkg-config --libs gtk+-3.0 gcr-3 webkit2gtk-4.0\`
WEBEXTINC = \`pkg-config --cflags webkit2gtk-4.0 webkit2gtk-web-extension-4.0 gio-2.0\`
WEBEXTLIBS = \`pkg-config --libs webkit2gtk-4.0 webkit2gtk-web-extension-4.0 gio-2.0\`
```

*Note:* Ensure that `webkit2gtk-4.0` and its development files are installed on your system.

## Installation

1. **Clone the Repository:**

   ```bash
   git clone https://github.com/wellingtonctm/surf.git
   cd surf
   ```

2. **Compile and Install:**

   Ensure you have the necessary dependencies installed, including `webkit2gtk` and `dmenu`.

   ```bash
   make clean install
   ```

   *Note:* You may need superuser privileges to install.

## Usage

Launch Surf with an optional URL:

```bash
surf \[URL\]
```

- Press `MODKEY + s` to initiate a Google search via `dmenu`.
- Use standard Surf keybindings for navigation and other operations.

## Credits

- **Surf Browser:** Developed by the [suckless](https://suckless.org/) community.
- **Web Search Patch:** Created by Bryon Meinka and Paras Kumar Langyan. [Patch Details](https://surf.suckless.org/patches/web-search/)

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.
