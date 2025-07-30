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

<a href="javascript:void%20function(){javascript:(function(){function%20a(){document.querySelectorAll(`.${i},.${f},.${g},.${h}`).forEach(function(a){a.classList.remove(i,f,g,h)})}function%20b(){function%20b(a){try{a.cssRules%26%26Array.from(a.cssRules).forEach(function(a){a.type===CSSRule.MEDIA_RULE%26%26a.media.mediaText.includes(%22print%22)%3FArray.from(a.cssRules).forEach(function(a){a.selectorText%26%26(!c.has(a.selectorText)%26%26c.set(a.selectorText,[]),c.get(a.selectorText).push(a),d.add(a.selectorText))}):a.type===CSSRule.IMPORT_RULE%26%26b(a.styleSheet)})}catch(a){}}a();const%20c=new%20Map,d=new%20Set;Array.from(document.styleSheets).forEach(function(a){b(a)}),document.querySelectorAll(%22*%22).forEach(function(a){const%20b=window.getComputedStyle(a),d=b.getPropertyValue(%22display%22);let%20e=!1,j=!1,k=!1;if(0%3Cc.size)for(const%20h%20of%20c.keys())try{if(a.matches(h)){e=!0;const%20i=c.get(h),l=i.find(a=%3Ea.style%26%26a.style.display);if(l){const%20b=l.style.display;%22none%22===d%26%26%22none%22!==b%3F(a.classList.add(f),j=!0):%22none%22!==d%26%26%22none%22===b%26%26(a.classList.add(g),j=!0)}for(const%20a%20of%20i){if(a.style)for(let%20c=0;c%3Ca.style.length;c++){const%20d=a.style[c],e=a.style.getPropertyValue(d),f=b.getPropertyValue(d);if(%22display%22!==d%26%26e!==f){k=!0;break}}if(k)break}}}catch(a){}!e||j||k||a.classList.add(i),k%26%26a.classList.add(h)})}const%20c=%22print-media-highlight-style%22,d=%22print-media-highlight-toggle-button%22,e=%22print-media-highlight-legend%22,f=%22print-media-highlight-print-only%22,g=%22print-media-highlight-hidden-print%22,h=%22print-media-highlight-css-change%22,i=%22print-media-highlight-general%22;(function(){if(!document.getElementById(c)){const%20a=document.createElement(%22style%22);a.id=c,a.textContent=`%20.${i}{outline:3px%20solid%20red%20!important;box-shadow:0%200%200%202px%20%23fff,0%200%208px%202px%20%23f00%20!important;}.${f}{outline:3px%20solid%20limegreen%20!important;box-shadow:0%200%200%202px%20%23fff,0%200%208px%202px%20limegreen%20!important;}.${g}{outline:3px%20solid%20dodgerblue%20!important;box-shadow:0%200%200%202px%20%23fff,0%200%208px%202px%20dodgerblue%20!important;}.${h}{outline:3px%20solid%20darkviolet%20!important;box-shadow:0%200%200%202px%20%23fff,0%200%208px%202px%20darkviolet%20!important;}%23${d}{position:fixed;top:10px;right:10px;z-index:99999;background-color:%23333;color:white;border:none;padding:8px%2012px;border-radius:4px;cursor:pointer;font-family:sans-serif;font-size:14px;opacity:0.8;transition:opacity%200.3s;}%23${d}:hover{opacity:1;}%23${e}{position:fixed;top:50px;right:10px;z-index:99999;background-color:%23f9f9f9;border:1px%20solid%20%23ccc;padding:10px;border-radius:4px;font-family:sans-serif;font-size:12px;line-height:1.5;box-shadow:0%202px%205px%20rgba(0,0,0,0.2);}%23${e}p{margin:0;}%23${e}.legend-item{display:flex;align-items:center;margin-bottom:5px;}%23${e}.legend-color-box{width:15px;height:15px;margin-right:8px;border:1px%20solid%20%23aaa;}`,document.head.appendChild(a)}})(),function(){let%20c=document.getElementById(d);c||(c=document.createElement(%22button%22),c.id=d,c.textContent=%22Toggle%20Print%20Media%20Highlights%22,document.body.appendChild(c));let%20f=document.getElementById(e);f||(f=document.createElement(%22div%22),f.id=e,f.innerHTML=`%3Cdiv%20class=%22legend-item%22%3E%3Cdiv%20class=%22legend-color-box%22%20style=%22background-color:limegreen;%22%3E%3C/div%3E%3Cp%3EVisible%20only%20in%20Print%3C/p%3E%3C/div%3E%3Cdiv%20class=%22legend-item%22%3E%3Cdiv%20class=%22legend-color-box%22%20style=%22background-color:dodgerblue;%22%3E%3C/div%3E%3Cp%3EHidden%20in%20Print%3C/p%3E%3C/div%3E%3Cdiv%20class=%22legend-item%22%3E%3Cdiv%20class=%22legend-color-box%22%20style=%22background-color:darkviolet;%22%3E%3C/div%3E%3Cp%3ECSS%20Change%20in%20Print%3C/p%3E%3C/div%3E%3Cdiv%20class=%22legend-item%22%3E%3Cdiv%20class=%22legend-color-box%22%20style=%22background-color:red;%22%3E%3C/div%3E%3Cp%3EGeneral%20Print%20Style%3C/p%3E%3C/div%3E`,document.body.appendChild(f)),f.style.display=%22none%22;let%20g=!1;c.onclick=function(){g%3F(a(),c.textContent=%22Toggle%20Print%20Media%20Highlights(Off)%22,f.style.display=%22none%22):(b(),c.textContent=%22Toggle%20Print%20Media%20Highlights(On)%22,f.style.display=%22block%22),g=!g}}(),a(),document.getElementById(d).textContent=%22Toggle%20Print%20Media%20Highlights(Off)%22;const%20j=document.getElementById(e);j%26%26(j.style.display=%22none%22)})()}();">Print Highlighter</a>

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
javascript:void%20function(){javascript:(function(){function%20a(){document.querySelectorAll(`.${i},.${f},.${g},.${h}`).forEach(function(a){a.classList.remove(i,f,g,h)})}function%20b(){function%20b(a){try{a.cssRules%26%26Array.from(a.cssRules).forEach(function(a){a.type===CSSRule.MEDIA_RULE%26%26a.media.mediaText.includes(%22print%22)%3FArray.from(a.cssRules).forEach(function(a){a.selectorText%26%26(!c.has(a.selectorText)%26%26c.set(a.selectorText,[]),c.get(a.selectorText).push(a),d.add(a.selectorText))}):a.type===CSSRule.IMPORT_RULE%26%26b(a.styleSheet)})}catch(a){}}a();const%20c=new%20Map,d=new%20Set;Array.from(document.styleSheets).forEach(function(a){b(a)}),document.querySelectorAll(%22*%22).forEach(function(a){const%20b=window.getComputedStyle(a),d=b.getPropertyValue(%22display%22);let%20e=!1,j=!1,k=!1;if(0%3Cc.size)for(const%20h%20of%20c.keys())try{if(a.matches(h)){e=!0;const%20i=c.get(h),l=i.find(a=%3Ea.style%26%26a.style.display);if(l){const%20b=l.style.display;%22none%22===d%26%26%22none%22!==b%3F(a.classList.add(f),j=!0):%22none%22!==d%26%26%22none%22===b%26%26(a.classList.add(g),j=!0)}for(const%20a%20of%20i){if(a.style)for(let%20c=0;c%3Ca.style.length;c++){const%20d=a.style[c],e=a.style.getPropertyValue(d),f=b.getPropertyValue(d);if(%22display%22!==d%26%26e!==f){k=!0;break}}if(k)break}}}catch(a){}!e||j||k||a.classList.add(i),k%26%26a.classList.add(h)})}const%20c=%22print-media-highlight-style%22,d=%22print-media-highlight-toggle-button%22,e=%22print-media-highlight-legend%22,f=%22print-media-highlight-print-only%22,g=%22print-media-highlight-hidden-print%22,h=%22print-media-highlight-css-change%22,i=%22print-media-highlight-general%22;(function(){if(!document.getElementById(c)){const%20a=document.createElement(%22style%22);a.id=c,a.textContent=`%20.${i}{outline:3px%20solid%20red%20!important;box-shadow:0%200%200%202px%20%23fff,0%200%208px%202px%20%23f00%20!important;}.${f}{outline:3px%20solid%20limegreen%20!important;box-shadow:0%200%200%202px%20%23fff,0%200%208px%202px%20limegreen%20!important;}.${g}{outline:3px%20solid%20dodgerblue%20!important;box-shadow:0%200%200%202px%20%23fff,0%200%208px%202px%20dodgerblue%20!important;}.${h}{outline:3px%20solid%20darkviolet%20!important;box-shadow:0%200%200%202px%20%23fff,0%200%208px%202px%20darkviolet%20!important;}%23${d}{position:fixed;top:10px;right:10px;z-index:99999;background-color:%23333;color:white;border:none;padding:8px%2012px;border-radius:4px;cursor:pointer;font-family:sans-serif;font-size:14px;opacity:0.8;transition:opacity%200.3s;}%23${d}:hover{opacity:1;}%23${e}{position:fixed;top:50px;right:10px;z-index:99999;background-color:%23f9f9f9;border:1px%20solid%20%23ccc;padding:10px;border-radius:4px;font-family:sans-serif;font-size:12px;line-height:1.5;box-shadow:0%202px%205px%20rgba(0,0,0,0.2);}%23${e}p{margin:0;}%23${e}.legend-item{display:flex;align-items:center;margin-bottom:5px;}%23${e}.legend-color-box{width:15px;height:15px;margin-right:8px;border:1px%20solid%20%23aaa;}`,document.head.appendChild(a)}})(),function(){let%20c=document.getElementById(d);c||(c=document.createElement(%22button%22),c.id=d,c.textContent=%22Toggle%20Print%20Media%20Highlights%22,document.body.appendChild(c));let%20f=document.getElementById(e);f||(f=document.createElement(%22div%22),f.id=e,f.innerHTML=`%3Cdiv%20class=%22legend-item%22%3E%3Cdiv%20class=%22legend-color-box%22%20style=%22background-color:limegreen;%22%3E%3C/div%3E%3Cp%3EVisible%20only%20in%20Print%3C/p%3E%3C/div%3E%3Cdiv%20class=%22legend-item%22%3E%3Cdiv%20class=%22legend-color-box%22%20style=%22background-color:dodgerblue;%22%3E%3C/div%3E%3Cp%3EHidden%20in%20Print%3C/p%3E%3C/div%3E%3Cdiv%20class=%22legend-item%22%3E%3Cdiv%20class=%22legend-color-box%22%20style=%22background-color:darkviolet;%22%3E%3C/div%3E%3Cp%3ECSS%20Change%20in%20Print%3C/p%3E%3C/div%3E%3Cdiv%20class=%22legend-item%22%3E%3Cdiv%20class=%22legend-color-box%22%20style=%22background-color:red;%22%3E%3C/div%3E%3Cp%3EGeneral%20Print%20Style%3C/p%3E%3C/div%3E`,document.body.appendChild(f)),f.style.display=%22none%22;let%20g=!1;c.onclick=function(){g%3F(a(),c.textContent=%22Toggle%20Print%20Media%20Highlights(Off)%22,f.style.display=%22none%22):(b(),c.textContent=%22Toggle%20Print%20Media%20Highlights(On)%22,f.style.display=%22block%22),g=!g}}(),a(),document.getElementById(d).textContent=%22Toggle%20Print%20Media%20Highlights(Off)%22;const%20j=document.getElementById(e);j%26%26(j.style.display=%22none%22)})()}();
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
