##  加载和执行

----

* [浏览器线程](https://dailc.github.io/2018/01/21/js_singlethread_eventloop.html)
* js文件下载完成,会立刻执行在进行下载,所以减少执行时间,会明显改善总体性能
* 请求一个100KB明显比4个25KB要快,因为要头部header处理等需要时间,减少页面脚本数量
* 把一段内嵌脚本放在引用 外链样式表的`<link>`之后会导致页面堵塞去等待样式下载，这样做是为了确保内嵌脚本执行时候会得到可靠信息，所以不要把内嵌脚本写在link后面
* [defer 和 async](https://segmentfault.com/q/1010000000640869)
* defer在onload之前执行
* [onload 和 DOMContentLoaded](http://harttle.land/2016/05/14/binding-document-ready-event.html)
    ```js
        switch (document.readyState) {
        case "loading":
            // The document is still loading.
            break;
        case "interactive":
            // The document has finished loading.
            // We can now access the DOM elements.
            var span = document.createElement("span");
            span.textContent = "A <span> element.";
            document.body.appendChild(span);
            break;
        case "complete":
            // The page is fully loaded.
            let CSS_rule = document.styleSheets[0].cssRules[0].cssText;
            console.log(`The first CSS rule is: ${CSS_rule }`);
            break;
        }

        // 模拟 DOMContentLoaded/ jquery ready
        document.onreadystatechange = function () {
        if (document.readyState === "interactive") {
            initApplication();
        }
        }

        // 模拟 load/onload 事件
        document.onreadystatechange = function () {
        if (document.readyState === "complete") {
            initApplication();
        }
        }
    ```