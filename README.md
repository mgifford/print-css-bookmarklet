# Print Highlighter Bookmarklet

A simple browser bookmarklet to help developers and designers quickly identify elements on a webpage that are affected by CSS print media queries. Ever wonder what disappears or changes when your page goes to print? This tool gives you a quick visual audit! This is a useful tool to help designers and developer make it easier to reduce the number of PDFs they need to publish, because they can use properly formatted HTML instead. We should [avoid using PDFs](https://www.culturehive.co.uk/resources/10-things-about-pdf-content-and-why-you-should-avoid-it/) because they have been a [real problem for many web users](https://gds.blog.gov.uk/2018/07/16/why-gov-uk-content-should-be-published-in-html-and-not-pdf/) and have been for a [long time](https://www.nngroup.com/articles/pdf-unfit-for-human-consumption/) and it contributes to [climate change](https://accessibility.blog.gov.uk/2023/06/12/making-a-positive-change-pdf-to-html/). 

## ✨ Features

* **Highlight Hidden Elements:** Marks elements that are likely hidden (display: none) in print view with a light gray background and dashed border.  
* **Highlight Altered Elements:** Marks elements that have other styles (like font size, color, etc.) changed in print view with a light yellow background and a solid orange border.  
* **Toggle On/Off:** A convenient button appears on the page to easily switch the highlighting on and off without reloading.  
* **Easy Installation:** Drag-and-drop the bookmarklet directly into your browser's favorites/bookmarks bar.

## 🚀 How to Use

1. Drag and Drop Installation:

<a href="javascript:(function()%7Bconst%20STYLE_ID%3D%22print-media-highlight-style%22%2CTOGGLE_ID%3D%22print-media-highlight-toggle-button%22%2CLEGEND_ID%3D%22print-media-highlight-legend%22%3Bfunction%20markScreenHiddenElementsWithMediaOnly(printRules%2CscreenRules)%7Bdocument.querySelectorAll(%22*%22).forEach(el%3D%3E%7Bconst%20style%3DgetComputedStyle(el)%3Bif(style.display!%3D%3D%22none%22)return%3Bfunction%20matchesMediaRules(rulesMap)%7Bfor(const%20%5Bselector%2Crules%5D%20of%20rulesMap.entries())%7Btry%7Bif(!el.matches(selector))continue%3Bfor(const%20rule%20of%20rules)%7Bif(rule.style.getPropertyValue(%22display%22)%3D%3D%3D%22none%22)return%20true%7D%7Dcatch(e)%7B%7D%7Dreturn%20false%7Dif(matchesMediaRules(printRules)%7C%7CmatchesMediaRules(screenRules))%7Bel.style.setProperty(%22display%22%2C%22block%22%2C%22important%22)%3Bel.classList.add(%22print-media-highlight-screen-hidden%22)%3Bel.setAttribute(%22data-screen-hidden%22%2C%22display%3Anone%20(@media)%22)%3Bel.title%3D%22display%3Anone%20(@media)%22%7D%7D)%7Dfunction%20clearHighlights()%7Bdocument.querySelectorAll(%22.print-media-highlight-general%2C.print-media-highlight-print-only%2C.print-media-highlight-hidden-print%2C.print-media-highlight-css-change%2C.print-media-highlight-screen-hidden%22).forEach(el%3D%3E%7Bel.classList.remove(%22print-media-highlight-general%22%2C%22print-media-highlight-print-only%22%2C%22print-media-highlight-hidden-print%22%2C%22print-media-highlight-css-change%22%2C%22print-media-highlight-screen-hidden%22)%3Bel.removeAttribute(%22data-print-css%22)%3Bel.removeAttribute(%22data-screen-hidden%22)%3Bel.style.removeProperty(%22display%22)%7D)%7Dfunction%20extractCSSFromRule(rule)%7Blet%20styles%3D%5B%5D%3Bfor(let%20i%3D0%3Bi%3Crule.style.length%3Bi++)%7Blet%20prop%3Drule.style%5Bi%5D%3Blet%20val%3Drule.style.getPropertyValue(prop)%3Bstyles.push(%60%24%7Bprop%7D%3A%24%7Bval%7D%60)%7Dreturn%20styles.join(%22%3B%20%22)%7Dfunction%20applyHighlights()%7Bconst%20printRules%3Dnew%20Map%2CscreenRules%3Dnew%20Map%3Bfunction%20collectRules(sheet)%7Btry%7Bif(sheet.cssRules)%7BArray.from(sheet.cssRules).forEach(rule%3D%3E%7Bif(rule.type%3D%3D%3DCSSRule.MEDIA_RULE)%7Bconst%20mt%3Drule.media.mediaText.toLowerCase()%3Bconst%20target%3Dmt.includes(%22print%22)%3FprintRules%3Amt.includes(%22screen%22)%3FscreenRules%3Anull%3Bif(!target)return%3BArray.from(rule.cssRules).forEach(innerRule%3D%3E%7Bif(innerRule.selectorText)%7Bif(!target.has(innerRule.selectorText))target.set(innerRule.selectorText%2C%5B%5D)%3Btarget.get(innerRule.selectorText).push(innerRule)%7D%7D)%7Delse%20if(rule.type%3D%3D%3DCSSRule.IMPORT_RULE)%7BcollectRules(rule.styleSheet)%7D%7D)%7D%7Dcatch(e)%7B%7D%7DArray.from(document.styleSheets).forEach(collectRules)%3Bdocument.querySelectorAll(%22*%22).forEach(el%3D%3E%7Bconst%20computed%3DgetComputedStyle(el)%2CdisplayNow%3Dcomputed.display%3Blet%20matchesPrint%3Dfalse%2Chidden%3Dfalse%2Cchanged%3Dfalse%3Bfor(const%20selector%20of%20printRules.keys())%7Btry%7Bif(el.matches(selector))%7BmatchesPrint%3Dtrue%3Bconst%20rules%3DprintRules.get(selector)%2Ccss%3D%5B%5D%3Brules.forEach(rule%3D%3E%7Bconst%20ruleDisplay%3Drule.style.getPropertyValue(%22display%22)%3Bif(ruleDisplay%3D%3D%3D%22none%22%26%26displayNow!%3D%3D%22none%22)%7Bel.classList.add(%22print-media-highlight-hidden-print%22)%3Bhidden%3Dtrue%7Delse%20if(ruleDisplay!%3D%3D%22none%22%26%26displayNow%3D%3D%22none%22)%7Bel.classList.add(%22print-media-highlight-print-only%22)%3Bhidden%3Dtrue%7Dfor(let%20i%3D0%3Bi%3Crule.style.length%3Bi++)%7Bconst%20prop%3Drule.style%5Bi%5D%2Cval%3Drule.style.getPropertyValue(prop)%3Bif(computed.getPropertyValue(prop)!%3D%3Dval)%7Bchanged%3Dtrue%3Bcss.push(%60%24%7Bprop%7D%3A%24%7Bval%7D%60)%7D%7D%7D)%3Bif(css.length)%7Bel.setAttribute(%22data-print-css%22%2Ccss.join(%22%3B%20%22))%3Bel.title%3D%22Print%20CSS%3A%20%22%2Bcss.join(%22%3B%20%22)%7D%7D%7Dcatch(e)%7B%7D%7Dif(matchesPrint%26%26!hidden%26%26!changed)el.classList.add(%22print-media-highlight-general%22)%3Bif(changed)el.classList.add(%22print-media-highlight-css-change%22)%7D)%3BmarkScreenHiddenElementsWithMediaOnly(printRules%2CscreenRules)%7Dfunction%20injectStyleAndLegend()%7Bif(!document.getElementById(STYLE_ID))%7Bconst%20style%3Ddocument.createElement(%22style%22)%3Bstyle.id%3DSTYLE_ID%3Bstyle.textContent%3D%22.print-media-highlight-general%7Boutline%3A3px%20solid%20red!important%7D.print-media-highlight-print-only%7Boutline%3A3px%20solid%20limegreen!important%7D.print-media-highlight-hidden-print%7Boutline%3A3px%20solid%20dodgerblue!important%7D.print-media-highlight-css-change%7Boutline%3A3px%20solid%20darkviolet!important%7D.print-media-highlight-screen-hidden%7Boutline%3A3px%20solid%20orange!important%7D%5Bdata-print-css%5D%3A%3Aafter%7Bcontent%3Aattr(data-print-css)%3Bdisplay%3Ablock%3Bfont-size%3A10px%3Bbackground%3A%23fff6e6%3Bcolor%3A%23333%3Bpadding%3A2px%204px%3Bmargin-top%3A2px%3Bborder%3A1px%20dashed%20%23ccc%3Bwhite-space%3Apre-wrap%7D%5Bdata-screen-hidden%5D%3A%3Abefore%7Bcontent%3Aattr(data-screen-hidden)%3Bdisplay%3Ablock%3Bfont-size%3A10px%3Bbackground%3A%23ffe%3Bborder%3A1px%20dashed%20orange%3Bpadding%3A2px%3Bmargin-bottom%3A2px%3Bcolor%3A%23c60%7D%23print-media-highlight-toggle-button%7Bposition%3Afixed%3Btop%3A10px%3Bright%3A10px%3Bz-index%3A99999%3Bbackground-color%3A%23333%3Bcolor%3Awhite%3Bborder%3Anone%3Bpadding%3A8px%2012px%3Bborder-radius%3A4px%3Bcursor%3Apointer%3Bfont-family%3Asans-serif%3Bfont-size%3A14px%3Bopacity%3A0.8%3Btransition%3Aopacity%200.3s%7D%23print-media-highlight-toggle-button%3Ahover%7Bopacity%3A1%7D%23print-media-highlight-legend%7Bposition%3Afixed%3Btop%3A50px%3Bright%3A10px%3Bz-index%3A99999%3Bbackground-color%3A%23f9f9f9%3Bborder%3A1px%20solid%20%23ccc%3Bpadding%3A10px%3Bborder-radius%3A4px%3Bfont-family%3Asans-serif%3Bfont-size%3A12px%3Bline-height%3A1.5%3Bbox-shadow%3A0%202px%205px%20rgba(0%2C0%2C0%2C0.2)%7D%23print-media-highlight-legend%20p%7Bmargin%3A0%7D%23print-media-highlight-legend%20.legend-item%7Bdisplay%3Aflex%3Balign-items%3Acenter%3Bmargin-bottom%3A5px%7D%23print-media-highlight-legend%20.legend-color-box%7Bwidth%3A15px%3Bheight%3A15px%3Bmargin-right%3A8px%3Bborder%3A1px%20solid%20%23aaa%7D%22%3Bdocument.head.appendChild(style)%7Dif(!document.getElementById(TOGGLE_ID))%7Bconst%20toggle%3Ddocument.createElement(%22button%22)%3Btoggle.id%3DTOGGLE_ID%3Btoggle.textContent%3D%22Toggle%20Print%20Media%20Highlights%22%3Bdocument.body.appendChild(toggle)%7Dif(!document.getElementById(LEGEND_ID))%7Bconst%20legend%3Ddocument.createElement(%22div%22)%3Blegend.id%3DLEGEND_ID%3Blegend.innerHTML%3D%22%3Cdiv%20class%3D%5C%22legend-item%5C%22%3E%3Cdiv%20class%3D%5C%22legend-color-box%5C%22%20style%3D%5C%22background-color%3Alimegreen%3B%5C%22%3E%3C/div%3E%3Cp%3EVisible%20only%20in%20Print%3C/p%3E%3C/div%3E%3Cdiv%20class%3D%5C%22legend-item%5C%22%3E%3Cdiv%20class%3D%5C%22legend-color-box%5C%22%20style%3D%5C%22background-color%3Adodgerblue%3B%5C%22%3E%3C/div%3E%3Cp%3EHidden%20in%20Print%3C/p%3E%3C/div%3E%3Cdiv%20class%3D%5C%22legend-item%5C%22%3E%3Cdiv%20class%3D%5C%22legend-color-box%5C%22%20style%3D%5C%22background-color%3Adarkviolet%3B%5C%22%3E%3C/div%3E%3Cp%3ECSS%20Change%20in%20Print%3C/p%3E%3C/div%3E%3Cdiv%20class%3D%5C%22legend-item%5C%22%3E%3Cdiv%20class%3D%5C%22legend-color-box%5C%22%20style%3D%5C%22background-color%3Ared%3B%5C%22%3E%3C/div%3E%3Cp%3EGeneral%20Print%20Style%3C/p%3E%3C/div%3E%22%3Blegend.style.display%3D%22none%22%3Bdocument.body.appendChild(legend)%7D%7DinjectStyleAndLegend()%3Blet%20state%3Dfalse%3Bdocument.getElementById(TOGGLE_ID).onclick%3Dfunction()%7Bstate%3D!state%3Bstate%3F(applyHighlights()%2Cthis.textContent%3D%22Toggle%20Print%20Media%20Highlights%20(On)%22%2Cdocument.getElementById(LEGEND_ID).style.display%3D%22block%22)%3A(clearHighlights()%2Cthis.textContent%3D%22Toggle%20Print%20Media%20Highlights%20(Off)%22%2Cdocument.getElementById(LEGEND_ID).style.display%3D%22none%22)%7D%7D)();" title="Drag to favorites bar">Print Highlighter</a>


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
    box-shadow: 0 2px 5px rgba(0, 0, 0, 0.1);
  }

  /* --- Print CSS Demo Styles --- */
  .no-print-demo {
    color: #b00;
    /* Red color */
    font-weight: bold;
    border: 2px dashed #b00;
    padding: 10px;
    margin-bottom: 10px;
  }

  .print-different-demo {
    color: #333;
    /* Dark gray */
    font-size: 1.2em;
    text-decoration: underline;
    border: 2px solid #666;
    padding: 10px;
    margin-bottom: 10px;
  }
  
  .general-print-style-demo {
    padding: 15px;
    margin-bottom: 10px;
    background-color: #f0f8ff;
    /* AliceBlue */
    border: 1px solid #ccc;
  }

  /* --- Screen Media Query --- */
  @media screen {
    .print-only-demo {
      display: none;
      /* Hidden by default */
      background-color: #e6ffe6;
      /* Light green background */
      padding: 10px;
      margin-bottom: 10px;
      border: 2px solid limegreen;
    }
  }
  
  /* --- Print Media Query --- */
  @media print {

    body {
      /* Ensure default for white background and black text for print */
      background-color: #fff !important;
      color: #000 !important;
    }

    .demo-section {
      box-shadow: none;
      /* No shadows in print */
      border: 1px solid #eee;
    }

    .no-print-demo {
      display: none !important;
      /* This will be HIDDEN IN PRINT (blue highlight) */
    }

    .print-different-demo {
      color: #007700 !important;
      /* Changes to dark green */
      font-size: 2em !important;
      /* Becomes larger */
      font-weight: bold !important;
      text-decoration: none !important;
      /* Underline removed */
      border-color: #007700 !important;
      /* Border color changes */
    }

    .print-only-demo {
      display: block !important;
      /* This will be VISIBLE ONLY IN PRINT (green highlight) */
      color: #b00 !important;
      /* Red color in print */
      font-style: italic !important;
      font-size: 1.5em !important;
      background-color: #fff !important;
      /* Background removed for print */
      border-color: #b00 !important;
      /* Border color changes */
    }

    .general-print-style-demo {
      padding: 5px !important;
      /* Smaller padding in print */
      background-color: #f0f0f0 !important;
      /* Lighter background in print */
      border: 2px solid orange !important;
      /* New border style */
    }
  }
</style>

<div class="demo-section">
  <h2>Hidden in Print</h2>
  <div class="no-print-demo"> This element has `display: none` in `@media print`. It will be highlighted with a **blue border**. In normal view, it's red and bold. </div>
  <p>This is a regular paragraph that might change its font size in print due to a general `p` rule.</p>
</div>

<div class="demo-section">
  <h2>CSS Changes in Print</h2>
  <div class="print-different-demo"> This element has several CSS properties that change in `@media print` (color, font-size, text-decoration, border). It will be highlighted with a **purple border**. In normal view, it's dark gray and underlined. </div>
</div>

<div class="demo-section">
  <h2>Visible Only in Print</h2>
  <div class="print-only-demo"> This element has `display: none` by default, but `display: block` in `@media print`. It will be highlighted with a **limegreen border**. You should only see this text when you activate the print highlights. </div>
</div>

<div class="demo-section">
  <h2>General Print Style</h2>
  <div class="general-print-style-demo"> This element has some of its general styles (like padding, background, border) changed in the print stylesheet, but no display changes or very prominent CSS changes that triggered other categories. It will be highlighted with a **red border**. </div>
</div>

   * **Tip for Mobile/Manual Install:** If the drag-and-drop doesn't work (e.g., on some mobile browsers or if you prefer manual setup), follow these steps:  
     1. Create a new bookmark in your browser.  
     2. Name it "Print Highlighter" (or anything you like).  
     3. For the URL/Location, copy the *entire* JavaScript code from the javascript: prefix below and paste it into the URL field:  

## Minified Version for the bookmark
        
```
javascript:(function()%7Bconst%20STYLE_ID%3D%22print-media-highlight-style%22%2CTOGGLE_ID%3D%22print-media-highlight-toggle-button%22%2CLEGEND_ID%3D%22print-media-highlight-legend%22%3Bfunction%20markScreenHiddenElementsWithMediaOnly(printRules%2CscreenRules)%7Bdocument.querySelectorAll(%22*%22).forEach(el%3D%3E%7Bconst%20style%3DgetComputedStyle(el)%3Bif(style.display!%3D%3D%22none%22)return%3Bfunction%20matchesMediaRules(rulesMap)%7Bfor(const%20%5Bselector%2Crules%5D%20of%20rulesMap.entries())%7Btry%7Bif(!el.matches(selector))continue%3Bfor(const%20rule%20of%20rules)%7Bif(rule.style.getPropertyValue(%22display%22)%3D%3D%3D%22none%22)return%20true%7D%7Dcatch(e)%7B%7D%7Dreturn%20false%7Dif(matchesMediaRules(printRules)%7C%7CmatchesMediaRules(screenRules))%7Bel.style.setProperty(%22display%22%2C%22block%22%2C%22important%22)%3Bel.classList.add(%22print-media-highlight-screen-hidden%22)%3Bel.setAttribute(%22data-screen-hidden%22%2C%22display%3Anone%20(@media)%22)%3Bel.title%3D%22display%3Anone%20(@media)%22%7D%7D)%7Dfunction%20clearHighlights()%7Bdocument.querySelectorAll(%22.print-media-highlight-general%2C.print-media-highlight-print-only%2C.print-media-highlight-hidden-print%2C.print-media-highlight-css-change%2C.print-media-highlight-screen-hidden%22).forEach(el%3D%3E%7Bel.classList.remove(%22print-media-highlight-general%22%2C%22print-media-highlight-print-only%22%2C%22print-media-highlight-hidden-print%22%2C%22print-media-highlight-css-change%22%2C%22print-media-highlight-screen-hidden%22)%3Bel.removeAttribute(%22data-print-css%22)%3Bel.removeAttribute(%22data-screen-hidden%22)%3Bel.style.removeProperty(%22display%22)%7D)%7Dfunction%20extractCSSFromRule(rule)%7Blet%20styles%3D%5B%5D%3Bfor(let%20i%3D0%3Bi%3Crule.style.length%3Bi++)%7Blet%20prop%3Drule.style%5Bi%5D%3Blet%20val%3Drule.style.getPropertyValue(prop)%3Bstyles.push(%60%24%7Bprop%7D%3A%24%7Bval%7D%60)%7Dreturn%20styles.join(%22%3B%20%22)%7Dfunction%20applyHighlights()%7Bconst%20printRules%3Dnew%20Map%2CscreenRules%3Dnew%20Map%3Bfunction%20collectRules(sheet)%7Btry%7Bif(sheet.cssRules)%7BArray.from(sheet.cssRules).forEach(rule%3D%3E%7Bif(rule.type%3D%3D%3DCSSRule.MEDIA_RULE)%7Bconst%20mt%3Drule.media.mediaText.toLowerCase()%3Bconst%20target%3Dmt.includes(%22print%22)%3FprintRules%3Amt.includes(%22screen%22)%3FscreenRules%3Anull%3Bif(!target)return%3BArray.from(rule.cssRules).forEach(innerRule%3D%3E%7Bif(innerRule.selectorText)%7Bif(!target.has(innerRule.selectorText))target.set(innerRule.selectorText%2C%5B%5D)%3Btarget.get(innerRule.selectorText).push(innerRule)%7D%7D)%7Delse%20if(rule.type%3D%3D%3DCSSRule.IMPORT_RULE)%7BcollectRules(rule.styleSheet)%7D%7D)%7D%7Dcatch(e)%7B%7D%7DArray.from(document.styleSheets).forEach(collectRules)%3Bdocument.querySelectorAll(%22*%22).forEach(el%3D%3E%7Bconst%20computed%3DgetComputedStyle(el)%2CdisplayNow%3Dcomputed.display%3Blet%20matchesPrint%3Dfalse%2Chidden%3Dfalse%2Cchanged%3Dfalse%3Bfor(const%20selector%20of%20printRules.keys())%7Btry%7Bif(el.matches(selector))%7BmatchesPrint%3Dtrue%3Bconst%20rules%3DprintRules.get(selector)%2Ccss%3D%5B%5D%3Brules.forEach(rule%3D%3E%7Bconst%20ruleDisplay%3Drule.style.getPropertyValue(%22display%22)%3Bif(ruleDisplay%3D%3D%3D%22none%22%26%26displayNow!%3D%3D%22none%22)%7Bel.classList.add(%22print-media-highlight-hidden-print%22)%3Bhidden%3Dtrue%7Delse%20if(ruleDisplay!%3D%3D%22none%22%26%26displayNow%3D%3D%22none%22)%7Bel.classList.add(%22print-media-highlight-print-only%22)%3Bhidden%3Dtrue%7Dfor(let%20i%3D0%3Bi%3Crule.style.length%3Bi++)%7Bconst%20prop%3Drule.style%5Bi%5D%2Cval%3Drule.style.getPropertyValue(prop)%3Bif(computed.getPropertyValue(prop)!%3D%3Dval)%7Bchanged%3Dtrue%3Bcss.push(%60%24%7Bprop%7D%3A%24%7Bval%7D%60)%7D%7D%7D)%3Bif(css.length)%7Bel.setAttribute(%22data-print-css%22%2Ccss.join(%22%3B%20%22))%3Bel.title%3D%22Print%20CSS%3A%20%22%2Bcss.join(%22%3B%20%22)%7D%7D%7Dcatch(e)%7B%7D%7Dif(matchesPrint%26%26!hidden%26%26!changed)el.classList.add(%22print-media-highlight-general%22)%3Bif(changed)el.classList.add(%22print-media-highlight-css-change%22)%7D)%3BmarkScreenHiddenElementsWithMediaOnly(printRules%2CscreenRules)%7Dfunction%20injectStyleAndLegend()%7Bif(!document.getElementById(STYLE_ID))%7Bconst%20style%3Ddocument.createElement(%22style%22)%3Bstyle.id%3DSTYLE_ID%3Bstyle.textContent%3D%22.print-media-highlight-general%7Boutline%3A3px%20solid%20red!important%7D.print-media-highlight-print-only%7Boutline%3A3px%20solid%20limegreen!important%7D.print-media-highlight-hidden-print%7Boutline%3A3px%20solid%20dodgerblue!important%7D.print-media-highlight-css-change%7Boutline%3A3px%20solid%20darkviolet!important%7D.print-media-highlight-screen-hidden%7Boutline%3A3px%20solid%20orange!important%7D%5Bdata-print-css%5D%3A%3Aafter%7Bcontent%3Aattr(data-print-css)%3Bdisplay%3Ablock%3Bfont-size%3A10px%3Bbackground%3A%23fff6e6%3Bcolor%3A%23333%3Bpadding%3A2px%204px%3Bmargin-top%3A2px%3Bborder%3A1px%20dashed%20%23ccc%3Bwhite-space%3Apre-wrap%7D%5Bdata-screen-hidden%5D%3A%3Abefore%7Bcontent%3Aattr(data-screen-hidden)%3Bdisplay%3Ablock%3Bfont-size%3A10px%3Bbackground%3A%23ffe%3Bborder%3A1px%20dashed%20orange%3Bpadding%3A2px%3Bmargin-bottom%3A2px%3Bcolor%3A%23c60%7D%23print-media-highlight-toggle-button%7Bposition%3Afixed%3Btop%3A10px%3Bright%3A10px%3Bz-index%3A99999%3Bbackground-color%3A%23333%3Bcolor%3Awhite%3Bborder%3Anone%3Bpadding%3A8px%2012px%3Bborder-radius%3A4px%3Bcursor%3Apointer%3Bfont-family%3Asans-serif%3Bfont-size%3A14px%3Bopacity%3A0.8%3Btransition%3Aopacity%200.3s%7D%23print-media-highlight-toggle-button%3Ahover%7Bopacity%3A1%7D%23print-media-highlight-legend%7Bposition%3Afixed%3Btop%3A50px%3Bright%3A10px%3Bz-index%3A99999%3Bbackground-color%3A%23f9f9f9%3Bborder%3A1px%20solid%20%23ccc%3Bpadding%3A10px%3Bborder-radius%3A4px%3Bfont-family%3Asans-serif%3Bfont-size%3A12px%3Bline-height%3A1.5%3Bbox-shadow%3A0%202px%205px%20rgba(0%2C0%2C0%2C0.2)%7D%23print-media-highlight-legend%20p%7Bmargin%3A0%7D%23print-media-highlight-legend%20.legend-item%7Bdisplay%3Aflex%3Balign-items%3Acenter%3Bmargin-bottom%3A5px%7D%23print-media-highlight-legend%20.legend-color-box%7Bwidth%3A15px%3Bheight%3A15px%3Bmargin-right%3A8px%3Bborder%3A1px%20solid%20%23aaa%7D%22%3Bdocument.head.appendChild(style)%7Dif(!document.getElementById(TOGGLE_ID))%7Bconst%20toggle%3Ddocument.createElement(%22button%22)%3Btoggle.id%3DTOGGLE_ID%3Btoggle.textContent%3D%22Toggle%20Print%20Media%20Highlights%22%3Bdocument.body.appendChild(toggle)%7Dif(!document.getElementById(LEGEND_ID))%7Bconst%20legend%3Ddocument.createElement(%22div%22)%3Blegend.id%3DLEGEND_ID%3Blegend.innerHTML%3D%22%3Cdiv%20class%3D%5C%22legend-item%5C%22%3E%3Cdiv%20class%3D%5C%22legend-color-box%5C%22%20style%3D%5C%22background-color%3Alimegreen%3B%5C%22%3E%3C/div%3E%3Cp%3EVisible%20only%20in%20Print%3C/p%3E%3C/div%3E%3Cdiv%20class%3D%5C%22legend-item%5C%22%3E%3Cdiv%20class%3D%5C%22legend-color-box%5C%22%20style%3D%5C%22background-color%3Adodgerblue%3B%5C%22%3E%3C/div%3E%3Cp%3EHidden%20in%20Print%3C/p%3E%3C/div%3E%3Cdiv%20class%3D%5C%22legend-item%5C%22%3E%3Cdiv%20class%3D%5C%22legend-color-box%5C%22%20style%3D%5C%22background-color%3Adarkviolet%3B%5C%22%3E%3C/div%3E%3Cp%3ECSS%20Change%20in%20Print%3C/p%3E%3C/div%3E%3Cdiv%20class%3D%5C%22legend-item%5C%22%3E%3Cdiv%20class%3D%5C%22legend-color-box%5C%22%20style%3D%5C%22background-color%3Ared%3B%5C%22%3E%3C/div%3E%3Cp%3EGeneral%20Print%20Style%3C/p%3E%3C/div%3E%22%3Blegend.style.display%3D%22none%22%3Bdocument.body.appendChild(legend)%7D%7DinjectStyleAndLegend()%3Blet%20state%3Dfalse%3Bdocument.getElementById(TOGGLE_ID).onclick%3Dfunction()%7Bstate%3D!state%3Bstate%3F(applyHighlights()%2Cthis.textContent%3D%22Toggle%20Print%20Media%20Highlights%20(On)%22%2Cdocument.getElementById(LEGEND_ID).style.display%3D%22block%22)%3A(clearHighlights()%2Cthis.textContent%3D%22Toggle%20Print%20Media%20Highlights%20(Off)%22%2Cdocument.getElementById(LEGEND_ID).style.display%3D%22none%22)%7D%7D)();
```

## Readable Version

```javascript
javascript: (function() {
    const STYLE_ID = "print-media-highlight-style",
        TOGGLE_ID = "print-media-highlight-toggle-button",
        LEGEND_ID = "print-media-highlight-legend";

    function markScreenHiddenElementsWithMediaOnly(printRules, screenRules) {
        document.querySelectorAll("*").forEach(el => {
            const style = getComputedStyle(el);
            if (style.display !== "none") return;

            function matchesMediaRules(rulesMap) {
                for (const [selector, rules] of rulesMap.entries()) {
                    try {
                        if (!el.matches(selector)) continue;
                        for (const rule of rules) {
                            if (rule.style.getPropertyValue("display") === "none") return true
                        }
                    } catch (e) {}
                }
                return false
            }
            if (matchesMediaRules(printRules) || matchesMediaRules(screenRules)) {
                el.style.setProperty("display", "block", "important");
                el.classList.add("print-media-highlight-screen-hidden");
                el.setAttribute("data-screen-hidden", "display:none (@media)");
                el.title = "display:none (@media)"
            }
        })
    }

    function clearHighlights() {
        document.querySelectorAll(".print-media-highlight-general,.print-media-highlight-print-only,.print-media-highlight-hidden-print,.print-media-highlight-css-change,.print-media-highlight-screen-hidden").forEach(el => {
            el.classList.remove("print-media-highlight-general", "print-media-highlight-print-only", "print-media-highlight-hidden-print", "print-media-highlight-css-change", "print-media-highlight-screen-hidden");
            el.removeAttribute("data-print-css");
            el.removeAttribute("data-screen-hidden");
            el.style.removeProperty("display")
        })
    }

    function extractCSSFromRule(rule) {
        let styles = [];
        for (let i = 0; i < rule.style.length; i) {
            let prop = rule.style[i];
            let val = rule.style.getPropertyValue(prop);
            styles.push(`${prop}:${val}`)
        }
        return styles.join("; ")
    }

    function applyHighlights() {
        const printRules = new Map,
            screenRules = new Map;

        function collectRules(sheet) {
            try {
                if (sheet.cssRules) {
                    Array.from(sheet.cssRules).forEach(rule => {
                        if (rule.type === CSSRule.MEDIA_RULE) {
                            const mt = rule.media.mediaText.toLowerCase();
                            const target = mt.includes("print") ? printRules : mt.includes("screen") ? screenRules : null;
                            if (!target) return;
                            Array.from(rule.cssRules).forEach(innerRule => {
                                if (innerRule.selectorText) {
                                    if (!target.has(innerRule.selectorText)) target.set(innerRule.selectorText, []);
                                    target.get(innerRule.selectorText).push(innerRule)
                                }
                            })
                        } else if (rule.type === CSSRule.IMPORT_RULE) {
                            collectRules(rule.styleSheet)
                        }
                    })
                }
            } catch (e) {}
        }
        Array.from(document.styleSheets).forEach(collectRules);
        document.querySelectorAll("*").forEach(el => {
            const computed = getComputedStyle(el),
                displayNow = computed.display;
            let matchesPrint = false,
                hidden = false,
                changed = false;
            for (const selector of printRules.keys()) {
                try {
                    if (el.matches(selector)) {
                        matchesPrint = true;
                        const rules = printRules.get(selector),
                            css = [];
                        rules.forEach(rule => {
                            const ruleDisplay = rule.style.getPropertyValue("display");
                            if (ruleDisplay === "none" && displayNow !== "none") {
                                el.classList.add("print-media-highlight-hidden-print");
                                hidden = true
                            } else if (ruleDisplay !== "none" && displayNow == "none") {
                                el.classList.add("print-media-highlight-print-only");
                                hidden = true
                            }
                            for (let i = 0; i < rule.style.length; i) {
                                const prop = rule.style[i],
                                    val = rule.style.getPropertyValue(prop);
                                if (computed.getPropertyValue(prop) !== val) {
                                    changed = true;
                                    css.push(`${prop}:${val}`)
                                }
                            }
                        });
                        if (css.length) {
                            el.setAttribute("data-print-css", css.join("; "));
                            el.title = "Print CSS: " + css.join("; ")
                        }
                    }
                } catch (e) {}
            }
            if (matchesPrint && !hidden && !changed) el.classList.add("print-media-highlight-general");
            if (changed) el.classList.add("print-media-highlight-css-change")
        });
        markScreenHiddenElementsWithMediaOnly(printRules, screenRules)
    }

    function injectStyleAndLegend() {
        if (!document.getElementById(STYLE_ID)) {
            const style = document.createElement("style");
            style.id = STYLE_ID;
            style.textContent = ".print-media-highlight-general{outline:3px solid red!important}.print-media-highlight-print-only{outline:3px solid limegreen!important}.print-media-highlight-hidden-print{outline:3px solid dodgerblue!important}.print-media-highlight-css-change{outline:3px solid darkviolet!important}.print-media-highlight-screen-hidden{outline:3px solid orange!important}[data-print-css]::after{content:attr(data-print-css);display:block;font-size:10px;background:#fff6e6;color:#333;padding:2px 4px;margin-top:2px;border:1px dashed #ccc;white-space:pre-wrap}[data-screen-hidden]::before{content:attr(data-screen-hidden);display:block;font-size:10px;background:#ffe;border:1px dashed orange;padding:2px;margin-bottom:2px;color:#c60}#print-media-highlight-toggle-button{position:fixed;top:10px;right:10px;z-index:99999;background-color:#333;color:white;border:none;padding:8px 12px;border-radius:4px;cursor:pointer;font-family:sans-serif;font-size:14px;opacity:0.8;transition:opacity 0.3s}#print-media-highlight-toggle-button:hover{opacity:1}#print-media-highlight-legend{position:fixed;top:50px;right:10px;z-index:99999;background-color:#f9f9f9;border:1px solid #ccc;padding:10px;border-radius:4px;font-family:sans-serif;font-size:12px;line-height:1.5;box-shadow:0 2px 5px rgba(0,0,0,0.2)}#print-media-highlight-legend p{margin:0}#print-media-highlight-legend .legend-item{display:flex;align-items:center;margin-bottom:5px}#print-media-highlight-legend .legend-color-box{width:15px;height:15px;margin-right:8px;border:1px solid #aaa}";
            document.head.appendChild(style)
        }
        if (!document.getElementById(TOGGLE_ID)) {
            const toggle = document.createElement("button");
            toggle.id = TOGGLE_ID;
            toggle.textContent = "Toggle Print Media Highlights";
            document.body.appendChild(toggle)
        }
        if (!document.getElementById(LEGEND_ID)) {
            const legend = document.createElement("div");
            legend.id = LEGEND_ID;
            legend.innerHTML = "<div class=\"legend-item\"><div class=\"legend-color-box\" style=\"background-color:limegreen;\"></div><p>Visible only in Print</p></div><div class=\"legend-item\"><div class=\"legend-color-box\" style=\"background-color:dodgerblue;\"></div><p>Hidden in Print</p></div><div class=\"legend-item\"><div class=\"legend-color-box\" style=\"background-color:darkviolet;\"></div><p>CSS Change in Print</p></div><div class=\"legend-item\"><div class=\"legend-color-box\" style=\"background-color:red;\"></div><p>General Print Style</p></div>";
            legend.style.display = "none";
            document.body.appendChild(legend)
        }
    }
    injectStyleAndLegend();
    let state = false;
    document.getElementById(TOGGLE_ID).onclick = function() {
        state = !state;
        state ? (applyHighlights(), this.textContent = "Toggle Print Media Highlights (On)", document.getElementById(LEGEND_ID).style.display = "block") : (clearHighlights(), this.textContent = "Toggle Print Media Highlights (Off)", document.getElementById(LEGEND_ID).style.display = "none")
    }
})();
```

3. **Activate:** Navigate to any webpage you want to analyze, then click the "Print Highlighter" bookmarklet in your bookmarks bar.  
4. **Toggle:** A button will appear in the top-right corner of the page. Click it to activate the highlighting. Click it again to turn it off.

## ⚠️ Limitations & Notes

* This bookmarklet performs a heuristic analysis of CSS print rules. While effective for common cases, it's not a full print rendering engine. Complex print layouts or JavaScript-driven style changes might not be perfectly represented.  
* It focuses on display: none for hidden elements and general style changes for altered elements based on parsed CSS rules.  
* The highlighting is temporary and will disappear if you navigate away from the page or refresh it.

## 🤝 Contributing

Feel free to suggest improvements or report issues! This bookmarklet is a useful tool, and contributions are welcome.

## 📄 Learn More

- [How does print CSS work? (MDN)](https://developer.mozilla.org/en-US/docs/Web/CSS/@media/print)
- [Printedcss.com](https://printedcss.com/)
- [How to on Print Friendly CSS](https://coderscratchpad.com/css-creating-print-friendly-styles-with-css/)
- [Print Friendly CSS Guide](https://blog.devgenius.io/printing-with-style-using-css-for-printer-optimization-643f270eb102)
- [Minimify the JS](https://www.terrific.tools/code/js-minify)
- [Create the Bookmarklet](https://chriszarate.github.io/bookmarkleter)
- [Beutify the JS](https://js-beautify.com/)

### How to use this README on GitHub:

1. Create a new repository on GitHub (e.g., print-highlighter-bookmarklet).  
2. In the repository, create a new file named README.md.  
3. Copy and paste the entire content above into your README.md file.  
4. Commit the changes.

Now, when someone visits your GitHub repository, they'll see this [README](https://github.com/mgifford/print-css-bookmarklet), and they can easily drag the "Print Highlighter" link to their bookmarks bar!

<p style="font-size:0.95em;color:#666;">Tip: Use your browser's <b>Print Preview</b> to see the effect of these styles.</p>
