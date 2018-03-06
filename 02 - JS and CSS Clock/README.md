# JS + CSS Clock

### Think
1. 如何讓CSS隨著現在時間顯示指定角度
2. element transform的`rotate`不能以中心點為旋轉點
3. 設定`div`指針預設指向12點方向


## **JavaScript 步驟**
### **<1> 建立function `setDate`**
1. `setInterval(setDate, 1000);`定時器`setInterval`設定每1000毫秒鐘執行setDate

## **CSS設定**
1. `trnasform-origin: 100%;`
改變旋轉軸心位置，設訂位100%讓他可以最右側為軸心（預設中心點為50%）
2. `transform: rotate(90deg);`
將指針`順時針旋轉90度`，預設改為12點鐘方向
參數值可超過360度，正值為順時針旋轉，負值逆時針旋轉
3. `transition: all 0.05s;`
設定秒針動畫時間長度
4. `tansition-timing-function: cubic-bezier(0.13, 2.49, 0.25, 1);`
設定transition貝茲曲線值，讓秒針有跳動感（可從chrome獲取參數值）
