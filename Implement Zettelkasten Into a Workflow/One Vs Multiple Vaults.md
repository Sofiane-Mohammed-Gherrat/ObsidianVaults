
## 1. 💭 One Vault or Many?

|**Approach**|**✔ When to use**|**⚠ Trade‑offs**|
|---|---|---|
|**Single Vault**|Your learning domains _intersect_ or share ideas (like linking how _programming_ automates _marketing_ or to track Blender’s impact on app design). Promotes a cohesive Zettelkasten—captures emergent patterns across fields.|([Preslav Rachev](https://preslav.me/2022/10/19/do-you-use-one-or-more-obsidian-vaults/?utm_source=chatgpt.com "Do You Use One Or Multiple Obsidian Vaults? · Preslav Rachev")).- Theme or shortcut conflicts if you try to customize per domain. \||
|**Multiple Vaults**|Your domains are truly separate (**e.g.**, Blender 3D vault full of large assets, marketing vault with CRM templates, programming vault with CI/CD infrastructure), or you need different config/plugin sets.|- No built‑in wikilinks or global graph across vaults. Backlinks don't cross vault boundaries. (Cross-vault linking is URL-based only.)- Need to replicate plugin settings and hotkeys per vault.([Obsidian Forum](https://forum.obsidian.md/t/separate-vaults-or-separate-folders/68978?utm_source=chatgpt.com "Separate Vaults or Separate Folders? - Help - Obsidian Forum"))|

### What the Community Says

Preslav Rachev’s survey found most users strongly favor a single vault unless there's a compelling reason to split—great for discovery, backups, and linkage rewards([Preslav Rachev](https://preslav.me/2022/10/19/do-you-use-one-or-more-obsidian-vaults/?utm_source=chatgpt.com "Do You Use One Or Multiple Obsidian Vaults? · Preslav Rachev")).

Reddit users highlight both ends of the spectrum:

> _“I separate my vaults by project / concern… For me the biggest pro of having separate vaults is the ability to theme them differently which helps with the cognitive framing.”_ — user _ourobo‑ros_([Reddit](https://www.reddit.com/r/ObsidianMD/comments/zpnq4x/who_uses_multiple_vaults_vs_just_one/ "Who uses multiple vaults vs just one? : r/ObsidianMD"))

> _“I divided my vault into four separate vaults… managing such a large vault had become nearly impossible… I followed the ‘divide and conquer’ tactic.”_ — _Paladin_ (23 k notes, 64 plugins split into more usable parts)([Obsidian Forum](https://forum.obsidian.md/t/dividing-my-big-vault-into-smaller-ones-made-it-better/91515 "Dividing my big vault into smaller ones made it better - Share & showcase - Obsidian Forum"))

---

## 2. Recommended Path for You

**🔘 Start with one vault**, especially if you're still building your knowledge systems:
- Create folders such as `Learning/Programming`, `Learning/Blender`, `Learning/Marketing`.
- Tag notes with `#programming`, `#art`, `#digital‑marketing` etc.
- Use a **single Map of Contents (MOC)** to link across expertise areas.

**🟡 Split later only if needed**, e.g.:
- You hit serious lag or delays indexing due to excessive plugins or metadata.
- You require different plugin configs, or want to share one vault (like marketing deliverables) publicly while keeping the rest private.
- You want totally different themes, hotkeys, or .obsidian directories per domain.

If you do split, preserve portability: copy the folder (and attachments) out of your main vault and open it as a new vault. Obsidian rebuilds metadata automatically([Obsidian Forum](https://forum.obsidian.md/t/how-to-split-one-vault-into-two-or-more/56796?utm_source=chatgpt.com "How to split one vault into two (or more) - Help")).

---

## 3. Referencing Across Vaults: How & When

If you go multiple‑vault, linking _between_ vaults is possible—but limited:
- **No backlink previews, no graph view, no live wikilink auto-suggestions**.
- **Search only scans one vault at a time**—you can’t see global unlinked mentions.

### 3.1 Built‑in Method: **Obsidian URI**

1. In Vault A, open the note you want to reference.
2. Right‑click the note tab → **Copy Obsidian URL**. You’ll get a link like:
    ```bash
    obsidian://open?vault=VaultA&file=My%20Blender%20Tip.md
    ```

3. In Vault B, paste that link as a standard Markdown link:
    ```markdown
    [Memory footprint tip in Blender](obsidian://open?vault=VaultA&file=My%20Blender%20Tip.md)
    ```    

Clicking this will prompt Obsidian to switch vaults and open the note (provided VaultA exists in Obsidian's vault list)([Fork My Brain](https://notes.nicolevanderhoeven.com/obsidian-playbook/Using%2BObsidian/01%2BFirst%2Bsteps%2Bwith%2BObsidian/Working%2Bwith%2Bmultiple%2Bvaults?utm_source=chatgpt.com "Working with multiple vaults")).

### 3.2 Advanced Option: **Advanced URI Plugin (requires install in both vaults)**

- **Pros**: Stable even if you rename or move the file. Uses a `UID` in the note's YAML.
- Generated link looks like:
    ```shell
    obsidian://advanced-uri?vault=VaultA&uid=123e4567‑…
    ```

- Paste in the usual way. When clicked, Obsidian switches vaults and locates the note reliably([Obsidian Forum](https://forum.obsidian.md/t/linking-to-a-note-in-a-different-vault/40546?utm_source=chatgpt.com "Linking to a note in a different vault - Help")).

🎯 Tip: store UID-style cross-vault links in a MOC of external links—especially useful when brainstorming or planning multi‑domain projects.

---

## 4. What to Watch Out For

- **Missing backlinks**: Cross-vault links don’t backfill like internal links do. Your graph remains local.
- **Performance**: On mobile, switching vaults can be slow. Only one vault can be open at a time on iOS/Android([Obsidian Forum](https://forum.obsidian.md/t/dividing-my-big-vault-into-smaller-ones-made-it-better/91515 "Dividing my big vault into smaller ones made it better - Share & showcase - Obsidian Forum")).
- **Theme/Plugin overhead**: Every vault keeps its own `.obsidian` folder—maintaining multiple vaults means replicating config setups.
- **Avoid nesting vaults**: Obsidian strongly discourages vaults inside vault folders. Nested vaults can cause invisible data corruption or link breakages([Obsidian Forum](https://forum.obsidian.md/t/separate-vaults-or-separate-folders/68978?utm_source=chatgpt.com "Separate Vaults or Separate Folders? - Help - Obsidian Forum")).

---

## ✅ Final Call (by domain):

|**Learning Track**|Suggested Setup|
|---|---|
|**Programming**|Single vault → `/Learning/Programming` → Add `#programming`, use code block templates.|
|**Blender (3D)**|Still usually fits inside one vault, but if it balloons (tons of embedded PNGs, assets), split after you see performance issues.|
|**Marketing**|Start integrated—many campaigns depend on programming, automation, analytics; but split later if sharing, templates/plugin isolation, or compliance matters.|

---

### 🌱 Suggested Initial Folder Structure

```lua
📁 YourVault/
 ├── Dashboard.md          ← MOC root
 ├── Templates/
 ├── Fleeting/            ← short notes to process
 ├── Learning/            ← permanent
 │    ├── Programming/
 │    ├── Blender/
 │    └── Marketing/
 ├── Projects/            -- For Blender only
 ├── Literature/          -- Skip 
 ├── Daily/               -- Skip  
 └── Assets/              -- Skip
```

**Backlinking strategy**:

- Use internal `[[wikilinks]]` within `Learning/` and `Projects/`.
- Use `#tags` top-level like `#code-sysdesign`, `#3d‑shading`, `#ads‑metrics`.
- As your graph grows, add MOCs like `Programming MOC`, `Marketing MOC`.

---

✅ **If you're just starting or building your Zettelkasten**, go with **one vault**. It offers the best cross-linking, easier backups, simpler syncing and growth.

⏳ **Only split** when the overhead becomes real—either performance or configuration overload. And if you do, you already know that cross‑vault reference is still workable via Obsidian URL or Advanced URI.

Need help crafting post‑split template systems or naming conventions (UID-based or descriptive files) or automating the split‑workflow? I’m happy to help you customize your toolkit.