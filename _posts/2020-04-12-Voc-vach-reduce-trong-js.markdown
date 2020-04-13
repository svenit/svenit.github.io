---
layout: post
title:  "Vọc vạch Reduce trong JavaScript"
date:   2020-04-12 20:00:00 +0000
categories: Javascript
---
Xin chào các bạn đến với seri JavaScript căn bản cho Beginner ^^ 

Do tình hình nghỉ dịch hơi lâu nên tay chân mình có hơi bứt dứt nên ngồi viết tạm cái blog chém gió về code :D

Bài viết này mình nhắm tới những người mới bắt đầu với Javascript hoặc những người mới bắt đầu làm việc với Javascript nhưng chưa hiểu cách sử dụng reduce. Trước khi bắt đầu chúng ta điểm qua một vài khái niệm nhé

**Functional programming là gì ?**

Functional programming là một mô hình lập trình trong đó giá trị đầu ra của hàm chỉ phụ thuộc vào các đối số được truyền cho hàm đó , vì vậy việc gọi một hàm định nghĩa số lần sẽ luôn tạo ra cùng một kết quả , bất kể số lần bạn gọi là bao nhiêu . Điều này có vẻ trái ngược với lập trình thông thường , khi mà có rất nhiều hàm hoạt động với trạng thái là local hoặc global , có thể kết thúc trả về các kết quả khác nhau ở các lần thực thi khác nhau . Khi có sự thay đổi trong trạng thái đó có thể sẽ xuất hiện vấn đề và loại trừ những điều đó có thể giúp bạn hiểu và đoán hành vi code của mình dễ dàng hơn .

**Tại sao lại sử dụng  reduce ?**

Một trong những nền tảng chính của functional programming là việc sử dụng list và cách hoạt động của list . Trong Javascript chúng ta có map, filter và reduce , tất cả các chức năng khi đưa ra một danh sách ban đầu sau biến nó thành cái gì đó khác , nhưng vẫn giữ nguyên list gốc của nó . Mình hay sử dụng reduce để làm các bài toán như tìm kiếm min, max...

**Reduce là gì ?**

Hàm  **reduce**  sẽ biến đổi một mảng thành một giá trị đơn giản. Hàm  **reduce**  sẽ thực hiện một hàm được cung cấp cho mỗi giá trị của mảng, từ trái qua phải. Hàm sẽ trả về một kết quả được lưu trữ( tổng số hoặc kết quả tính toàn)

**Bắt đầu nào :))**

Lướt qua vài định nghĩa bên trên rồi giờ chúng ta luôn bước thực hành cho nóng =))

Dưới đây là cú pháp khi sử dụng reduce : 
```js
let something = arr.reduce((a, b) => {
    // Statements
}, defaultValue);
```
Trong đó :
`something` là một biến các bạn định nghĩa để gọi sau này
`arr` là mảng các bạn cân xử lý
`a` là giá trị của bước trước đó
`b` là giá trị hiện tại
`defaultValue` là giá trị mặc định của `a` khi `a` chưa được set

Nhìn cú pháp có vẻ khá đơn giản nhỉ ^^

Giờ thử làm một vài bài toán nhé =))

``Tính tổng các số trong mảng``

```js
   // Ta có một mảng như này
let arr = [1, 3, 6, 6,2, 10, 7];
```
**Dùng for :** 
```js
let sum = 0;
for(let i = 0; i < arr.length; ++i) 
{
    sum += arr[i];
}
console.log(sum);
```
**Dùng reduce :**
```js
let sum = arr.reduce((a, b) => a + b, defaultValue = 0);
console.log(sum);
```

Để mình giải thích qua cho dễ hiểu =)) 
Như đã giải thích chức năng của hàm reduce bên trên rồi, thì các bạn có thể thấy ta truyền vào 2 tham số ``a`` và ``b``. 
``a`` sẽ giá trị của bước trước đó, nếu như không có bước trước đó ``a`` sẽ được gán bằng ``defaultValue``, b sẽ là giá trị hiện tại. Hiểu đơn giản thì sẽ là như này : 

Step 1 : Do chưa có bước trước đó => ``a`` được gán bằng ``defaultValue``  = 0  => ``a`` = 0 tiếp theo b = 1 và ta được tổng ban đầu bằng 1

Step 2 : Lúc này ``a`` của ta đã được gán bằng 1 ở bước trước đó nên ta sẽ được kết quả bằng ``a`` + 3 ( b ) = 4 =))

Cứ như vậy cho đến khi hết mảng thì ta sẽ ra được kết quả :)) À còn 1 lưu ý đó là các bạn bắt buộc phải return nhé không return là không chạy được đâu =)) Còn nếu các bạn hỏi tại sao bên trên mình lại k dùng return thì do code chỉ có 1 line lên JS ngầm định cho mình đó là giá trị trả về luôn ( khá là ngô bá khá ^^ )

Ta có thể dễ dàng tìm min hoặc max với reduce : 
Giả sử ta có 1 mảng như sau : 
```js
let arr = [23, 92, 76, 5, 43, 16, 8, 104];
```
**Dùng for :** 

```js
let min = arr[0];
for(let i = 0;i < arr.length; ++i)
{
    min = min > arr[i] ? arr[i] : min;
}
console.log(min);
```

**Dùng reduce :** 
```js
let min = arr.reduce((a, b) => a > b ? b : a, arr[0]);
console.log(min);
```

Game là dễ nhỉ :'D

Để tìm max ta làm tương tự bằng cách thay dấu ``>`` thành ``<`` thôi ^^

Vậy là ta vừa tìm hiểu xong 1 vài bài toán cơ bản mà ta có thể sử dụng reduce một cách dễ dàng và ngắn gọn ^^

Ở phần tiếp theo mình sẽ hướng dẫn các bạn sử dụng map và filter trong JS

Hẹn gặp lại các bạn ở bài viết tiếp theo

**Xin chân thành cảm ơn**



