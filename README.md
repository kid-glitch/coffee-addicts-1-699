LINK BÀI LAB: https://www.vulnhub.com/entry/coffee-addicts-1,699/

Tiến hành SCAN:

![image](https://user-images.githubusercontent.com/72652376/126094998-8eb07ff3-a456-4369-8120-7b2e5817045e.png)

Phát hiện được IP của máy chủ, tiến hành scan port

![image](https://user-images.githubusercontent.com/72652376/126095043-94f69d71-1b1c-4dd7-8454-f940bca73381.png)

Thu được 2 port 22(SSH) và 80 (HTTP). Truy cập vào xem cổng 80 có gì

Ở đây yêu cầu thêm host coffeeaddicts.thm và file /etc/host (phải dùng quyền sudo của kali)

![image](https://user-images.githubusercontent.com/72652376/126094980-1c398920-484d-4359-bee7-e172b558c153.png)

Scan các thư mục ẩn:

![image](https://user-images.githubusercontent.com/72652376/126095273-44f248ea-568a-4d7d-884c-dbebe0bca5d5.png)

![image](https://user-images.githubusercontent.com/72652376/126095363-7271a75b-e84f-4cf1-9df4-1ccdd3bb7bc8.png)

Tại đây 1 user hỏi rằng đây có phải là pass là gusineedyouback . Có thể dùng để đăng nhập vào trang admin của wordpress 

![image](https://user-images.githubusercontent.com/72652376/126095565-7dad91c2-d9d2-42ca-a9fe-22a43e7db55c.png)

Login thành công. Có thể up shell để tiến hành RCE

Để dễ dàng thì có thể sử dụng module của Msfconsole:

![image](https://user-images.githubusercontent.com/72652376/126095698-eed4bba6-ed86-457a-98e3-44e84258cfd5.png)

![image](https://user-images.githubusercontent.com/72652376/126095753-c13b5c84-1628-4b02-ac63-e1cd6b004aed.png)

Có 1 cờ là user.txt và 1 thư của hacker để lại nói rằng chỉ có quyền sudo mới có thể xóa trang giao diện bị hack ở trên. Nghĩa là ta phải up lên quyền root :v 

![image](https://user-images.githubusercontent.com/72652376/126095940-6b91f20f-3ef0-42ca-82c1-422bd7b4586e.png)

Có một private key để đăng nhập ssh 

![image](https://user-images.githubusercontent.com/72652376/126096113-1dc98279-8026-4cf4-aaad-3db10f886f4f.png)

Sử dụng john và ssh2john để crack pass với id trên

![image](https://user-images.githubusercontent.com/72652376/126096210-6471be54-547b-49e4-82d9-e520094cc28b.png)

Thành công có được mật khẩu để truy cập với id_rsa

Tìm cách leo thang đặc quyền, kiểm tra bằng cách:

![image](https://user-images.githubusercontent.com/72652376/126096353-1a245763-3470-46e5-819e-89a0d0a55d2c.png)

Ta thấy không phải là thư mục /bin như các cách leo thang thông thường

![image](https://user-images.githubusercontent.com/72652376/126096482-32977a31-d3c0-4a6b-8e32-069727439a3f.png)

Không cần cầu kỳ lắm cho nên có thể leo thang thành công

Cờ của root:

![image](https://user-images.githubusercontent.com/72652376/126096034-33de8b23-c209-4c1e-b4df-357154748734.png)


DONE!!!

#kid-glitch
