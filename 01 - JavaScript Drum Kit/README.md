# Drum Kit

  敲擊不同的鍵盤，播放對應樂器的聲音，並做出鍵盤動畫

### 

### CSS概念

```css
.key {
	border: .4rem solid black;
	border-radius: .5rem;
	margin: 1rem;
	font-size: 1.5rem;
	padding: 1rem .5rem;
	transition: all .07s ease;
	width: 10rem;
	text-align: center;
	color: white;
	background: rgba(0,0,0,0.4);
	text-shadow: 0 0 .5rem black;
}
```

#### 1. flex基本用法  
  - 設定外層display: flex;
  - 給予內層不同flex值，會利用加總的值平均分配寬度(高度)  
  keys {  
    display: flex;  
    flex:1; //會利用內層flex加總的值下去分配  
    align-items : center; //垂直置中  
    justify-content:center; //水平置中  
  }  
  - flex-direction
    有以下幾種值：
      - row（預設）
      - row-reverse（水平反轉）
      - column（垂直）
      - column-reverse（垂直反轉）
      

## **javascript 步驟**
### **<1> keydown監聽**
`window.addEventListener('keydown', playSound);`監聽鍵盤
### **<2> 建立function `playSound`**
1. `audio`, `key`取得對應`data-key`的元素
2. 若不是則退出`return`
3. 對取得的元素進行播放及特效
4. 設定`audio`播放時間為0，才可以連擊
### **<3> 監聽transitionend**
1. 新增常數`keys`，傳入`class = "key"`的元素
2. 當特效被觸發並結束(transitionend)，呼叫`removeTransition`
### **<4> 建立function `removeTransition`**
1. 傳入的propertyName若不是transfrom則退出
2. 若是`transform`，則移除`playing`樣式

## **javascript 語法**

```javascript
function playSound(e) {
	const audio = document.querySelector(`audio[data-key="${e.keyCode}"]`);
	const key = document.querySelector(`.key[data-key="${e.keyCode}"]`);
	if (!audio) return; // stop the funcion from running all together
	audio.currentTime = 0; // rewind to the start
	audio.play();
	key.classList.add('playing');
}

function removeTransition(e) {
	if(e.propertyName !== 'transform') return; // skip it if it's not a transform
	this.classList.remove('playing');
}

const keys = document.querySelectorAll('.key');
keys.forEach(key => key.addEventListener('transitionend', removeTransition));
window.addEventListener('keydown', playSound);
```
1. 利用自定義屬性`data-key`儲存`keyCode`，連接音檔`audio`及按鍵`div`。
2. `transitionend`事件，在CSS transition後會被觸發，利用他將特效移除。
`比起使用setTimeout讓動畫效果消失，使用transitionend事件，能夠防止css修改js也必須修改的問題`
3. `if`用來判斷其中一個發生transition的樣式，讓特效移除只執行一次。

