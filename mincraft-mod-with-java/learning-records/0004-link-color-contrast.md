# Learning Record: High Contrast Links Required for Dark Mode

**Issue:**
The user reported that the hyperlink color used in Lesson 3 (and previous lessons) was too similar to the dark background color, making it nearly invisible. The original CSS used `var(--info)` (#40c4ff, a light blue) against a dark blue/purple background (`#0f0f1a` / `#1a1a2e`). While mathematically different, the hue similarity made it visually blend in for the user.

**Action Taken:**
1. Modified the global CSS for `a` tags in all existing HTML files.
2. Changed the link color to `#64ffda` (a very bright, distinct teal).
3. Added a permanent bottom border to links (`border-bottom: 1px solid rgba(100, 255, 218, 0.3)`) to provide a structural visual cue regardless of color.
4. Added a hover effect that fills the background slightly for better interactivity.
5. Updated `NOTES.md` to permanently record this user preference.

**Future Implication:**
In all future generated lessons, reference documents, or any HTML outputs for this user, hyperlinks MUST use high-contrast, non-blue bright colors (like `#64ffda` or `#ffcc00`) and should feature an underline or bottom border by default to ensure maximum visibility and accessibility.
