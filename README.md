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

<a href="javascript:(function(){const styleId='print-highlight-bookmarklet-style',buttonId='print-highlight-bookmarklet-toggle-button',hiddenClass='print-hidden-highlight',alteredClass='print-altered-highlight';function createHighlightStyles(){if(document.getElementById(styleId))return;const style=document.createElement('style');style.id=styleId;style.textContent='.'+hiddenClass+'{background-color:#f0f0f0 !important;border:1px dashed #999 !important;outline:2px dashed #999 !important;}.'+alteredClass+'{background-color:#fffacd !important;border:1px solid #da0 !important;outline:2px solid #da0 !important;}#'+buttonId+'{position:fixed;top:10px;right:10px;z-index:99999;background-color:#333;color:white;border:none;padding:8px 12px;border-radius:4px;cursor:pointer;font-family:sans-serif;font-size:14px;opacity:0.8;transition:opacity 0.3s;}#'+buttonId+':hover{opacity:1;}';document.head.appendChild(style);}function removeHighlightStyles(){const style=document.getElementById(styleId);if(style){style.remove();}}function removeHighlightClasses(){document.querySelectorAll('.'+hiddenClass+',.'+alteredClass).forEach(function(el){el.classList.remove(hiddenClass,alteredClass);});}function applyHighlighting(){const printRules=[];function extractRules(sheet){try{if(sheet.cssRules){Array.from(sheet.cssRules).forEach(function(rule){if(rule.type===CSSRule.MEDIA_RULE&&rule.media.mediaText.includes('print')){Array.from(rule.cssRules).forEach(function(printRule){printRules.push(printRule);});}else if(rule.type===CSSRule.STYLE_RULE){if(sheet.media&&sheet.media.mediaText.includes('print')){printRules.push(rule);}}else if(rule.type===CSSRule.IMPORT_RULE){extractRules(rule.styleSheet);}});}}catch(e){console.warn('Could not read stylesheet:',sheet.href||'inline style',e);}}Array.from(document.styleSheets).forEach(function(sheet){extractRules(sheet);});printRules.forEach(function(rule){if(rule.selectorText){try{document.querySelectorAll(rule.selectorText).forEach(function(el){if(rule.style.display==='none'){el.classList.add(hiddenClass);}else{if(Object.keys(rule.style).length>0){el.classList.add(alteredClass);}}});}catch(e){console.warn('Invalid selector:',rule.selectorText,e);}}});const commonHiddenSelectors=['nav','.navbar','#header','#footer','.sidebar','.menu','.ad','.ads','.no-print','[data-print=hidden]'];commonHiddenSelectors.forEach(function(selector){try{document.querySelectorAll(selector).forEach(function(el){if(!el.classList.contains(hiddenClass)&&getComputedStyle(el).display==='none'){el.classList.add(hiddenClass);}});}catch(e){console.warn('Invalid common hidden selector:',selector,e);}});}function setupToggleButton(){let button=document.getElementById(buttonId);if(!button){button=document.createElement('button');button.id=buttonId;button.textContent='Toggle Print Highlights';document.body.appendChild(button);let isActive=false;button.onclick=function(){if(isActive){removeHighlightClasses();button.textContent='Toggle Print Highlights (Off)';}else{applyHighlighting();button.textContent='Toggle Print Highlights (On)';}isActive=!isActive;};}}createHighlightStyles();setupToggleButton();removeHighlightClasses();document.getElementById(buttonId).textContent='Toggle Print Highlights (Off)';})();" title="Drag this to your bookmarks bar!">Print Highlighter</a>


   * **Tip for Mobile/Manual Install:** If the drag-and-drop doesn't work (e.g., on some mobile browsers or if you prefer manual setup), follow these steps:  
     1. Create a new bookmark in your browser.  
     2. Name it "Print Highlighter" (or anything you like).  
     3. For the URL/Location, copy the *entire* JavaScript code from the javascript: prefix below and paste it into the URL field:  
        
```
javascript:(function(){const styleId='print-highlight-bookmarklet-style',buttonId='print-highlight-bookmarklet-toggle-button',hiddenClass='print-hidden-highlight',alteredClass='print-altered-highlight';function createHighlightStyles(){if(document.getElementById(styleId))return;const style=document.createElement('style');style.id=styleId;style.textContent='.'+hiddenClass+'{background-color:#f0f0f0 !important;border:1px dashed #999 !important;outline:2px dashed #999 !important;}.'+alteredClass+'{background-color:#fffacd !important;border:1px solid #da0 !important;outline:2px solid #da0 !important;}#'+buttonId+'{position:fixed;top:10px;right:10px;z-index:99999;background-color:#333;color:white;border:none;padding:8px 12px;border-radius:4px;cursor:pointer;font-family:sans-serif;font-size:14px;opacity:0.8;transition:opacity 0.3s;}#'+buttonId+':hover{opacity:1;}';document.head.appendChild(style);}function removeHighlightStyles(){const style=document.getElementById(styleId);if(style){style.remove();}}function removeHighlightClasses(){document.querySelectorAll('.'+hiddenClass+',.'+alteredClass).forEach(function(el){el.classList.remove(hiddenClass,alteredClass);});}function applyHighlighting(){const printRules=[];function extractRules(sheet){try{if(sheet.cssRules){Array.from(sheet.cssRules).forEach(function(rule){if(rule.type===CSSRule.MEDIA_RULE&&rule.media.mediaText.includes('print')){Array.from(rule.cssRules).forEach(function(printRule){printRules.push(printRule);});}else if(rule.type===CSSRule.STYLE_RULE){if(sheet.media&&sheet.media.mediaText.includes('print')){printRules.push(rule);}}else if(rule.type===CSSRule.IMPORT_RULE){extractRules(rule.styleSheet);}});}}catch(e){console.warn('Could not read stylesheet:',sheet.href||'inline style',e);}}Array.from(document.styleSheets).forEach(function(sheet){extractRules(sheet);});printRules.forEach(function(rule){if(rule.selectorText){try{document.querySelectorAll(rule.selectorText).forEach(function(el){if(rule.style.display==='none'){el.classList.add(hiddenClass);}else{if(Object.keys(rule.style).length>0){el.classList.add(alteredClass);}}});}catch(e){console.warn('Invalid selector:',rule.selectorText,e);}}});const commonHiddenSelectors=['nav','.navbar','#header','#footer','.sidebar','.menu','.ad','.ads','.no-print','[data-print=hidden]'];commonHiddenSelectors.forEach(function(selector){try{document.querySelectorAll(selector).forEach(function(el){if(!el.classList.contains(hiddenClass)&&getComputedStyle(el).display==='none'){el.classList.add(hiddenClass);}});}catch(e){console.warn('Invalid common hidden selector:',selector,e);}});}function setupToggleButton(){let button=document.getElementById(buttonId);if(!button){button=document.createElement('button');button.id=buttonId;button.textContent='Toggle Print Highlights';document.body.appendChild(button);let isActive=false;button.onclick=function(){if(isActive){removeHighlightClasses();button.textContent='Toggle Print Highlights (Off)';}else{applyHighlighting();button.textContent='Toggle Print Highlights (On)';}isActive=!isActive;};}}createHighlightStyles();setupToggleButton();removeHighlightClasses();document.getElementById(buttonId).textContent='Toggle Print Highlights (Off)';})();
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

<p style="font-size:0.95em;color:#666;">Tip: Use your browser's <b>Print Preview</b> to see the effect of these styles.</p>
