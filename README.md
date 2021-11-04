## Writeup-Cookie-Arena-Season 1

ĐÂY LÀ WRITE-UP CỦA MỘT PẠN TRẺ CHÂU CẢM ƠN VÌ ĐÃ ĐỌC VÀ HÃY GÓP Ý VỚI MÌNH NHÉ !!!


<a href="https://ibb.co/bFTLP9T"><img src="https://i.ibb.co/gdNw3KN/KB.jpg" alt="KB" border="0"></a>

## Challenges
<span style='font-size:100px;'>&#128020;</span> [Web Basic](https://github.com/chkhanh/Writeup-Cookie-Arena-Season-1#Web-Basic)  
<span style='font-size:100px;'>&#128020;</span> [Web Exploitation ](https://github.com/chkhanh/Writeup-Cookie-Arena-Season-1#Web-Exploitation)  
<span style='font-size:100px;'>&#128020;</span> [Programming ](https://github.com/chkhanh/Writeup-Cookie-Arena-Season-1#Programming)  
<span style='font-size:100px;'>&#128020;</span> [Network ](https://github.com/chkhanh/Writeup-Cookie-Arena-Season-1#Network)  
<span style='font-size:100px;'>&#128020;</span> [Cryptography](https://github.com/chkhanh/Writeup-Cookie-Arena-Season-1#Cryptography)  
<span style='font-size:100px;'>&#128020;</span> [Forensic](https://github.com/chkhanh/Writeup-Cookie-Arena-Season-1#Forensic)  
<span style='font-size:100px;'>&#128020;</span> [Misc](https://github.com/chkhanh/Writeup-Cookie-Arena-Season-1#Misc)  
## Web-Basic
<span style='font-size:100px;'>&#128020;</span> [Hân Hoan](http://chal5.web.letspentest.org/)
  
  Đọc đề bài đã có hint là bài này sẽ liên quan đến cookie ta sẽ thử username, password bất kỳ để xem có gì nào.
  
  <a href="https://ibb.co/RYWwZgW"><img src="https://i.ibb.co/RYWwZgW/image.png" alt="image" border="0"></a>
  
  Ok "You are not CookieHanHoan!" Bắt đầu sửa cookie bằng EditThisCookie từ Guest thành CookieHanHoan ta sẽ có Flag đầu tiên.  
<a href="https://ibb.co/kmMPB3L"><img src="https://i.ibb.co/kmMPB3L/image.png" alt="image" border="0"></a> 

```Flag{Cookies_Yummy_Cookies_Yammy!}```       
 
 <span style='font-size:100px;'>&#128020;</span> [Header 401](http://chal3.web.letspentest.org/)     
 
 Ta sẽ dùng Burp Suite để lấy các Request từ website  
  <a href="https://ibb.co/3krk86w"><img src="https://i.ibb.co/3krk86w/image.png" alt="image" border="0"></a>  
 Tiếp theo tiến hành Send to repeater để chỉnh sửa Request và gửi nó đi.  
 <a href="https://ibb.co/VwqqWK1"><img src="https://i.ibb.co/VwqqWK1/image.png" alt="image" border="0"></a>  
 Tại phần Repeater ta tiến hành chỉnh sửa  
     ```GET thành POST và thêm một header: Authorization: Basic Z2Fjb25sb250b246Y29va2llaGFuaG9hbg==```   
 Sau khi sửa và thêm header xong ta bấm vào Send để nhận về Response.
 
 <a href="https://ibb.co/zmJdY6K"><img src="https://i.ibb.co/zmJdY6K/image.png" alt="image" border="0"></a>
 
 Ta được ```Flag{m4g1c@l_h34d3r_xD}```   
  <a href="https://ibb.co/FHgssS5"><img src="https://i.ibb.co/FHgssS5/image.png" alt="image" border="0"></a> 
 
 <span style='font-size:100px;'>&#128020;</span>[JS Beep Beep](http://chal4.web.letspentest.org/)  
 Đọc đề bài thì có lẽ bài này liên quan đến JS ta phát hiện ra có 4 phần JS đều đã được mã hóa, ta sẽ phải chuyển sang dạng eval nó bằng công cụ "JavaScript Deobfuscator and Unpacker"  
 <a href="https://ibb.co/682jFMm"><img src="https://i.ibb.co/682jFMm/image.png" alt="image" border="0"></a>
<a href="https://ibb.co/FKv0G4F"><img src="https://i.ibb.co/FKv0G4F/image.png" alt="image" border="0"></a>  
```
Username=cookiehanhoan
Password=sup3rSercur3p@ssW0rd
```
 Sau khi đọc được code phần role ta thấy nó có 5 ký tự và đó là bảng mã ASCII  
 <a href="https://ibb.co/GQyPprF"><img src="https://i.ibb.co/GQyPprF/image.png" alt="image" border="0"></a>  
 ```
 role.charCodeAt(0) != 64
 role.charCodeAt(1) != 100
 role.charCodeAt(2) != 109
 role.charCodeAt(3) != 105
 role.charCodeAt(4) != 78
 -->Role=@dmiN
 ```
 Sau khi đăng nhập ta được Flag bài này ```Flag{JAV-ascript_F*ck} ```  
 
 
 <span style='font-size:100px;'>&#128020;</span>[Impossible](http://chal7.web.letspentest.org/)  
  Ta đọc source bài này ta sẽ thấy 2 password ở phần <script>.  
    
  ```<script>
function checkPass()
{
	var password = document.getElementById('password').value;
	if (btoa(password.replace("cookiehanhoan", "")) == "Y29va2llaGFuaG9hbg==") {
		window.setTimeout(function() {
			window.location.assign('check.php?password=' + password);
		}, 500);
	}
}
</script>
```
    
  Sau khi decrypt đoạn mã base64 ta được thêm 1 password là "cookiehanhoan" và suy từ phần script trên ta được password hoàn chỉnh là  
  ```ccookiehanhoanookiehanhoan```  
  Nhập vào và lấy Flag nào!  
     ```Flag{Javascript_is_not_safe???}```  
  
  <span style='font-size:100px;'>&#128020;</span>[Infinite Loop](http://chal6.web.letspentest.org/)  
Đọc kỹ "can thiệp dòng chảy" bài này thì ta vẫn dùng Burp Suite để làm. Sau khi login vào hệ thống với user và pass bất khì ta thấy 1 loại url với đuôi là "id=" vậy ta có thể suy ra đó là dòng chảy mà đề bài nhắc đến.   
<a href="https://ibb.co/dWWqdF8"><img src="https://i.ibb.co/dWWqdF8/image.png" alt="image" border="0"></a>    
Ta tiến hành Send to Intruder để bắt đầu brute-force cái id này.  
<a href="https://ibb.co/QXW5cX8"><img src="https://i.ibb.co/QXW5cX8/image.png" alt="image" border="0"></a>  
<h1>Updating...</h1>
