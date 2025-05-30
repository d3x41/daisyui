---
title: Use daisyUI with Tailwind CSS Standalone CLI
desc: How to run daisyUI with Tailwind CSS Standalone CLI without Node.js
---

<script>
  import Translate from "$components/Translate.svelte"
</script>

### 1. Get Tailwind CSS executable

Follow [Tailwind CSS guide](https://tailwindcss.com/blog/standalone-cli) and get the latest version of Tailwind CSS executable for your OS.

For example:

```sh:Terminal
# Run the corresponding command for your OS

# Linux
curl -sLo tailwindcss https://github.com/tailwindlabs/tailwindcss/releases/latest/download/tailwindcss-linux-arm64
curl -sLo tailwindcss https://github.com/tailwindlabs/tailwindcss/releases/latest/download/tailwindcss-linux-arm64-musl
curl -sLo tailwindcss https://github.com/tailwindlabs/tailwindcss/releases/latest/download/tailwindcss-linux-x64
curl -sLo tailwindcss https://github.com/tailwindlabs/tailwindcss/releases/latest/download/tailwindcss-linux-x64-musl

# MacOS
curl -sLo tailwindcss https://github.com/tailwindlabs/tailwindcss/releases/latest/download/tailwindcss-macos-arm64
curl -sLo tailwindcss https://github.com/tailwindlabs/tailwindcss/releases/latest/download/tailwindcss-macos-x64

# Windows
curl -sLo tailwindcss.exe https://github.com/tailwindlabs/tailwindcss/releases/latest/download/tailwindcss-windows-x64.exe
```

Make the file executable (For Linux and MacOS):

```sh:Terminal
chmod +x tailwindcss
```

### 2. Get daisyUI bundled JS file

Run this code to download latest version of daisyUI as a single js file and put it next to Tailwind's executable file.

```sh:Terminal
curl -sLO https://github.com/saadeghi/daisyui/releases/latest/download/daisyui.js
curl -sLO https://github.com/saadeghi/daisyui/releases/latest/download/daisyui-theme.js
```

### 3. Add Tailwind CSS and daisyUI

Add Tailwind CSS and daisyUI to your CSS file.  
Address your HTML and other markup files in the `source` function.

```postcss:input.css
@import "tailwindcss" source(none);
@source "./public/*.{html,php,erb}";
@plugin "./daisyui.js";

/* Optional for custom themes – Docs: https://daisyui.com/docs/themes/#how-to-add-a-new-custom-theme */
@plugin "./daisyui-theme.js"{
  /* custom theme here */
}
```

### 4. Build CSS

Run this command to build the CSS file using Tailwind CSS executable.  
Using `--watch` will automatically update the output.css file when you change the input.css file.  
For CI/CD, run the command without `--watch` to generate the output.css file once.

```sh:Terminal
./tailwindcss -i input.css -o output.css --watch
# For Windows
tailwindcss.exe -i input.css -o output.css --watch
```

Now you can use daisyUI class names!
