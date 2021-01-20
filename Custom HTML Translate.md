# Custom HTML Translate

# Custom translate
here will you how to translate page with html

## Create the HTML tag
```javascript
class TTSLANG extends HTMLElement {
    connectedCallback() {
        if (getUrlParam("lang") == "en") {
            this.innerHTML = this.getAttribute('en');
        } else if (getUrlParam("lang") == "de") {
            this.innerHTML = this.getAttribute('de');
        }
    }
}
customElements.define("dg-lang", TTSLANG);
```
output will be `<dg-lang></dg-lang>`

## Setup the HTML tag
so use you this

```html
<!-- ... Some content ... -->
<div id="what_ever_you_use">
...
<dg-lang de="Zugriff" en="Access"></dg-lang>
...
</div>
<!-- ... Some content ... -->
```

## How to get the translation

Code (get url param)
```javascript
function getUrlParam(param) {
    param = param.replace(/([\[\](){}*?+^$.\\|])/g, "\\$1");
    var regex = new RegExp("[?]" + param + "=([^&#]*)");
    var url = decodeURIComponent(window.location.href);
    var match = regex.exec(url);
    return match ? match[1] : "";
}
```

**DE**     
`https://example.com/?lang=de --> <dg-lang de="Zugriff" en="Access">Zugriff</dg-lang>`

**EN**    
`https://example.com/?lang=en --> <dg-lang de="Zugriff" en="Access">Access</dg-lang>`