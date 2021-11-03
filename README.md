## Writeup-Cookie-Arena-Season 1

ĐÂY LÀ WRITE-UP CỦA MỘT PẠN TRẺ CHÂU ĐƯỢC HUẤN LUYỆN TẠI FPTU CẢM ƠN VÌ ĐÃ ĐỌC VÀ HÃY GÓP Ý VỚI MÌNH NHÉ !!!


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
 Sau khi sửa và thêm header xong ta bấm vào Send để nhận về Response 
 
 <a href="https://ibb.co/zmJdY6K"><img src="https://i.ibb.co/zmJdY6K/image.png" alt="image" border="0"></a>
 
 Ta được ```Flag{m4g1c@l_h34d3r_xD}```   
  <a href="https://ibb.co/FHgssS5"><img src="https://i.ibb.co/FHgssS5/image.png" alt="image" border="0"></a> 
 
 <span style='font-size:100px;'>&#128020;</span>[JS B**p B**p](http://chal4.web.letspentest.org/)
 
 
 
  
  
