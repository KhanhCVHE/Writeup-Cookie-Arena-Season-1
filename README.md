## Writeup-Cookie-Arena-Season 1

ĐÂY LÀ WRITE-UP CỦA MỘT PẠN TRẺ CHÂU CẢM ƠN VÌ ĐÃ ĐỌC VÀ HÃY GÓP Ý VỚI MÌNH NHÉ !!!


![image](https://user-images.githubusercontent.com/75576279/140270016-3e2ad2cf-d07b-446e-9a0e-b0f0e89df6ef.png)

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
  
  ![image](https://user-images.githubusercontent.com/75576279/140270060-7a1a8e15-426b-4db4-aeed-d0d2a215c7cb.png)
  
  Ok "You are not CookieHanHoan!" Bắt đầu sửa cookie bằng EditThisCookie từ Guest thành CookieHanHoan ta sẽ có Flag đầu tiên.  
![image](https://user-images.githubusercontent.com/75576279/140270336-af8a927e-7934-468a-be98-b99425077a19.png)

```Flag{Cookies_Yummy_Cookies_Yammy!}```       
 
 <span style='font-size:100px;'>&#128020;</span> [Header 401](http://chal3.web.letspentest.org/)     
 
 Ta sẽ dùng Burp Suite để lấy các Request từ website  
![image](https://user-images.githubusercontent.com/75576279/140270430-25e514c0-1d42-43ae-b950-e7016f5f355f.png)
  
 Tiếp theo tiến hành Send to repeater để chỉnh sửa Request và gửi nó đi.  
 ![image](https://user-images.githubusercontent.com/75576279/140270444-7d0a2180-ea5f-4992-a6e7-f36050c5c5bc.png)  
 Tại phần Repeater ta tiến hành chỉnh sửa  
     ```GET thành POST và thêm một header: Authorization: Basic Z2Fjb25sb250b246Y29va2llaGFuaG9hbg==```   
 Sau khi sửa và thêm header xong ta bấm vào Send để nhận về Response.
 
 ![image](https://user-images.githubusercontent.com/75576279/140270475-7c4814e4-b45c-4c8c-932a-bb1cf1d6d034.png)
 
 Ta được ```Flag{m4g1c@l_h34d3r_xD}```   
  ![image](https://user-images.githubusercontent.com/75576279/140270496-26689706-979e-4b3e-9bbc-42248122e726.png) 
 
 <span style='font-size:100px;'>&#128020;</span>[JS Beep Beep](http://chal4.web.letspentest.org/)  
 Đọc đề bài thì có lẽ bài này liên quan đến JS ta phát hiện ra có 4 phần JS đều đã được mã hóa, ta sẽ phải chuyển sang dạng eval nó bằng công cụ "JavaScript Deobfuscator and Unpacker"  
 ![image](https://user-images.githubusercontent.com/75576279/140270532-17d20b0e-d426-4e8c-85a4-3f2797eb2fd4.png)
![image](https://user-images.githubusercontent.com/75576279/140270559-ec88a0db-5e33-4e2a-8931-ad23a4e510a3.png)  
```
Username=cookiehanhoan
Password=sup3rSercur3p@ssW0rd
```
 Sau khi đọc được code phần role ta thấy nó có 5 ký tự và đó là bảng mã ASCII  
 ![image](https://user-images.githubusercontent.com/75576279/140270581-d09ccd28-a67a-4005-9ff2-accb546de8c5.png)  
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
	![image](https://user-images.githubusercontent.com/75576279/140270603-c2eb28d2-9881-4b88-b94d-833690974161.png)    
Ta tiến hành Send to Intruder để bắt đầu brute-force cái id này.  
	![image](https://user-images.githubusercontent.com/75576279/140270621-f5caa8a1-4560-4ce9-9904-d980942699a2.png) 
Khi chạy xong ta thấy được Flag tại phần Response với Payload là 6.
	![image](https://user-images.githubusercontent.com/75576279/140270985-e3132225-7580-4d3e-9e73-d67a4ebffa41.png)  
 ```Flag{Y0u_c4ptur3_m3_xD!!!}```  
<span style='font-size:100px;'>&#128020;</span>[I am not a robot](http://chal2.web.letspentest.org/)  
Với bài này thì chắc nhiều người đọc đề bài là đã biết Flag ở đâu rồi đúng không??
Sau khi truy cập vào đường dẫn  ```http://chal2.web.letspentest.org/robots.txt```  
Ta thấy ![image](https://user-images.githubusercontent.com/75576279/140271547-ea04326e-d987-447a-a5ed-4307be61df97.png)  
Chú ý phần "Allow" tiếp theo ta sẽ gắn tiếp dường dẫn là ```http://chal2.web.letspentest.org/fl@g1337_d240c789f29416e11a3084a7b50fade5.txt```  
Flag được giấu ở đây ```Flag{N0_B0T_@ll0w}```  
<span style='font-size:100px;'>&#128020;</span>[Sause](http://chal1.web.letspentest.org/)  
Flag phần này được giấu ở source để mở phần này ta bấm Ctrl + U hoặc bấm F12 để mở Tools dev cũng có thể đọc được.  
![image](https://user-images.githubusercontent.com/75576279/140272119-f7663cf5-52b1-40c5-b7d1-59afc544e8fc.png)
```Flag{Web_Sause_Delicious}```  
<h1>Updating...</h1>	
	

