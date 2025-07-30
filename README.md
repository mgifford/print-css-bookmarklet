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

<a href="javascript:void%20function(){javascript:(function(){function%20b(){document.querySelectorAll(%22.print-media-highlight-general,.print-media-highlight-print-only,.print-media-highlight-hidden-print,.print-media-highlight-css-change%22).forEach(function(a){a.classList.remove(i,e,g,h)})}function%20d(){function%20c(a){try{a.cssRules%26%26Array.from(a.cssRules).forEach(function(a){a.type===CSSRule.MEDIA_RULE%26%26a.media.mediaText.includes(%22print%22)%3FArray.from(a.cssRules).forEach(function(a){a.selectorText%26%26(f.has(a.selectorText)||f.set(a.selectorText,[]),f.get(a.selectorText).push(a))}):a.type===CSSRule.IMPORT_RULE%26%26c(a.styleSheet)})}catch(a){}}b();const%20f=new%20Map;Array.from(document.styleSheets).forEach(function(a){c(a)}),document.querySelectorAll(%22*%22).forEach(function(b){const%20a=window.getComputedStyle(b),i=a.getPropertyValue(%22display%22);let%20j=!1,k=!1,l=!1;if(0!==f.size)for(const%20c%20of%20f.keys())try{if(b.matches(c)){j=!0;const%20d=f.get(c),h=d.find(a=%3Ea.style%26%26a.style.display);if(h){const%20a=h.style.display;%22none%22===i%26%26%22none%22!==a%3F(b.classList.add(e),k=!0):%22none%22!==i%26%26%22none%22===a%26%26(b.classList.add(g),k=!0)}for(const%20b%20of%20d){if(b.style)for(let%20c=0;c%3Cb.style.length;c++){const%20d=b.style[c],e=b.style.getPropertyValue(d),f=a.getPropertyValue(d);if(%22display%22!==d%26%26e!==f){l=!0;break}}if(l)break}}}catch(a){}!j||k||l||b.classList.add(i),l%26%26b.classList.add(h)})}const%20c=%22print-media-highlight-style%22,f=%22print-media-highlight-toggle-button%22,a=%22print-media-highlight-legend%22,e=%22print-media-highlight-print-only%22,g=%22print-media-highlight-hidden-print%22,h=%22print-media-highlight-css-change%22,i=%22print-media-highlight-general%22;(function(){if(!document.getElementById(c)){const%20b=document.createElement(%22style%22);b.id=c,b.textContent=%22.print-media-highlight-general{outline:3px%20solid%20red%20!important;box-shadow:0%200%200%202px%20%23fff,0%200%208px%202px%20%23f00%20!important;}.print-media-highlight-print-only{outline:3px%20solid%20limegreen%20!important;box-shadow:0%200%200%202px%20%23fff,0%200%208px%202px%20limegreen%20!important;}.print-media-highlight-hidden-print{outline:3px%20solid%20dodgerblue%20!important;box-shadow:0%200%200%202px%20%23fff,0%200%208px%202px%20dodgerblue%20!important;}.print-media-highlight-css-change{outline:3px%20solid%20darkviolet%20!important;box-shadow:0%200%200%202px%20%23fff,0%200%208px%202px%20darkviolet%20!important;}%23%22+buttonId+%22{position:fixed;top:10px;right:10px;z-index:99999;background-color:%23333;color:white;border:none;padding:8px%2012px;border-radius:4px;cursor:pointer;font-family:sans-serif;font-size:14px;opacity:0.8;transition:opacity%200.3s;}%23%22+buttonId+%22:hover{opacity:1;}%23%22+legendId+%22{position:fixed;top:50px;right:10px;z-index:99999;background-color:%23f9f9f9;border:1px%20solid%20%23ccc;padding:10px;border-radius:4px;font-family:sans-serif;font-size:12px;line-height:1.5;box-shadow:0%202px%205px%20rgba(0,0,0,0.2);}%23%22+legendId+%22%20p{margin:0;}%23%22+legendId+%22%20.legend-item{display:flex;align-items:center;margin-bottom:5px;}%23%22+legendId+%22%20.legend-color-box{width:15px;height:15px;margin-right:8px;border:1px%20solid%20%23aaa;}%22,document.head.appendChild(b)}})(),function(){let%20c=document.getElementById(f);c||(c=document.createElement(%22button%22),c.id=f,c.textContent=%22Toggle%20Print%20Media%20Highlights%22,document.body.appendChild(c));let%20e=document.getElementById(a);e||(e=document.createElement(%22div%22),e.id=a,e.innerHTML=%22%3Cdiv%20class=\%22legend-item\%22%3E%3Cdiv%20class=\%22legend-color-box\%22%20style=\%22background-color:limegreen;\%22%3E%3C/div%3E%3Cp%3EVisible%20only%20in%20Print%3C/p%3E%3C/div%3E%3Cdiv%20class=\%22legend-item\%22%3E%3Cdiv%20class=\%22legend-color-box\%22%20style=\%22background-color:dodgerblue;\%22%3E%3C/div%3E%3Cp%3EHidden%20in%20Print%3C/p%3E%3C/div%3E%3Cdiv%20class=\%22legend-item\%22%3E%3Cdiv%20class=\%22legend-color-box\%22%20style=\%22background-color:darkviolet;\%22%3E%3C/div%3E%3Cp%3ECSS%20Change%20in%20Print%3C/p%3E%3C/div%3E%3Cdiv%20class=\%22legend-item\%22%3E%3Cdiv%20class=\%22legend-color-box\%22%20style=\%22background-color:red;\%22%3E%3C/div%3E%3Cp%3EGeneral%20Print%20Style%3C/p%3E%3C/div%3E%22,document.body.appendChild(e)),e.style.display=%22none%22;let%20g=!1;c.onclick=function(){g%3F(b(),c.textContent=%22Toggle%20Print%20Media%20Highlights%20(Off)%22,e.style.display=%22none%22):(d(),c.textContent=%22Toggle%20Print%20Media%20Highlights%20(On)%22,e.style.display=%22block%22),g=!g}}(),b(),document.getElementById(%22print-media-highlight-toggle-button%22).textContent=%22Toggle%20Print%20Media%20Highlights%20(Off)%22;const%20j=document.getElementById(%22print-media-highlight-legend%22);j%26%26%22block%22===j.style.display%26%26(j.style.display=%22none%22)})()}();">Print Highlighter</a>

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
javascript:void%20function(){javascript:(function(){function%20b(){document.querySelectorAll(%22.print-media-highlight-general,.print-media-highlight-print-only,.print-media-highlight-hidden-print,.print-media-highlight-css-change%22).forEach(function(a){a.classList.remove(i,e,g,h)})}function%20d(){function%20c(a){try{a.cssRules%26%26Array.from(a.cssRules).forEach(function(a){a.type===CSSRule.MEDIA_RULE%26%26a.media.mediaText.includes(%22print%22)%3FArray.from(a.cssRules).forEach(function(a){a.selectorText%26%26(f.has(a.selectorText)||f.set(a.selectorText,[]),f.get(a.selectorText).push(a))}):a.type===CSSRule.IMPORT_RULE%26%26c(a.styleSheet)})}catch(a){}}b();const%20f=new%20Map;Array.from(document.styleSheets).forEach(function(a){c(a)}),document.querySelectorAll(%22*%22).forEach(function(b){const%20a=window.getComputedStyle(b),i=a.getPropertyValue(%22display%22);let%20j=!1,k=!1,l=!1;if(0!==f.size)for(const%20c%20of%20f.keys())try{if(b.matches(c)){j=!0;const%20d=f.get(c),h=d.find(a=%3Ea.style%26%26a.style.display);if(h){const%20a=h.style.display;%22none%22===i%26%26%22none%22!==a%3F(b.classList.add(e),k=!0):%22none%22!==i%26%26%22none%22===a%26%26(b.classList.add(g),k=!0)}for(const%20b%20of%20d){if(b.style)for(let%20c=0;c%3Cb.style.length;c++){const%20d=b.style[c],e=b.style.getPropertyValue(d),f=a.getPropertyValue(d);if(%22display%22!==d%26%26e!==f){l=!0;break}}if(l)break}}}catch(a){}!j||k||l||b.classList.add(i),l%26%26b.classList.add(h)})}const%20c=%22print-media-highlight-style%22,f=%22print-media-highlight-toggle-button%22,a=%22print-media-highlight-legend%22,e=%22print-media-highlight-print-only%22,g=%22print-media-highlight-hidden-print%22,h=%22print-media-highlight-css-change%22,i=%22print-media-highlight-general%22;(function(){if(!document.getElementById(c)){const%20b=document.createElement(%22style%22);b.id=c,b.textContent=%22.print-media-highlight-general{outline:3px%20solid%20red%20!important;box-shadow:0%200%200%202px%20%23fff,0%200%208px%202px%20%23f00%20!important;}.print-media-highlight-print-only{outline:3px%20solid%20limegreen%20!important;box-shadow:0%200%200%202px%20%23fff,0%200%208px%202px%20limegreen%20!important;}.print-media-highlight-hidden-print{outline:3px%20solid%20dodgerblue%20!important;box-shadow:0%200%200%202px%20%23fff,0%200%208px%202px%20dodgerblue%20!important;}.print-media-highlight-css-change{outline:3px%20solid%20darkviolet%20!important;box-shadow:0%200%200%202px%20%23fff,0%200%208px%202px%20darkviolet%20!important;}%23%22+buttonId+%22{position:fixed;top:10px;right:10px;z-index:99999;background-color:%23333;color:white;border:none;padding:8px%2012px;border-radius:4px;cursor:pointer;font-family:sans-serif;font-size:14px;opacity:0.8;transition:opacity%200.3s;}%23%22+buttonId+%22:hover{opacity:1;}%23%22+legendId+%22{position:fixed;top:50px;right:10px;z-index:99999;background-color:%23f9f9f9;border:1px%20solid%20%23ccc;padding:10px;border-radius:4px;font-family:sans-serif;font-size:12px;line-height:1.5;box-shadow:0%202px%205px%20rgba(0,0,0,0.2);}%23%22+legendId+%22%20p{margin:0;}%23%22+legendId+%22%20.legend-item{display:flex;align-items:center;margin-bottom:5px;}%23%22+legendId+%22%20.legend-color-box{width:15px;height:15px;margin-right:8px;border:1px%20solid%20%23aaa;}%22,document.head.appendChild(b)}})(),function(){let%20c=document.getElementById(f);c||(c=document.createElement(%22button%22),c.id=f,c.textContent=%22Toggle%20Print%20Media%20Highlights%22,document.body.appendChild(c));let%20e=document.getElementById(a);e||(e=document.createElement(%22div%22),e.id=a,e.innerHTML=%22%3Cdiv%20class=\%22legend-item\%22%3E%3Cdiv%20class=\%22legend-color-box\%22%20style=\%22background-color:limegreen;\%22%3E%3C/div%3E%3Cp%3EVisible%20only%20in%20Print%3C/p%3E%3C/div%3E%3Cdiv%20class=\%22legend-item\%22%3E%3Cdiv%20class=\%22legend-color-box\%22%20style=\%22background-color:dodgerblue;\%22%3E%3C/div%3E%3Cp%3EHidden%20in%20Print%3C/p%3E%3C/div%3E%3Cdiv%20class=\%22legend-item\%22%3E%3Cdiv%20class=\%22legend-color-box\%22%20style=\%22background-color:darkviolet;\%22%3E%3C/div%3E%3Cp%3ECSS%20Change%20in%20Print%3C/p%3E%3C/div%3E%3Cdiv%20class=\%22legend-item\%22%3E%3Cdiv%20class=\%22legend-color-box\%22%20style=\%22background-color:red;\%22%3E%3C/div%3E%3Cp%3EGeneral%20Print%20Style%3C/p%3E%3C/div%3E%22,document.body.appendChild(e)),e.style.display=%22none%22;let%20g=!1;c.onclick=function(){g%3F(b(),c.textContent=%22Toggle%20Print%20Media%20Highlights%20(Off)%22,e.style.display=%22none%22):(d(),c.textContent=%22Toggle%20Print%20Media%20Highlights%20(On)%22,e.style.display=%22block%22),g=!g}}(),b(),document.getElementById(%22print-media-highlight-toggle-button%22).textContent=%22Toggle%20Print%20Media%20Highlights%20(Off)%22;const%20j=document.getElementById(%22print-media-highlight-legend%22);j%26%26%22block%22===j.style.display%26%26(j.style.display=%22none%22)})()}();
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
