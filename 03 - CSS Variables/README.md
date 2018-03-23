# JS30_Day3 - CSS Variables

### Think

1. 定義CSS變數，讓JS可以更新
2. 監聽 input 取得值
3. 將值對應的css樣式套入圖片

## **JavaScript步驟**
1. 宣告變數`inputs`，取得頁面所有`input`元素
2. 監聽`inputs`，只要有變動`change`即觸發`handleUpdate`更新
    ```js
    inputs.forEach(input => input.addEventListener('change', handleUpdate));
    ```
3. 增加滑鼠滑動`mousemove`的監聽(方法同2)
**但是mousemove方法只要滑鼠有變動值就會改變，可以再新增有click之類的達到按下滑動才改變的功能

4. CSS雖然有宣告屬性值，但沒有值的suffix(單位識別)，所以，宣告suffix，並用自訂屬性data-sizing帶入值
    ```js
    const suffix = this.dataset.sizing || ''; //suffix等於dataset.sizing 或 nothing
    ```

5. 再將變動的CSS樣式值存入CSS內(記得加上suffix，才能有單會可以顯示變動)

### HTML部分
1. `<input type="range">` 滑動軸
  補充`range`的css運用
  http://www.oxxostudio.tw/articles/201503/html5-input-range-style.html
2. `<input type="color">` 顏色選擇器

### CSS部分
1. 利用`:root`宣告全域css變數初始值(default)，`--+變數名稱`（sass的是`$+變數名稱`）
2. 定義完成後即可在選擇器`img{}`內使用變數
3. `hl{}`也利用變數取值

