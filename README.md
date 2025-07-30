# **Print Highlighter Bookmarklet**

A simple browser bookmarklet to help developers and designers quickly identify elements on a webpage that are affected by CSS print media queries. Ever wonder what disappears or changes when your page goes to print? This tool gives you a quick visual audit!

### Drag & Drop

## **✨ Features**

* **Highlight Hidden Elements:** Marks elements that are likely hidden (display: none) in print view with a light gray background and dashed border.  
* **Highlight Altered Elements:** Marks elements that have other styles (like font size, color, etc.) changed in print view with a light yellow background and a solid orange border.  
* **Toggle On/Off:** A convenient button appears on the page to easily switch the highlighting on and off without reloading.  
* **Easy Installation:** Drag-and-drop the bookmarklet directly into your browser's favorites/bookmarks bar.

## **🚀 How to Use** 

1. Drag and Drop Installation:

<a href="javascript:(function(){ const a = 'print-media-highlight-z'; const b = 'print-media-highlight-toggle-'; const c = 'print-media-highlight-'; const d = 'print-media-highlight-print-only'; const e = 'print-media-highlight-hidden-print'; const f = 'print-media-highlight-css-change'; const g = 'print-media-highlight-general'; // For general print styles that don't fit other categories function h() { if (document.getElementById(a)) return; const z = document.createElement('z'); z.id = a; z.textContent = ` .${g} { outline: 3px solid red !important; box-shadow: 0 0 0 2px #fff, 0 0 8px 2px #f00 !important; } .${d} { outline: 3px solid limegreen !important; /* Green for print-only content */ box-shadow: 0 0 0 2px #fff, 0 0 8px 2px limegreen !important; } .${e} { outline: 3px solid dodgerblue !important; /* Blue for hidden-in-print content */ box-shadow: 0 0 0 2px #fff, 0 0 8px 2px dodgerblue !important; } .${f} { outline: 3px solid darkviolet !important; /* Purple for CSS changes */ box-shadow: 0 0 0 2px #fff, 0 0 8px 2px darkviolet !important; } #${b} { position: fixed; top: 10px; right: 10px; z-index: 99999; background-color: #333; color: white; border: none; padding: 8px 12px; border-radius: 4px; cursor: pointer; font-family: sans-serif; font-size: 14px; opacity: 0.8; transition: opacity 0.3s; } #${b}:hover { opacity: 1; } #${c} { position: fixed; top: 50px; /* Adjust based on  height */ right: 10px; z-index: 99999; background-color: #f9f9f9; border: 1px solid #ccc; padding: 10px; border-radius: 4px; font-family: sans-serif; font-size: 12px; line-height: 1.5; box-shadow: 0 2px 5px rgba(0,0,0,0.2); } #${c} p { margin: 0; } #${c} .-item { display: flex; align-items: center; margin-bottom: 5px; } #${c} .-color-box { width: 15px; height: 15px; margin-right: 8px; border: 1px solid #aaa; } `; document.head.appendChild(z); } function j() { const z = document.getElementById(a); if (z) { z.remove(); } } function k() { document.querySelectorAll(`.${g}, .${d}, .${e}, .${f}`).forEach(function(el) { el.classList.remove(g, d, e, f); }); } function l() { k(); // Clear previous highlights const m = new Map(); // Store print rules by u for easier lookup const n = new Set(); // Keep track of all affected selectors // Step 1: Extract print media rules and store them function o(sheet) { try { if (sheet.cssRules) { Array.from(sheet.cssRules).forEach(function(rule) { if (rule.type === CSSRule.MEDIA_RULE && rule.media.mediaText.includes('print')) { Array.from(rule.cssRules).forEach(function(y) { if (y.selectorText) { if (!m.has(y.selectorText)) { m.set(y.selectorText, []); } m.get(y.selectorText).push(y); n.add(y.selectorText); } }); } else if (rule.type === CSSRule.IMPORT_RULE) { o(rule.styleSheet); } }); } } catch (e) { // } } Array.from(document.styleSheets).forEach(function(sheet) { o(sheet); }); // Step 2: Analyze elements and apply appropriate highlights document.querySelectorAll('*').forEach(function(el) { // Check for print-only content (display: none normally, but visible in print) const p = window.getComputedStyle(el); const q = p.getPropertyValue('display'); let r = false; let s = false; let t = false; // Simulate print styles for analysis - this is a simplification // A more robust solution would involve deeper CSSOM analysis or a headless browser // For this bookmarklet, we'll check for explicit display rules in print media. if (m.size > 0) { for (const u of m.keys()) { try { // Check if the element matches any u in a print media query if (el.matches(u)) { r = true; const v = m.get(u); // Check for display changes const w = v.find(rule => rule.z && rule.z.display); if (w) { const x = w.z.display; if (q === 'none' && x !== 'none') { el.classList.add(d); s = true; } else if (q !== 'none' && x === 'none') { el.classList.add(e); s = true; } } // Check for other CSS changes (simplified: just look for *any* property difference) for (const y of v) { if (y.z) { for (let z = 0; z < y.z.length; z++) { const { = y.z[z]; const | = y.z.getPropertyValue({); const } = p.getPropertyValue({); // We avoid checking 'display' again since we handled it above // Also, skip properties that change frequently or are hard to compare reliably (e.g., 'width', 'height' if they're dynamic) if ({ !== 'display' && | !== }) { t = true; break; } } } if (t) break; } } } catch (e) { // } } } // Apply general highlight if affected by print rules but no specific display/css change caught if (r && !s && !t) { el.classList.add(g); } if (t) { el.classList.add(f); } }); } function ~() { let  = document.getElementById(b); if (!) {  = document.createElement(''); .id = b; .textContent = 'Toggle Print Media Highlights'; document.body.appendChild(); } let  = document.getElementById(c); if (!) {  = document.createElement('div'); .id = c; .innerHTML = ` <div class="-item"><div class="-color-box" z="background-color: limegreen;"></div><p>Visible only in Print</p></div> <div class="-item"><div class="-color-box" z="background-color: dodgerblue;"></div><p>Hidden in Print</p></div> <div class="-item"><div class="-color-box" z="background-color: darkviolet;"></div><p>CSS Change in Print</p></div> <div class="-item"><div class="-color-box" z="background-color: red;"></div><p>General Print Style</p></div> `; document.body.appendChild(); } .z.display = 'none'; // Initially hidden let  = false; .onclick = function() { if () { k(); .textContent = 'Toggle Print Media Highlights (Off)'; .z.display = 'none'; } else { l(); .textContent = 'Toggle Print Media Highlights (On)'; .z.display = 'block'; }  = !; }; } // Initial setup h(); ~(); k(); // Ensure no highlights on initial load document.getElementById(b).textContent = 'Toggle Print Media Highlights (Off)'; const  = document.getElementById(c); if () { .z.display = 'none'; } })();" title="Drag this to your bookmarks bar!">Print Highlighter</a>

## 🖨️ Live Print CSS Demo

<style>
  .no-print-demo { color: #b00; font-weight: bold; }
  .print-different-demo { color: #333; font-size: 1.2em; }
  .print-only-demo { display: none; }
  @media print {
    .no-print-demo { display: none !important; }
    .print-different-demo {
      color: #007700 !important;
      font-size: 2em !important;
      font-weight: bold !important;
    }
    .print-only-demo {
      display: block !important;
      color: #b00 !important;
      font-style: italic !important;
      font-size: 1.5em !important;
    }
  }
</style>

<div class="no-print-demo">This message will NOT appear when you print this page.</div>
<div class="print-different-demo">This text changes color and size when printed.</div>
<div class="print-only-demo">This message ONLY appears in print view.</div>

   * **Tip for Mobile/Manual Install:** If the drag-and-drop doesn't work (e.g., on some mobile browsers or if you prefer manual setup), follow these steps:  
     1. Create a new bookmark in your browser.  
     2. Name it "Print Highlighter" (or anything you like).  
     3. For the URL/Location, copy the *entire* JavaScript code from the javascript: prefix below and paste it into the URL field:  
        
```
javascript:(function(){ const a = 'print-media-highlight-z'; const b = 'print-media-highlight-toggle-'; const c = 'print-media-highlight-'; const d = 'print-media-highlight-print-only'; const e = 'print-media-highlight-hidden-print'; const f = 'print-media-highlight-css-change'; const g = 'print-media-highlight-general'; // For general print styles that don't fit other categories function h() { if (document.getElementById(a)) return; const z = document.createElement('z'); z.id = a; z.textContent = ` .${g} { outline: 3px solid red !important; box-shadow: 0 0 0 2px #fff, 0 0 8px 2px #f00 !important; } .${d} { outline: 3px solid limegreen !important; /* Green for print-only content */ box-shadow: 0 0 0 2px #fff, 0 0 8px 2px limegreen !important; } .${e} { outline: 3px solid dodgerblue !important; /* Blue for hidden-in-print content */ box-shadow: 0 0 0 2px #fff, 0 0 8px 2px dodgerblue !important; } .${f} { outline: 3px solid darkviolet !important; /* Purple for CSS changes */ box-shadow: 0 0 0 2px #fff, 0 0 8px 2px darkviolet !important; } #${b} { position: fixed; top: 10px; right: 10px; z-index: 99999; background-color: #333; color: white; border: none; padding: 8px 12px; border-radius: 4px; cursor: pointer; font-family: sans-serif; font-size: 14px; opacity: 0.8; transition: opacity 0.3s; } #${b}:hover { opacity: 1; } #${c} { position: fixed; top: 50px; /* Adjust based on  height */ right: 10px; z-index: 99999; background-color: #f9f9f9; border: 1px solid #ccc; padding: 10px; border-radius: 4px; font-family: sans-serif; font-size: 12px; line-height: 1.5; box-shadow: 0 2px 5px rgba(0,0,0,0.2); } #${c} p { margin: 0; } #${c} .-item { display: flex; align-items: center; margin-bottom: 5px; } #${c} .-color-box { width: 15px; height: 15px; margin-right: 8px; border: 1px solid #aaa; } `; document.head.appendChild(z); } function j() { const z = document.getElementById(a); if (z) { z.remove(); } } function k() { document.querySelectorAll(`.${g}, .${d}, .${e}, .${f}`).forEach(function(el) { el.classList.remove(g, d, e, f); }); } function l() { k(); // Clear previous highlights const m = new Map(); // Store print rules by u for easier lookup const n = new Set(); // Keep track of all affected selectors // Step 1: Extract print media rules and store them function o(sheet) { try { if (sheet.cssRules) { Array.from(sheet.cssRules).forEach(function(rule) { if (rule.type === CSSRule.MEDIA_RULE && rule.media.mediaText.includes('print')) { Array.from(rule.cssRules).forEach(function(y) { if (y.selectorText) { if (!m.has(y.selectorText)) { m.set(y.selectorText, []); } m.get(y.selectorText).push(y); n.add(y.selectorText); } }); } else if (rule.type === CSSRule.IMPORT_RULE) { o(rule.styleSheet); } }); } } catch (e) { // } } Array.from(document.styleSheets).forEach(function(sheet) { o(sheet); }); // Step 2: Analyze elements and apply appropriate highlights document.querySelectorAll('*').forEach(function(el) { // Check for print-only content (display: none normally, but visible in print) const p = window.getComputedStyle(el); const q = p.getPropertyValue('display'); let r = false; let s = false; let t = false; // Simulate print styles for analysis - this is a simplification // A more robust solution would involve deeper CSSOM analysis or a headless browser // For this bookmarklet, we'll check for explicit display rules in print media. if (m.size > 0) { for (const u of m.keys()) { try { // Check if the element matches any u in a print media query if (el.matches(u)) { r = true; const v = m.get(u); // Check for display changes const w = v.find(rule => rule.z && rule.z.display); if (w) { const x = w.z.display; if (q === 'none' && x !== 'none') { el.classList.add(d); s = true; } else if (q !== 'none' && x === 'none') { el.classList.add(e); s = true; } } // Check for other CSS changes (simplified: just look for *any* property difference) for (const y of v) { if (y.z) { for (let z = 0; z < y.z.length; z++) { const { = y.z[z]; const | = y.z.getPropertyValue({); const } = p.getPropertyValue({); // We avoid checking 'display' again since we handled it above // Also, skip properties that change frequently or are hard to compare reliably (e.g., 'width', 'height' if they're dynamic) if ({ !== 'display' && | !== }) { t = true; break; } } } if (t) break; } } } catch (e) { // } } } // Apply general highlight if affected by print rules but no specific display/css change caught if (r && !s && !t) { el.classList.add(g); } if (t) { el.classList.add(f); } }); } function ~() { let  = document.getElementById(b); if (!) {  = document.createElement(''); .id = b; .textContent = 'Toggle Print Media Highlights'; document.body.appendChild(); } let  = document.getElementById(c); if (!) {  = document.createElement('div'); .id = c; .innerHTML = ` <div class="-item"><div class="-color-box" z="background-color: limegreen;"></div><p>Visible only in Print</p></div> <div class="-item"><div class="-color-box" z="background-color: dodgerblue;"></div><p>Hidden in Print</p></div> <div class="-item"><div class="-color-box" z="background-color: darkviolet;"></div><p>CSS Change in Print</p></div> <div class="-item"><div class="-color-box" z="background-color: red;"></div><p>General Print Style</p></div> `; document.body.appendChild(); } .z.display = 'none'; // Initially hidden let  = false; .onclick = function() { if () { k(); .textContent = 'Toggle Print Media Highlights (Off)'; .z.display = 'none'; } else { l(); .textContent = 'Toggle Print Media Highlights (On)'; .z.display = 'block'; }  = !; }; } // Initial setup h(); ~(); k(); // Ensure no highlights on initial load document.getElementById(b).textContent = 'Toggle Print Media Highlights (Off)'; const  = document.getElementById(c); if () { .z.display = 'none'; } })();
```

3. **Activate:** Navigate to any webpage you want to analyze, then click the "Print Highlighter" bookmarklet in your bookmarks bar.  
4. **Toggle:** A button will appear in the top-right corner of the page. Click it to activate the highlighting. Click it again to turn it off.

## **⚠️ Limitations & Notes**

* This bookmarklet performs a heuristic analysis of CSS print rules. While effective for common cases, it's not a full print rendering engine. Complex print layouts or JavaScript-driven style changes might not be perfectly represented.  
* It focuses on display: none for hidden elements and general style changes for altered elements based on parsed CSS rules.  
* The highlighting is temporary and will disappear if you navigate away from the page or refresh it.

## **🤝 Contributing**

Feel free to suggest improvements or report issues\! This bookmarklet is a useful tool, and contributions are welcome.


## 📄 Learn More

- [How does print CSS work? (MDN)](https://developer.mozilla.org/en-US/docs/Web/CSS/@media/print)
- [h123 Bookmarklet Inspiration](https://hinderlingvolkart.github.io/h123/)
- https://chriszarate.github.io/bookmarkleter
- https://printedcss.com/
- https://coderscratchpad.com/css-creating-print-friendly-styles-with-css/
- https://blog.devgenius.io/printing-with-style-using-css-for-printer-optimization-643f270eb102
- https://www.terrific.tools/code/js-minify

**How to use this README on GitHub:**

1. Create a new repository on GitHub (e.g., print-highlighter-bookmarklet).  
2. In the repository, create a new file named README.md.  
3. Copy and paste the entire content above into your README.md file.  
4. Commit the changes.

Now, when someone visits your GitHub repository, they'll see this README, and they can easily drag the "Print Highlighter" link to their bookmarks bar!


<p style="font-size:0.95em;color:#666;">Tip: Use your browser's <b>Print Preview</b> to see the effect of these styles.</p>
