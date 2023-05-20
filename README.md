# AndroidChromeExtensions
Simple extensions that do some usefull work by calling it.

+ Saving the copied svg code to file (as a download)
```javascript
javascript:(
  function(){
    var svgCode = prompt('Enter SVG code:');
    if (!svgCode) {
      alert('No SVG code entered.');
      return;
    }
    var svgBlob = new Blob([svgCode], { type: 'image/svg+xml' });
    var svgURL = URL.createObjectURL(svgBlob);
    var downloadLink = document.createElement('a');
    downloadLink.href = svgURL;
    downloadLink.download = 'image.svg';
    downloadLink.style.display = 'none';
    document.body.appendChild(downloadLink);
    downloadLink.click();
    document.body.removeChild(downloadLink);
    URL.revokeObjectURL(svgURL);
  }
)();
```

+ Inspector tool

```javascript
javascript:(
  function(){
    var script = document.createElement('script');
    script.src="https://cdn.jsdelivr.net/npm/eruda";
    document.body.appendChild(script);
    script.onload=function(){
      eruda.init();
    }
  }
)();
```
