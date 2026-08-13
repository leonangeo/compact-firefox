# Compact Firefox

## Overview
- A *Firefox UI modification* to *merge the address and tab bars into a single line*, maximizing vertical screen space *without extensions*.

## 1. Result
The default Firefox layout consumes vertical space with multiple bars:
<img width="1076" height="209" alt="image" src="https://github.com/user-attachments/assets/e297358e-2863-4998-b8dd-d804d73472b3" /> 

After applying this tweak, both bars are merged into one, freeing up screen space:
<img width="1425" height="274" alt="image" src="https://github.com/user-attachments/assets/9cd618ad-fa76-4d13-8044-51bbf57ec17a" />

*Note: Developed and tested on Firefox 153.0.4 (Windows 64-bit). The CSS architecture ensures high compatibility with other recent versions.*
## 2. Setup

1. **Enable UI customization:**
   - Go to `about:config` and accept the risk.
   - Search for `toolkit.legacyUserProfileCustomizations.stylesheets` and toggle its value to `true`.

2. **Access Profile Folder:**
   - Go to `about:support`.
   - Find **Profile Folder** in the "Application Basics" table and click **Open Folder**.

3. **Create file structure:**
   - Inside your profile folder, create a new folder named `chrome`.
   - Inside `chrome`, create a text file named `userChrome.css`.

4. **Inject CSS:**
   - Open `userChrome.css` and paste the code below (adjust `50vw` if needed):

```css
:root {
  --uc-nav-width: 50vw;
}

#TabsToolbar {
  margin-left: var(--uc-nav-width) !important;
}

#nav-bar {
  margin-top: calc(-1 * (var(--tab-min-height) + 2 * var(--tab-block-margin, 0px))) !important;
  width: var(--uc-nav-width) !important;
  background: transparent !important;
  box-shadow: none !important;
  position: relative !important;
  z-index: 2 !important;
}

.titlebar-spacer {
  display: none !important;
}
```

5. **Apply and adjust:**
   - Save the file and **restart Firefox**.
   - If tabs overlap the address bar, tweak the `50vw` value in the code. (The default `50vw` works well for 1080p but may vary by resolution).

## 3. Advanced Customization
- Right-click the toolbar -> **Customize Toolbar...** to drag and drop extensions or buttons as desired.

## 4. Contributing
- If this helped you, consider leaving a star!
- Contributions are welcome. Feel free to open an **Issue** for bug reports or submit a **Pull Request** with improvements.
- Built for personal use, shared to help others!
