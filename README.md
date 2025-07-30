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

<a href="javascript:(function(){!function(){const n="print-media-highlight-style",e="print-media-highlight-toggle-button",t="print-media-highlight-legend",i="print-media-highlight-print-only",o="print-media-highlight-hidden-print",l="print-media-highlight-css-change",d="print-media-highlight-general";function r(){document.querySelectorAll(`.${d}, .${i}, .${o}, .${l}`).forEach((function(n){n.classList.remove(d,i,o,l)}))}function s(){r();const n=new Map,e=new Set;function t(i){try{i.cssRules&&Array.from(i.cssRules).forEach((function(i){i.type===CSSRule.MEDIA_RULE&&i.media.mediaText.includes("print")?Array.from(i.cssRules).forEach((function(t){t.selectorText&&(n.has(t.selectorText)||n.set(t.selectorText,[]),n.get(t.selectorText).push(t),e.add(t.selectorText))})):i.type===CSSRule.IMPORT_RULE&&t(i.styleSheet)}))}catch(n){}}Array.from(document.styleSheets).forEach((function(n){t(n)})),document.querySelectorAll("*").forEach((function(e){const t=window.getComputedStyle(e),r=t.getPropertyValue("display");let s=!1,a=!1,c=!1;if(n.size>0)for(const l of n.keys())try{if(e.matches(l)){s=!0;const d=n.get(l),p=d.find((n=>n.style&&n.style.display));if(p){const n=p.style.display;"none"===r&&"none"!==n?(e.classList.add(i),a=!0):"none"!==r&&"none"===n&&(e.classList.add(o),a=!0)}for(const n of d){if(n.style)for(let e=0;e<n.style.length;e++){const i=n.style[e],o=n.style.getPropertyValue(i),l=t.getPropertyValue(i);if("display"!==i&&o!==l){c=!0;break}}if(c)break}}}catch(n){}!s||a||c||e.classList.add(d),c&&e.classList.add(l)}))}!function(){if(document.getElementById(n))return;const r=document.createElement("style");r.id=n,r.textContent=`\n            .${d} {\n                outline: 3px solid red !important;\n                box-shadow: 0 0 0 2px #fff, 0 0 8px 2px #f00 !important;\n            }\n            .${i} {\n                outline: 3px solid limegreen !important; /* Green for print-only content */\n                box-shadow: 0 0 0 2px #fff, 0 0 8px 2px limegreen !important;\n            }\n            .${o} {\n                outline: 3px solid dodgerblue !important; /* Blue for hidden-in-print content */\n                box-shadow: 0 0 0 2px #fff, 0 0 8px 2px dodgerblue !important;\n            }\n            .${l} {\n                outline: 3px solid darkviolet !important; /* Purple for CSS changes */\n                box-shadow: 0 0 0 2px #fff, 0 0 8px 2px darkviolet !important;\n            }\n            #${e} {\n                position: fixed;\n                top: 10px;\n                right: 10px;\n                z-index: 99999;\n                background-color: #333;\n                color: white;\n                border: none;\n                padding: 8px 12px;\n                border-radius: 4px;\n                cursor: pointer;\n                font-family: sans-serif;\n                font-size: 14px;\n                opacity: 0.8;\n                transition: opacity 0.3s;\n            }\n            #${e}:hover {\n                opacity: 1;\n            }\n            #${t} {\n                position: fixed;\n                top: 50px; /* Adjust based on button height */\n                right: 10px;\n                z-index: 99999;\n                background-color: #f9f9f9;\n                border: 1px solid #ccc;\n                padding: 10px;\n                border-radius: 4px;\n                font-family: sans-serif;\n                font-size: 12px;\n                line-height: 1.5;\n                box-shadow: 0 2px 5px rgba(0,0,0,0.2);\n            }\n            #${t} p {\n                margin: 0;\n            }\n            #${t} .legend-item {\n                display: flex;\n                align-items: center;\n                margin-bottom: 5px;\n            }\n            #${t} .legend-color-box {\n                width: 15px;\n                height: 15px;\n                margin-right: 8px;\n                border: 1px solid #aaa;\n            }\n        `,document.head.appendChild(r)}(),function(){let n=document.getElementById(e);n||(n=document.createElement("button"),n.id=e,n.textContent="Toggle Print Media Highlights",document.body.appendChild(n));let i=document.getElementById(t);i||(i=document.createElement("div"),i.id=t,i.innerHTML='\n                <div class="legend-item"><div class="legend-color-box" style="background-color: limegreen;"></div><p>Visible only in Print</p></div>\n                <div class="legend-item"><div class="legend-color-box" style="background-color: dodgerblue;"></div><p>Hidden in Print</p></div>\n                <div class="legend-item"><div class="legend-color-box" style="background-color: darkviolet;"></div><p>CSS Change in Print</p></div>\n                <div class="legend-item"><div class="legend-color-box" style="background-color: red;"></div><p>General Print Style</p></div>\n            ',document.body.appendChild(i)),i.style.display="none";let o=!1;n.onclick=function(){o?(r(),n.textContent="Toggle Print Media Highlights (Off)",i.style.display="none"):(s(),n.textContent="Toggle Print Media Highlights (On)",i.style.display="block"),o=!o}}(),r(),document.getElementById(e).textContent="Toggle Print Media Highlights (Off)";const a=document.getElementById(t);a&&(a.style.display="none")}();}());" title="Drag this to your bookmarks bar!">Print Highlighter</a>

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
javascript:(function(){!function(){const n="print-media-highlight-style",e="print-media-highlight-toggle-button",t="print-media-highlight-legend",i="print-media-highlight-print-only",o="print-media-highlight-hidden-print",l="print-media-highlight-css-change",d="print-media-highlight-general";function r(){document.querySelectorAll(`.${d}, .${i}, .${o}, .${l}`).forEach((function(n){n.classList.remove(d,i,o,l)}))}function s(){r();const n=new Map,e=new Set;function t(i){try{i.cssRules&&Array.from(i.cssRules).forEach((function(i){i.type===CSSRule.MEDIA_RULE&&i.media.mediaText.includes("print")?Array.from(i.cssRules).forEach((function(t){t.selectorText&&(n.has(t.selectorText)||n.set(t.selectorText,[]),n.get(t.selectorText).push(t),e.add(t.selectorText))})):i.type===CSSRule.IMPORT_RULE&&t(i.styleSheet)}))}catch(n){}}Array.from(document.styleSheets).forEach((function(n){t(n)})),document.querySelectorAll("*").forEach((function(e){const t=window.getComputedStyle(e),r=t.getPropertyValue("display");let s=!1,a=!1,c=!1;if(n.size>0)for(const l of n.keys())try{if(e.matches(l)){s=!0;const d=n.get(l),p=d.find((n=>n.style&&n.style.display));if(p){const n=p.style.display;"none"===r&&"none"!==n?(e.classList.add(i),a=!0):"none"!==r&&"none"===n&&(e.classList.add(o),a=!0)}for(const n of d){if(n.style)for(let e=0;e<n.style.length;e++){const i=n.style[e],o=n.style.getPropertyValue(i),l=t.getPropertyValue(i);if("display"!==i&&o!==l){c=!0;break}}if(c)break}}}catch(n){}!s||a||c||e.classList.add(d),c&&e.classList.add(l)}))}!function(){if(document.getElementById(n))return;const r=document.createElement("style");r.id=n,r.textContent=`\n            .${d} {\n                outline: 3px solid red !important;\n                box-shadow: 0 0 0 2px #fff, 0 0 8px 2px #f00 !important;\n            }\n            .${i} {\n                outline: 3px solid limegreen !important; /* Green for print-only content */\n                box-shadow: 0 0 0 2px #fff, 0 0 8px 2px limegreen !important;\n            }\n            .${o} {\n                outline: 3px solid dodgerblue !important; /* Blue for hidden-in-print content */\n                box-shadow: 0 0 0 2px #fff, 0 0 8px 2px dodgerblue !important;\n            }\n            .${l} {\n                outline: 3px solid darkviolet !important; /* Purple for CSS changes */\n                box-shadow: 0 0 0 2px #fff, 0 0 8px 2px darkviolet !important;\n            }\n            #${e} {\n                position: fixed;\n                top: 10px;\n                right: 10px;\n                z-index: 99999;\n                background-color: #333;\n                color: white;\n                border: none;\n                padding: 8px 12px;\n                border-radius: 4px;\n                cursor: pointer;\n                font-family: sans-serif;\n                font-size: 14px;\n                opacity: 0.8;\n                transition: opacity 0.3s;\n            }\n            #${e}:hover {\n                opacity: 1;\n            }\n            #${t} {\n                position: fixed;\n                top: 50px; /* Adjust based on button height */\n                right: 10px;\n                z-index: 99999;\n                background-color: #f9f9f9;\n                border: 1px solid #ccc;\n                padding: 10px;\n                border-radius: 4px;\n                font-family: sans-serif;\n                font-size: 12px;\n                line-height: 1.5;\n                box-shadow: 0 2px 5px rgba(0,0,0,0.2);\n            }\n            #${t} p {\n                margin: 0;\n            }\n            #${t} .legend-item {\n                display: flex;\n                align-items: center;\n                margin-bottom: 5px;\n            }\n            #${t} .legend-color-box {\n                width: 15px;\n                height: 15px;\n                margin-right: 8px;\n                border: 1px solid #aaa;\n            }\n        `,document.head.appendChild(r)}(),function(){let n=document.getElementById(e);n||(n=document.createElement("button"),n.id=e,n.textContent="Toggle Print Media Highlights",document.body.appendChild(n));let i=document.getElementById(t);i||(i=document.createElement("div"),i.id=t,i.innerHTML='\n                <div class="legend-item"><div class="legend-color-box" style="background-color: limegreen;"></div><p>Visible only in Print</p></div>\n                <div class="legend-item"><div class="legend-color-box" style="background-color: dodgerblue;"></div><p>Hidden in Print</p></div>\n                <div class="legend-item"><div class="legend-color-box" style="background-color: darkviolet;"></div><p>CSS Change in Print</p></div>\n                <div class="legend-item"><div class="legend-color-box" style="background-color: red;"></div><p>General Print Style</p></div>\n            ',document.body.appendChild(i)),i.style.display="none";let o=!1;n.onclick=function(){o?(r(),n.textContent="Toggle Print Media Highlights (Off)",i.style.display="none"):(s(),n.textContent="Toggle Print Media Highlights (On)",i.style.display="block"),o=!o}}(),r(),document.getElementById(e).textContent="Toggle Print Media Highlights (Off)";const a=document.getElementById(t);a&&(a.style.display="none")}();}());
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
- https://make-bookmarklets.com
- https://chriszarate.github.io/bookmarkleter
- https://printedcss.com/
- https://coderscratchpad.com/css-creating-print-friendly-styles-with-css/
- https://blog.devgenius.io/printing-with-style-using-css-for-printer-optimization-643f270eb102

**How to use this README on GitHub:**

1. Create a new repository on GitHub (e.g., print-highlighter-bookmarklet).  
2. In the repository, create a new file named README.md.  
3. Copy and paste the entire content above into your README.md file.  
4. Commit the changes.

Now, when someone visits your GitHub repository, they'll see this README, and they can easily drag the "Print Highlighter" link to their bookmarks bar!


<p style="font-size:0.95em;color:#666;">Tip: Use your browser's <b>Print Preview</b> to see the effect of these styles.</p>
