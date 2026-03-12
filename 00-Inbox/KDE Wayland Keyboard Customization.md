
In Fedora 43 (and recent Plasma 6+ versions), the transition to Wayland means that traditional X11 tools like `xmodmap` or `setxkbmap` no longer work for the entire session. Instead, the **KWin compositor** handles keyboard mapping directly using the **XKB** (X Keyboard Extension) library.

Here is how to customize your layout depending on how deep you want to go.

---

## 1. Using System Settings (The Easiest Way)

For standard changes (swapping Caps Lock and Escape, adding extra languages, or changing the layout variant), use the built-in GUI.

1. Open **System Settings**.

2. Navigate to **Input Devices** → **Keyboard**.

3. Go to the **Layouts** tab.

4. **To add a language:** Click **+ Add**, select your language, and pick a specific **Variant** (e.g., "English (US, intl., with dead keys)").

5. **For Advanced Remapping:** Click the **Advanced** tab (sometimes found under "Configure keyboard options"). Here you can find toggles for:
    
    - **Caps Lock behavior** (e.g., "Make Caps Lock an additional Esc").1
        
    - **Switching to another layout** (e.g., "Alt+Shift" to toggle languages).
        
    - **Position of Compose Key**.
        

---

## 2. Creating a Custom "User" Layout (The Wayland Way)

If you need a layout that doesn't exist in the default list (e.g., a custom Neo or Dvorak mod), Wayland looks for files in your home directory before system directories.

1. **Create the directory:**

```
 mkdir -p ~/.config/xkb/symbols
```

2. **Create your custom file:** Create a file named `custom` (or any name) inside that folder.
    
```
nano ~/.config/xkb/symbols/custom
```
    
3. **Define your mapping:** Add your logic. For example, to swap `j` and `k`:
    
    Code snippet
    
```
xkb_symbols "my_mod" {
    include "us(basic)"
    key <AC07> { [ k, K ] };
    key <AC08> { [ j, J ] };
};
```
    
4. **Apply it:** In Plasma Wayland, you often have to manually edit your `kxkbrc` to point to this, as the GUI might not see local files yet.
    
    - Edit `~/.config/kxkbrc`.
        
    - Under `[Layout]`, set `LayoutList=custom` and `VariantList=my_mod`.
        
    - **Restart the session** (Log out and log back in).
        

---

## 3. Power-User Tool: Input Remapper

If you want a GUI that works perfectly on Wayland for complex macros, per-device remapping, or "hold for Shift, tap for Esc" behavior, **Input Remapper** is the gold standard for Fedora users.

1. **Install it:**
    
    Bash
    
```shell
sudo dnf install input-remapper
```
    
2. **Enable the service:**
    
    Bash
    
```shell
sudo systemctl enable --now input-remapper
```
    
3. Open the **Input Remapper** app from your menu. It works by creating a "virtual" keyboard, which bypasses Wayland's security restrictions on direct key manipulation.
    

---

## Summary of Tools

| **Method**          | **Best For...**                                         | **Persistence** |
| ------------------- | ------------------------------------------------------- | --------------- |
| **Plasma Settings** | Standard layouts & common swaps (Caps -> Esc).          | Permanent       |
| **localectl**       | Setting the system-wide layout (for SDDM login screen). | Permanent       |
| **~/.config/xkb**   | Professional/Complex custom layouts.                    | Permanent       |
| **Input Remapper**  | Gaming, macros, and per-device customization.           | Permanent       |

**Would you like me to help you write a specific XKB symbol file for a particular key remap you have in mind?**

---
## On this laptop 

the keyboard files are here 

```zsh
cd /usr/share/X11/xkb/symbols/
```

`evdev.xml` is here 

```zsh
cd /usr/share/X11/xkb/rules/
```

**To Edit The Keyboard Entries**:

```shell
cd ~/.config
nano kxkbrc
```

