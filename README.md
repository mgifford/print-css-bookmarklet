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

<a href="javascript:(function(){const n="print-media-highlight-style",a="print-media-highlight-toggle-button",e="print-media-highlight-legend",i="print-media-highlight-print-only",l="print-media-highlight-hidden-print",t="print-media-highlight-css-change",o="print-media-highlight-general";function s(){if(document.getElementById(n))return;const s=document.createElement("style");s.id=n,s.textContent="."+o+"{outline:3px solid red !important;box-shadow:0 0 0 2px #fff,0 0 8px 2px #f00 !important;}."+i+"{outline:3px solid limegreen !important;box-shadow:0 0 0 2px #fff,0 0 8px 2px limegreen !important;}."+l+"{outline:3px solid dodgerblue !important;box-shadow:0 0 0 2px #fff,0 0 8px 2px dodgerblue !important;}."+t+"{outline:3px solid darkviolet !important;box-shadow:0 0 0 2px #fff,0 0 8px 2px darkviolet !important;}#"+a+"{position:fixed;top:10px;right:10px;z-index:99999;background-color:#333;color:white;border:none;padding:8px 12px;border-radius:4px;cursor:pointer;font-family:sans-serif;font-size:14px;opacity:0.8;transition:opacity 0.3s;}#"+a+":hover{opacity:1;}#"+e+"{position:fixed;top:50px;right:10px;z-index:99999;background-color:#f9f9f9;border:1px solid #ccc;padding:10px;border-radius:4px;font-family:sans-serif;font-size:12px;line-height:1.5;box-shadow:0 2px 5px rgba(0,0,0,0.2);}#"+e+" p{margin:0;}#"+e+" .legend-item{display:flex;align-items:center;margin-bottom:5px;}#"+e+" .legend-color-box{width:15px;height:15px;margin-right:8px;border:1px solid #aaa;}",document.head.appendChild(s)}function d(){document.querySelectorAll("."+o+",."+i+",."+l+",."+t).forEach(function(n){n.classList.remove(o,i,l,t)})}function c(){d();const n=new Map;function a(e){try{e.cssRules&&Array.from(e.cssRules).forEach(function(e){e.type===CSSRule.MEDIA_RULE&&e.media.mediaText.includes("print")?Array.from(e.cssRules).forEach(function(e){e.selectorText&&(n.has(e.selectorText)||n.set(e.selectorText,[]),n.get(e.selectorText).push(e))}):e.type===CSSRule.IMPORT_RULE&&a(e.styleSheet)})}catch(n){}}Array.from(document.styleSheets).forEach(function(n){a(n)}),document.querySelectorAll("*").forEach(function(a){const e=window.getComputedStyle(a),o=e.getPropertyValue("display");let s=!1,i=!1,l=!1;if(0!==n.size)for(const t of n.keys())try{if(a.matches(t)){s=!0;const p=n.get(t),r=p.find(n=>n.style&&n.style.display);if(r){const n=r.style.display;"none"===o&&"none"!==n?(a.classList.add("print-media-highlight-print-only"),i=!0):"none"!==o&&"none"===n&&(a.classList.add("print-media-highlight-hidden-print"),i=!0)}for(const n of p){if(n.style)for(let t=0;t<n.style.length;t++){const o=n.style[t],s=n.style.getPropertyValue(o),d=e.getPropertyValue(o);if("display"!==o&&s!==d){l=!0;break}}if(l)break}}}catch(n){}s&&!i&&!l&&a.classList.add("print-media-highlight-general"),l&&a.classList.add("print-media-highlight-css-change")})}function h(){let n=document.getElementById(a);n||(n=document.createElement("button"),n.id=a,n.textContent="Toggle Print Media Highlights",document.body.appendChild(n));let i=document.getElementById(e);i||(i=document.createElement("div"),i.id=e,i.innerHTML='<div class="legend-item"><div class="legend-color-box" style="background-color:limegreen;"></div><p>Visible only in Print</p></div><div class="legend-item"><div class="legend-color-box" style="background-color:dodgerblue;"></div><p>Hidden in Print</p></div><div class="legend-item"><div class="legend-color-box" style="background-color:darkviolet;"></div><p>CSS Change in Print</p></div><div class="legend-item"><div class="legend-color-box" style="background-color:red;"></div><p>General Print Style</p></div>',document.body.appendChild(i)),i.style.display="none";let l=!1;n.onclick=function(){l?(d(),n.textContent="Toggle Print Media Highlights (Off)",i.style.display="none"):(c(),n.textContent="Toggle Print Media Highlights (On)",i.style.display="block"),l=!l}}s(),h(),d(),document.getElementById(a).textContent="Toggle Print Media Highlights (Off)";const p=document.getElementById(e);p&&p.style.display==="block"&& (p.style.display="none");})();">Print Highlighter</a>

## 🖨️ Live Print CSS Demo

    <style>
        body {
            font-family: Arial, sans-serif;
            margin: 20px;
            background-color: #f4f4f4;
            color: #333;
        }

        h1 {
            color: #0056b3;
        }

        .demo-section {
            background-color: #fff;
            padding: 20px;
            margin-bottom: 15px;
            border-radius: 8px;
            box-shadow: 0 2px 5px rgba(0,0,0,0.1);
        }

        /* --- Print CSS Demo Styles --- */
        .no-print-demo {
            color: #b00; /* Red color */
            font-weight: bold;
            border: 2px dashed #b00;
            padding: 10px;
            margin-bottom: 10px;
        }

        .print-different-demo {
            color: #333; /* Dark gray */
            font-size: 1.2em;
            text-decoration: underline;
            border: 2px solid #666;
            padding: 10px;
            margin-bottom: 10px;
        }

        .print-only-demo {
            display: none; /* Hidden by default */
            background-color: #e6ffe6; /* Light green background */
            padding: 10px;
            margin-bottom: 10px;
            border: 2px solid limegreen;
        }

        .general-print-style-demo {
            padding: 15px;
            margin-bottom: 10px;
            background-color: #f0f8ff; /* AliceBlue */
            border: 1px solid #ccc;
        }

        /* --- Print Media Query --- */
        @media print {
            body {
                background-color: #fff !important; /* Ensure white background for print */
                color: #000 !important;
            }

            .demo-section {
                box-shadow: none; /* No shadows in print */
                border: 1px solid #eee;
            }

            .no-print-demo {
                display: none !important; /* This will be HIDDEN IN PRINT (blue highlight) */
            }

            .print-different-demo {
                color: #007700 !important; /* Changes to dark green */
                font-size: 2em !important; /* Becomes larger */
                font-weight: bold !important;
                text-decoration: none !important; /* Underline removed */
                border-color: #007700 !important; /* Border color changes */
            }

            .print-only-demo {
                display: block !important; /* This will be VISIBLE ONLY IN PRINT (green highlight) */
                color: #b00 !important; /* Red color in print */
                font-style: italic !important;
                font-size: 1.5em !important;
                background-color: #fff !important; /* Background removed for print */
                border-color: #b00 !important; /* Border color changes */
            }

            .general-print-style-demo {
                padding: 5px !important; /* Smaller padding in print */
                background-color: #f0f0f0 !important; /* Lighter background in print */
                border: 2px solid orange !important; /* New border style */
            }

            /* Example of a general rule affecting elements not explicitly called out */
            p {
                margin-bottom: 5px !important;
                font-size: 0.9em !important;
            }
        }
    </style>


    <div class="demo-section">
        <h2>Hidden in Print</h2>
        <div class="no-print-demo">
            This element has `display: none` in `@media print`. It will be highlighted with a **blue border**.
            In normal view, it's red and bold.
        </div>
        <p>This is a regular paragraph that might change its font size in print due to a general `p` rule.</p>
    </div>

    <div class="demo-section">
        <h2>CSS Changes in Print</h2>
        <div class="print-different-demo">
            This element has several CSS properties that change in `@media print` (color, font-size, text-decoration, border). It will be highlighted with a **purple border**.
            In normal view, it's dark gray and underlined.
        </div>
    </div>

    <div class="demo-section">
        <h2>Visible Only in Print</h2>
        <div class="print-only-demo">
            This element has `display: none` by default, but `display: block` in `@media print`. It will be highlighted with a **limegreen border**.
            You should only see this text when you activate the print highlights.
        </div>
    </div>

    <div class="demo-section">
        <h2>General Print Style</h2>
        <div class="general-print-style-demo">
            This element has some of its general styles (like padding, background, border) changed in the print stylesheet, but no display changes or very prominent CSS changes that triggered other categories. It will be highlighted with a **red border**.
        </div>
    </div>



<div class="no-print-demo">This message will NOT appear when you print this page.</div>
<div class="print-different-demo">This text changes color and size when printed.</div>
<div class="print-only-demo">This message ONLY appears in print view.</div>

   * **Tip for Mobile/Manual Install:** If the drag-and-drop doesn't work (e.g., on some mobile browsers or if you prefer manual setup), follow these steps:  
     1. Create a new bookmark in your browser.  
     2. Name it "Print Highlighter" (or anything you like).  
     3. For the URL/Location, copy the *entire* JavaScript code from the javascript: prefix below and paste it into the URL field:  
        
```
javascript:(function(){const n="print-media-highlight-style",a="print-media-highlight-toggle-button",e="print-media-highlight-legend",i="print-media-highlight-print-only",l="print-media-highlight-hidden-print",t="print-media-highlight-css-change",o="print-media-highlight-general";function s(){if(document.getElementById(n))return;const s=document.createElement("style");s.id=n,s.textContent="."+o+"{outline:3px solid red !important;box-shadow:0 0 0 2px #fff,0 0 8px 2px #f00 !important;}."+i+"{outline:3px solid limegreen !important;box-shadow:0 0 0 2px #fff,0 0 8px 2px limegreen !important;}."+l+"{outline:3px solid dodgerblue !important;box-shadow:0 0 0 2px #fff,0 0 8px 2px dodgerblue !important;}."+t+"{outline:3px solid darkviolet !important;box-shadow:0 0 0 2px #fff,0 0 8px 2px darkviolet !important;}#"+a+"{position:fixed;top:10px;right:10px;z-index:99999;background-color:#333;color:white;border:none;padding:8px 12px;border-radius:4px;cursor:pointer;font-family:sans-serif;font-size:14px;opacity:0.8;transition:opacity 0.3s;}#"+a+":hover{opacity:1;}#"+e+"{position:fixed;top:50px;right:10px;z-index:99999;background-color:#f9f9f9;border:1px solid #ccc;padding:10px;border-radius:4px;font-family:sans-serif;font-size:12px;line-height:1.5;box-shadow:0 2px 5px rgba(0,0,0,0.2);}#"+e+" p{margin:0;}#"+e+" .legend-item{display:flex;align-items:center;margin-bottom:5px;}#"+e+" .legend-color-box{width:15px;height:15px;margin-right:8px;border:1px solid #aaa;}",document.head.appendChild(s)}function d(){document.querySelectorAll("."+o+",."+i+",."+l+",."+t).forEach(function(n){n.classList.remove(o,i,l,t)})}function c(){d();const n=new Map;function a(e){try{e.cssRules&&Array.from(e.cssRules).forEach(function(e){e.type===CSSRule.MEDIA_RULE&&e.media.mediaText.includes("print")?Array.from(e.cssRules).forEach(function(e){e.selectorText&&(n.has(e.selectorText)||n.set(e.selectorText,[]),n.get(e.selectorText).push(e))}):e.type===CSSRule.IMPORT_RULE&&a(e.styleSheet)})}catch(n){}}Array.from(document.styleSheets).forEach(function(n){a(n)}),document.querySelectorAll("*").forEach(function(a){const e=window.getComputedStyle(a),o=e.getPropertyValue("display");let s=!1,i=!1,l=!1;if(0!==n.size)for(const t of n.keys())try{if(a.matches(t)){s=!0;const p=n.get(t),r=p.find(n=>n.style&&n.style.display);if(r){const n=r.style.display;"none"===o&&"none"!==n?(a.classList.add("print-media-highlight-print-only"),i=!0):"none"!==o&&"none"===n&&(a.classList.add("print-media-highlight-hidden-print"),i=!0)}for(const n of p){if(n.style)for(let t=0;t<n.style.length;t++){const o=n.style[t],s=n.style.getPropertyValue(o),d=e.getPropertyValue(o);if("display"!==o&&s!==d){l=!0;break}}if(l)break}}}catch(n){}s&&!i&&!l&&a.classList.add("print-media-highlight-general"),l&&a.classList.add("print-media-highlight-css-change")})}function h(){let n=document.getElementById(a);n||(n=document.createElement("button"),n.id=a,n.textContent="Toggle Print Media Highlights",document.body.appendChild(n));let i=document.getElementById(e);i||(i=document.createElement("div"),i.id=e,i.innerHTML='<div class="legend-item"><div class="legend-color-box" style="background-color:limegreen;"></div><p>Visible only in Print</p></div><div class="legend-item"><div class="legend-color-box" style="background-color:dodgerblue;"></div><p>Hidden in Print</p></div><div class="legend-item"><div class="legend-color-box" style="background-color:darkviolet;"></div><p>CSS Change in Print</p></div><div class="legend-item"><div class="legend-color-box" style="background-color:red;"></div><p>General Print Style</p></div>',document.body.appendChild(i)),i.style.display="none";let l=!1;n.onclick=function(){l?(d(),n.textContent="Toggle Print Media Highlights (Off)",i.style.display="none"):(c(),n.textContent="Toggle Print Media Highlights (On)",i.style.display="block"),l=!l}}s(),h(),d(),document.getElementById(a).textContent="Toggle Print Media Highlights (Off)";const p=document.getElementById(e);p&&p.style.display==="block"&& (p.style.display="none");})();
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
- [https://chriszarate.github.io/bookmarkleter](https://chriszarate.github.io/bookmarkleter)
- [https://printedcss.com/](https://printedcss.com/)
- [https://coderscratchpad.com/css-creating-print-friendly-styles-with-css/](https://coderscratchpad.com/css-creating-print-friendly-styles-with-css/)
- [https://blog.devgenius.io/printing-with-style-using-css-for-printer-optimization-643f270eb102](https://blog.devgenius.io/printing-with-style-using-css-for-printer-optimization-643f270eb102)
- [https://www.terrific.tools/code/js-minify](https://www.terrific.tools/code/js-minify)

**How to use this README on GitHub:**

1. Create a new repository on GitHub (e.g., print-highlighter-bookmarklet).  
2. In the repository, create a new file named README.md.  
3. Copy and paste the entire content above into your README.md file.  
4. Commit the changes.

Now, when someone visits your GitHub repository, they'll see this README, and they can easily drag the "Print Highlighter" link to their bookmarks bar!


<p style="font-size:0.95em;color:#666;">Tip: Use your browser's <b>Print Preview</b> to see the effect of these styles.</p>
