# 奇怪js的東東
javascript array 可以用 array.length = 0 來清空array

debounce (防抖程式，可避免某一時間內多次執行函式)
```
function debounce(fn, delay = 300) {
    let timer;
    return function() {
        window.clearTimeout(timer)
        timer = setTimeout(()=>{
            fn.apply(this, arguments);
            window.clearTimeout(timer)
        }, delay)
    }
}
```