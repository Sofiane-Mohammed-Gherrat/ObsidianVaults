# How to make the extension match the style of the editor 📄

To align the **Markdown All in One** (specifically the Markdown Preview) with your Catppuccin theme and font preferences, you need to modify your VS Code `settings.json`.

VS Code's Markdown preview is essentially a mini web browser, so we use CSS to override its default styling.

### 1. The Configuration

Open your `settings.json` (via `Cmd+Shift+P` / `Ctrl+Shift+P` and typing "Open User Settings (JSON)") and add these properties:

```json
{
    "markdown.preview.fontFamily": "'Your Font Name', monospace",
    "markdown.preview.fontSize": 14,
    "markdown.styles": [
        "https://cdn.jsdelivr.net/npm/@catppuccin/vscode@latest/dist/catppuccin.css"
    ],
    "markdown.extension.preview.autoShowPreviewToSide": true,
    "markdown.preview.lineHeight": 1.6
}

```

### 2. Custom CSS for H1 and Theming

To fix the specific **H1 break line** issue and ensure the colors are perfect, you should create a small local CSS file.

1. Create a file named `markdown-style.css` in a safe place (like `~/.config/vscode/markdown-style.css`).
2. Paste the following:

```css
/* Remove the border/line under H1 */
h1 {
    border-bottom: none !important;
    padding-bottom: 0 !important;
    margin-bottom: 10px !important;
}

/* Force Catppuccin-style background and text if the CDN fails */
body {
    background-color: #1e1e2e !important; /* Catppuccin Mocha Base */
    color: #cdd6f4 !important;            /* Catppuccin Mocha Text */
    font-family: var(--vscode-editor-font-family);
}

/* Style headers to match Catppuccin accents */
h1, h2, h3 { color: #89b4fa !important; } /* Blue accent */

```

3. Update your `settings.json` to point to this file:

```json
"markdown.styles": [
    "C:/Users/YourName/.config/vscode/markdown-style.css" 
]

```

*(Use the absolute path to wherever you saved that CSS file).*

### 3. Summary of Fixes

* **Theme Match:** By using `markdown.styles`, we inject Catppuccin colors into the preview pane.
* **Font Match:** `markdown.preview.fontFamily` syncs the preview font with your editor font.
* **H1 Break Line:** The CSS `border-bottom: none !important;` removes that horizontal line that VS Code usually places under top-level headings.

**A quick heads-up:** If you are using the **Catppuccin** extension itself, it actually includes a setting to theme the markdown preview automatically. Check if you have `"catppuccin.accent": "blue"` or similar enabled, as it often handles the colors for you!

Would you like me to help you find the exact Hex codes for a specific Catppuccin flavor (Latte, Frappé, Macchiato, or Mocha)?

# Match Style With Mocha Flavor 

Since you're using **Mocha**, we'll use the specific palette hex codes (Base: `#1e1e2e`, Text: `#cdd6f4`, Blue: `#89b4fa`) to ensure a perfect match.

Because the **Markdown All in One** extension uses the built-in VS Code preview engine, you can control the style entirely through a local CSS file.

### 1. Create your Mocha CSS file

Create a file named `mocha-markdown.css` (e.g., in your home folder or VS Code config folder) and paste this:

```css
/* mocha-markdown.css */
body {
    background-color: #1e1e2e !important;
    color: #cdd6f4 !important;
    /* This variable automatically pulls your editor font */
    font-family: var(--vscode-editor-font-family), "Inter", sans-serif;
    line-height: 1.6;
}

/* Remove the line (border) after H1 */
h1 {
    border-bottom: none !important;
    margin-bottom: 0.5em !important;
    padding-bottom: 0 !important;
    color: #89b4fa !important; /* Mocha Blue */
}

h2, h3, h4 {
    color: #89b4fa !important;
    border-bottom: 1px solid #313244 !important; /* Surface0 color for subtle lines on H2+ */
}

code {
    background-color: #313244 !important; /* Surface0 */
    color: #f5e0dc !important;            /* Rosewater */
    border-radius: 4px;
    padding: 2px 4px;
}

blockquote {
    border-left: 4px solid #f5c2e7 !important; /* Pink accent */
    color: #bac2de !important;                 /* Subtext1 */
    background-color: #181825 !important;      /* Mantle */
}

```

### 2. Update VS Code Settings

Open your `settings.json` and add these lines. **Crucially**, make sure the path to the CSS file is absolute.

```json
{
    "markdown.preview.fontFamily": "var(--vscode-editor-font-family)",
    "markdown.styles": [
        "/Users/YOUR_NAME/path/to/mocha-markdown.css"
    ],
    "markdown.preview.markEditorSelection": true
}

```

*(On Windows, the path would look like `C:\\Users\\Name\\Documents\\mocha-markdown.css`)*.

### 3. Why this works

* **The H1 Issue:** VS Code's default stylesheet applies `border-bottom: 1px solid var(--vscode-settings-dropdownListBorder)` to `h1`. Our CSS overrides this with `none !important`.
* **The Font:** Using `var(--vscode-editor-font-family)` is the cleanest way to ensure that if you change your editor font (to JetBrains Mono, Fira Code, etc.), the Markdown preview updates automatically.
* **Mocha Colors:** By manually setting `body` and `h1` colors, we prevent the "flash" of white or default gray when opening a preview.

**One final tip:** After saving the CSS and `settings.json`, you might need to close and reopen your Markdown preview (`Ctrl+Shift+V`) for the changes to trigger
