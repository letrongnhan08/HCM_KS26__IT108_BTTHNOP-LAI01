# PHẦN I – Làm việc với hệ điều hành và máy tính
## Bài 1: Quản lý lưu trữ và đường dẫn tệp trong Windows 
Phần 1:(Phân tích)
Sai lầm của Nam:
- Đặt file bài lưu trữ trong ổ C, file sẽ mất nếu như reset window hoặc không thể truy cập yêu cầu cần cấp quyền  "Permission Denied"
- Đặt tên file có khoảng cách "bai tap 1" khiến hệ thống không nhận diện được
- Nam không có kiến thức về gói mạng có tốc độ mạng là đơn vị Mbps khác đơn vị MB/s  tốc độ tải, và Nam nghĩ tốc độ mạng 100 Mbps chính là thời gian tải là 100 MB/s nên khi gặp 12.5 MB/s thì Nam nghĩ là nhà mạng lừa đảo

Ổ cứng SSD 256GB thực tế hiển thị nhỏ hơn vì:
1GB = 1 000 000 000 bytes thì 256 GB = 256 000 000 000 bytes 
Windows hiển thị theo hệ nhị phân: 1 GB = 1073741824 bytes 
Nên 256 000 000 000 bytes = 238,4185791 GB là con số thực tế của SSD

Phần 2 (Hoàn thiện):
cây thư mục:
D:\
├── nhap-mon-cntt\
│   └── session-01\
    │       └── bai-tap-01.py
    └── session-02\
            └── bai-tap-02.py


## Bài 2 : Phân tích hiệu năng hệ thống và quản lý đường dẫn tệp
Báo cáo phân tích:
-Nguyên nhân lỗi:
ổ đĩa C:/User/... thì mục user (tên cá nhân) trong máy của mỗi người đều có tên User khác nhau, đường dẫn tuyệt đối khi gặp một tên User khác không giống tên của người gửi thì bị lỗi đứt đường truyền 
-Phân tích luồng IPO của ứng dụng từ lúc nạp từ Storage vào RAM máy của bạn thân:
Input (đầu vào):
Người gửi các tệp file ảnh cho bạn thân để kiểm tra, file ảnh vào storage máy của bạn thân
Process (Quá trình xử lý):
máy bạn thân xác định đường truyền các file ảnh trong storage, và gặp các file ảnh bị lỗi không xác định do đứt đường truyền path 
Output (Đầu ra):
sau khi xử lý tải xong ảnh, thì mở file dự án lên thì máy bạn thân phải load file ảnh đã tải về nhưng bị lỗi không xác định thì máy cứ cố đọc thì khiến RAM quá tải 98%

Giải pháp kỹ thuật:
Viết lại cấu trúc đường dẫn tương đối:
dấu (.) ví dụ: [ ./assets/logo.png ]
dấu (..) ví dụ [ ../Src/code.py ]

3 bước xử lý để giảm lag cho máy bạn thân dựa trên Task Manager:
Cách 1: đóng ứng dụng gây lỗi như python bằng End task
Cách 2: đóng những ứng dụng không cần thiết 
Cách 3: đóng ứng dụng gây lỗi như Shopee-Lite bằng End task

## Bài 3 : Thiết kế hệ thống IoT thông minh và quản lý cấu hình 
Mô hình DIKW cho hệ thống trang trại:
1. Data (Dữ liệu thô):
Thu thập thông số môi trường như:Độ ẩm đất, độ ẩm không khí, nhiệt độ môi trường, cường độ ánh sáng, lưu lượng nước
2. Information (Thông tin):
cung cấp thông tin  (ví dụ: nhiệt độ hiện tại là 39 độ C
3. Knowledge (Hiểu biết)
Thiết lập logic tự động , tính toán ,xác định nhiệt độ là 39 độ C,  bật máy bơm vì nhiệt độ trên 35 độ C
4. Wisdom (trí tuệ):
-Dự đoán thông qua dự báo thời tiết ngày mai để tối ưu hóa việc tưới nước sao cho tốt nhất. ví dụ ngày mai có mưa thì hệ thống sẽ tưới nước cho cây giảm 35% lượng nước để tránh cây bị ngập úng

Cách tránh bẫy dữ liệu:
Bẫy 1:
luôn bật "Hidden Items" để tránh xóa mất file
Tạo thư mục riêng là Cache cho ứng dụng để dọn rác ,dọn dẹp rác trong ứng dụng
Bẫy 2:
50 MB dữ liệu/ngày thì 1 năm : 18250 MB = 18.25 GB
Tính dung lượng ổ cứng phù hợp: 18.25 GB chia 70% = 26.07 GB , nên cần ổ cứng trên 26 GB trở lên như như SSD 128GB , 256GB,512GB hoặc HDD 500 GB - 1 TB

## Bài 4 : Tối ưu tài nguyên máy tính và xây dựng hệ thống lưu trữ khoa học
Phần 1: 
-Phân tích:
Sử dụng Task Manager để tìm nguyên nhân:
RAM: phải xử lý 20 tab Chrome tìm tài liệu, vừa chạy VS Code, thì RAM 8GB quá yếu để chạy chương trình và quá tải lên 80% trở lên.
CPU: khi RAM không chạy được, CPU phải làm việc liên tục hoán đổi dữ liệu và xử lý tiến trình Chrome và VS Code , CPU có thể trên 80% trở lên và quá tải sẽ bị đứng máy.
-Giải thích sự khác biệt về vai trò giữa RAM (Bàn làm việc) và Storage (Ngăn tủ):
RAM: Là bộ nhớ tạm thời,xử lý rất nhanh các công việc và nó chỉ chứa tối đa các công việc được giao như (8 , 16 ,32 GB) và nếu số lượng công việc quá nhiêu RAM (bàn làm việc) sẽ bị kiệt sức ,quá tải khiến máy bị lag
Storage (SSD 256 GB): Là nơi lưu trữ lâu dài (tủ đồ) , có thể lưu trữ vĩnh viễn , và trong bối cảnh trên khi RAM đầy nó sẽ đem ra một ít dung lượng cho (tủ đồ) để máy không sập nguồn ứng dụng, nhưng Storage (tủ đồ) chỉ là nơi lưu trữ không có tốc độ xử lý nhanh như RAM.
Phần 2 (Thiết kế):Cây thư mục
Ví dụ:
D:\
└── APP-Python\
    └── Python-data\
        ├── demo\
        │   ├── code-cua-toi.py

D:/APP-Python/Python-data/demo/code-cua-toi.py

## Bài 5: Phân tích tốc độ truyền dữ liệu và quản lý đường dẫn tệp an toàn



\-Bảng so sánh đường dẫn tuyệt đối và tương đối:

||Đường dẫn tuyệt đối:|Đường dẫn tương đối:|
|-|-|-|
|ý nghĩa|Là vị trí của file, thư mục bắt đầu từ thư mục gốc của hệ thống (root/ổ đĩa)|Là vị trí của file, thư mục dựa trên vị trí làm việc hiện tại|
|tính di động|thấp: dù tìm chính xác nhưng dễ bị hư đường path khi sang máy người khác|hiệu quả cao: có thể copy cả dự án sang bất kỳ máy tính nào mà không bị hư path|





\-Thời gian tải file 2GB với gói mạng 80 Mbps:

2 GB = 2048 MB (Megabyte)

80 Mbps = 10 MB/s

với file nặng 2 GB với tốc độ tải 10 MB/s thì thời gian chính xác là 205 giây 



\-Viết lại Đường dẫn 

Chọn dạng Tương đối (Relative Path):

ví dụ (Project\\data\\db.csv)

đường dẫn tương đối là:

(ký hiệu "."):  \[ .data/db.csv ]

&#x20;

\- Đề xuất các bước thiết lập "View Options":

mở file explorer ,tìm thanh công cụ view, luôn bật file name extensions để nhận biết, và bật hidden item để phòng ngừa tránh file mã độc 

## Bài 6 : Thiết kế hệ thống ứng dụng theo mô hình DIKW và quản lý tệp cấu hình
Cách tránh bẫy dữ liệu:
Bẫy 1:
bật Hidden item để tránh xóa file.env khi dọn dẹp
Bẫy 2:
1 giao dịch 1 KB , 1 ngày 1 triệu giao dịch = 1000000 KB
Đổi sang MB: 1000000 KB chia 1024 MB = 976.56 MB
Cần trên 976 MB là 1 GB để lưu trữ mỗi ngày

Mô tả chi tiết 4 tầng DIKW của MoMo-Lite:
- Data (Dữ liệu thô):
Input (đầu vào):
ứng dụng nhận yêu cầu dữ liệu thô từ người dùng ví dụ như: ID tên khách hàng:123xxx , số điện thoại:xxxxx ,số tiền hiện tại: 1500000 VNĐ ,thời gian gửi: 12h00, tổng số tiền chuyển khoản tháng này: 2000000 VNĐ, tổng thu nhập: 3500000
Process (Xử lý):
xác nhận tính hợp lệ, qua mật khẩu hoặc nhận diện khuôn mặt để xác định người dùng
Output (Đầu ra):
dựa trên Nhật ký giao dịch thô đã lưu trữ
- Information (thông tin):
Input(đầu vào):
nhận dữ liệu từ data,và xác định thời gian hiện tại 
Process (Xử lý):
Tính tổng, tính phần trăm theo danh mục.
Output (Đầu ra):
Báo cáo tổng chi tiêu tháng theo biểu đồ
ví dụ: nửa tháng 4 này người dùng chi tiêu đến 2000000 = 57% tổng thu nhập, tăng 3% so với tháng 3 là 54%
- Knowledge (Tri thức):
Dựa vào ngân sách chi tiêu của người dùng
Process (Xử lý):
so sánh số liệu, dự đoán người dùng chi tiêu
Output (Đầu ra):
Đưa ra thông báo cảnh báo
ví dụ:
Hệ thống nhận diện ngân sách sử dụng tiền ở mức không ổn định và đưa ra thông báo chi tiêu :"người dùng đang chi tiêu không ổn định, có nguy cơ không đủ tiền vào cuối tháng
- Wisdom (Trí tuệ):
Input(đầu vào):
Lịch sử hành vi chi tiêu dài hạn của người dùng
Process (Xử lý):
hệ thống AI dựa trên dữ liệu đã học sẽ chạy chương trình logic và phân tích chiến lược chi tiêu hợp lý.
Output (Đầu ra):
Thông báo đưa ra kết quả chi tiêu hợp lý
Đưa ra định hướng chiến lược, giải pháp tối ưu:
ví dụ: dựa trên hành vi người dùng thích uống trà sữa mỗi ngày,mua đồ ăn vặt, mất khoảng 700000 VNĐ mỗi tháng,ứng dụng sẽ đề xuất giảm uống trà sữa chỉ nên uống vào cuối tuần, đồ ăn vặt không quá 20000 VNĐ trong 1 ngày.

# PHẦN II – các thao tác terminal
## Bài 1 : Tối ưu hóa quy trình khởi tạo hạ tầng Smart-Farm qua PowerShell

Phần 1: Phân tích
lỗi của Nam :
Lỗi thứ nhất: tên thư mục có khoảng trắng
Lỗi thứ hai: mkdir chưa tìm được src của thư mục vì src có thể không tồn tại

Nguyên nhân lỗi trong PowerShell:
-về dấu ngoặc kép : khi các từ cách nhau có khoảng trắng mà sử dụng dấu (""), PowerShell chỉ hiểu đó là tham số độc lập thay vì chuỗi văn bản
-còn lệnh cd thì cũng như trên: nếu có khoảng trắng thì cần ("") để PowerShell hiểu còn không có thì lệnh sẽ bị lỗi không chạy được.
-Thiếu thư mục ngữ cảnh do Nam không tạo các thư mục src/sensors/temperature nên sẽ ra Path not found


Phần 2: Hoàn thiện:
Chuỗi lệnh ít dòng nhất: 
mkdir "Smart-Farm-Project/src/sensors/temperature"


## Bài 2 : Chẩn đoán lỗi thực thi và xác định vị trí làm việc trong Terminal 

- Hệ điều Hành: Windows PowerShell
    

- Lệnh tạo thư mục: mkdir drink_module
    
- Di chuyển vào thư mục vừa tạo: cd drink_module
    
- Tạo 2 file trống: New-Item -Itemtype File “coffee.txt”, “tea.txt”
    

## Bài 3 : Kiến trúc sư hạ tầng server chuyên nghiệp 
Yêu cầu nghiệp vụ
Tạo cây thư mục lồng nhau
mkdir smart-farm\data\logs , smart-farm\code , smart-farm\backup
Tạo cùng lúc 3 file cấu hình:
"smart-farm\config.json", "smart-farm\sensors.py", "smart-farm\.env" | ForEach-Object { New-Item -ItemType File -Path $_ -Force }; (Get-Item "smart-farm\.env").Attributes = "Hidden"


Sao chép toàn bộ thư mục:
cp \smart-farm\code\ , \smart-farm\backup\code_v1 -Recurse -Force


Bản phác thảo sơ đồ luồng IPO của việc khởi tạo hạ tầng:
   -   Input: (dữ liệu đầu vào)
-cây thư mục lồng nhau:smart-farm\data\logs , smart-farm\code , smart-farm\backup
-3 file cấu hình: config.json, sensors.py, .env
-thư mục sao chép: smart-farm\code sang  smart-farm\backup\code_v1
  -  Process:(xử lý)
Lệnh mkdir tạo ra cây thư mục
Lệnh New-Item  là tạo ra tệp trong thư mục và Get-Item là lấy chọn file cần chọn chỉnh sửa và định dạng tệp “Attributes = Hidden” là thêm tính năng ẩn của file.env 
Lệnh Cp  và đường dẫn Path giúp xác định vị trí file và lệnh -Recurse để sao chép toàn bộ thư mục đang chọn đến thư mục cần đặt.
   -  Output: (Đầu ra)
cây thư mục tạo ra hoàn chỉnh
file cấu hình được tạo ra
thư mục  backup\code_v1 nhận được thư mục sao chép smart-farm\code
Danh sách các câu lệnh PowerShell đã sử dụng: 
mkdir
New-Item
-Recurse
 Itemtype
-Force
Copy-Item(cp)
Attributes
ForEach-Object
-Path
Get-Item

## Bài 4 : Xử lý lỗi đường dẫn khi triển khai dự án

Phần 1: Bảng so sánh Absolute Path và Relative Path 



|Tiêu chí |Absolute Path (Đường dẫn tuyệt đối) |Relative Path (Đường dẫn tương đối) |
|-|-|-|
|độ dài|Dài, ghi đầy đủ đường dẫn |Ngắn gọn hơn |
|tính di động|Thấp, phụ thuộc vào ổ đĩa và tên máy |Cao hơn, dễ chia sẻ project cho người khác |
|Độ an toàn|Thấp vì chứa tên người dùng,lộ cấu trúc máy chủ|Cao vì không lộ tên User, dấu vết phần cứng,hệ thống|



Phần 2: Lựa chọn giải pháp tối ưu và Giải thích 

\-chọn Relative Path (../data/logs.csv) vì ngắn gọn, thuận tiện khi chia sẻ project cho người khác mà không bị hư đường truyền,không phụ thuộc vào tên tài khoản User trên máy tính. 

\-Ý nghĩa ký hiệu: “..” Đại diện cho thư mục cấp cha (lùi ra 1 cấp thư mục so với thư mục hiện tại). Khi chương trình thực thi, “..” có tác dụng chỉ thị hệ thống lùi lại src → Đến thư mục D:\\FarmProject\\ (Thư mục gốc dự án)  trước khi trỏ tiếp vào thư mục (/data/logs.csv). 


## Bài 5 : Thiết kế quy trình tự động quản lý tệp bằng Terminal
Ràng buộc & Trường hợp kiểm thử (Edge Case)
lỗi "Is a directory" xảy ra khi robot sử dụng lệnh rm xóa đối với thư mục ( lệnh rm được mặc định để xóa file nên xảy ra lỗi”
ví dụ robot phát hiện thư mục tên thien.tmp nên robot thực hiện xóa thư mục bằng lệnh “rm” kết quả sẽ xảy ra lỗi "Is a directory"
-> rm thien.tmp
-> rm: cannot remove 'thien.tmp': Is a directory
dù là đuôi tmp nhưng nó lại là thư mục nên rb ko thể xóa bằng “rm”
Giải quyết: Robot gõ dir hoặc ls để xem file phải directory qua nhận biết (d------) không nếu không phải (d------) thì xóa file (-a------) để không xảy ra lỗi "Is a directory"
Yêu cầu đầu ra
sơ đồ:
tầng DIKW trong kịch bản Robot:

Data (Dữ liệu)

là Các file thô trong Downloads 

Information (Thông tin):
Robot quét và gán ngữ cảnh cho dữ liệu như File .pdf thuộc về thư mục Documents, file .tmp về thùng rác
Knowledge (Tri thức):
Robot nhận thức được rủi ro (Is a directory),áp dụng dữ liệu đã học để ra lệnh dir,ls để xem file thien.tmp có tệp con không và thuộc tính có phải (d------) không và xóa file (-a------) , tránh làm sập kịch bản
Wisdom (Trí tuệ):
Khả năng vận hành đặc biệt (ví dụ: tự động học hỏi thói quen dọn dẹp của người dùng theo khung giờ, hoặc đề xuất xóa các file rác cũ không còn sử dụng trong nhiều năm để tiết kiệm dung lượng ổ cứng)

1. input (file thô) -> 2. Process: kiểm tra xem là file hay thư mục bằng dir,ls (nếu là thư mục thì bỏ qua) -> nếu là file -> phân loại theo đuôi -> 3. output: đuôi .png/ .jpg/ -> (mv media/), đuôi .py -> (mv scripts/), đuôi .tmp -> (rm)
danh sách câu lệnh kịch bản cho Robot:
 mkdir -p media scripts
mv *.png *.jpg media/
mv *.py scripts/
dir *.tmp
rm *.tmp


## Bài 6 : Thiết lập môi trường làm việc cho hệ thống Smart-Farm trên SoC
Bước 1 : mkdir smart-farm/bin, smart-farm/config, smart-farm/data

Bước 2 :

New-Item smart-farm\\config\\.env -force

(gi smart-farm\\config\\.env -Force).Attributes='Hidden'

ls smart-farm\\config -Force

Get -ChildItem thông thường không nhìn thấy file .env vì .env được gán là file ẩn nên get-childItem chỉ tìm thấy những thư mục bình thường không tìm file ẩn nên phải dung -force để get-childItem nhìn thấy file ẩn



Bước 3 : cp C:\\Users\\Public\\template.ps1 \~\\smart-farm\\bin\\pump\_control.ps1



Bước 4 : ls smart-farm -Recurse -Force



\- Nếu gặp lỗi "Access to the path is denied"

gõ lệnh powershell:  Start-Process powershell -Verb RunAs





Nhật ký (Log) các câu lệnh PowerShell đã thực hiện:



|mkdir smart-farm/bin, smart-farm/config, smart-farm/data|tạo thư mục gồm 3 thư mục con bin,config và data|
|-|-|
|New-Item smart-farm\\config\\.env -force<br />(gi smart-farm\\config\\.env -Force).Attributes='Hidden'|tạo file ẩn <br />và xác nhận file|
|cp C:\\Users\\Public\\template.ps1 \~\\smart-farm\\bin\\pump\_control.ps1|sao chép và đổi tên file|
|ls smart-farm-Recurse -Force|xem danh sách các thư mục trong smart-farm|





Bản phân tích luồng IPO cho toàn bộ quá trình thiết lập căn cứ số này





|Input|Tạo thư mục (mkdir smart-farm/bin, smart-farm/config, smart-farm/data)<br />Tạo file ẩn (New-Item smart-farm\\config\\.env -force<br />(gi smart-farm\\config\\.env -Force).Attributes='Hidden')<br />sao chép và đổi tên file (cp C:\\Users\\Public\\template.ps1 \~\\smart-farm\\bin\\pump\_control.ps1)<br />xem danh sách các thư mục trong smart-farm (ls smart-farm-Recurse -Force)|
|-|-|
|Process|(1) mkdir tạo cây thư mục, (2) New-Item tạo .env + gi để chọn file chỉnh sửa + Attributes  ẩn file, (3) cp sao chép và đổi tên, (4) ls -Recurse -Force kiểm tra|
|Output|Cấu trúc smart-farm/ gồm bin/pump\_control.ps1, config/.env (ẩn), data/ (rỗng)|



# PHẦN III – Tự động hóa bằng script
## Bài 1 : Xử lý Log máy chủ dung lượng lớn
Phần 1:
Máy tính bị "Not Responding" khi mở bằng Notepad vì Notepad là trình soạn thảo văn bản giao diện đồ họa (GUI) thiết kế cho các tệp nhỏ, khi mở file nặng 800MB thì Notepad sẽ cố gắng tải toàn bộ nội dung tệp vào bộ nhớ RAM và hiển thị trong một trang khiến cho RAM xử lý quá tải và bị treo Not Responding
Lệnh cat bị lỗi trong CMD vì CMD cũ hơn PowerShell, và CMD quá cũ nên lập trình không có lệnh cat, và cat chỉ có trong PowerShell vì PowerShell hiện đại hơn CMD và PowerShell được thiết kế có tính hỗ trợ tương thích cao với các lệnh phổ biến như hệ điều hành Linux
Phần 2: lệnh PowerShell
-Lệnh xem toàn bộ nội dung tệp
Get-Content -Path server_log_800MB.log | more
-Lệnh xem 10 dòng cuối cùng để kiểm tra lỗi mới nhất
Get-Content -Path server_log_800MB.log -Tail 10

ý nghĩa từng tham số lệnh
-Path : xác định đường dẫn
more :xem toàn bộ nội dung tệp
-Tail 10: xem 10 dòng cuối cùng để kiểm tra lỗi mới nhất
Get-Content đọc nội dung tệp

## Bài 2 : Xử lý sự cố Website từ Access Log
Phần 1: Phân tích
Nhầm lẫn của An:
An mắc lỗi nhầm lẫn giữa việc tìm kiếm tên tệp/thư mục và tìm kiếm nội dung bên trong tệp.
Sự khác biệt của Get-ChildItem và Select-String:
Get-ChildItem là dùng để liệt kê các tệp và thư mục trong hệ thống
Select-String lệnh chuẩn trong PowerShell dùng để tìm kiếm chuỗi văn bản bên trong nội dung các tệp
Phần 2:
Giải thích :-Path là Đường dẫn, dùng để để tìm kiếm, xác định file
-Pattern chỉ định từ khóa cần tìm kiếm bên trong nội dung tệp
viết lại lệnh:
Select-String -Path "access.log" -Pattern "error"

## Bài 3 : Thống kê sự cố TIMEOUT trên máy chủ

Phần 1:

Vẽ sơ đồ pipeline

|Lọc tệp , Tìm kiếm từ khóa (Select-String)<br /> - Quét nội dung tệp log<br /> - Lọc các dòng chứa từ khóa "TIMEOUT"|
|-|
|Lọc từ khóa loại trừ bẫy dữ liệu (Where-Object)<br /> - Lọc bỏ các dòng chứa "NOT TIMEOUT"|
|Đếm kết quả (.Count)<br /> - Tập hợp đối tượng mang theo thuộc tính .Count<br /> - Trả về duy nhất 1 con số tổng|



Phần 2: viết lại câu lệnh

(Get-Content \*.log | Select-String "TIMEOUT") | Where-Object { $\_ -notmatch "NOT TIMEOUT" }).Count

## Bài 4 : Xây dựng quy trình lưu nhật ký hệ thống

Bẫy dữ liệu:

\- Nếu An gõ ">" thay vì ">>" thì toàn bộ lịch sử dữ liệu bên trong file sẽ bị xóa toàn bộ do tính năng ghi đè của toán tử >

Phần 1: So sánh

||Toán tử >|Toán tử >>|
|-|-|-|
|Cơ chế hoạt động|Đối với tệp đã tồn tại, lệnh này ghi đè toàn bộ nội dung cũ sẽ bị xóa sạch và thay thế bằng kết quả mới|Đối với tệp đã tồn tại,sử dụng lệnh này thì kết quả mới sẽ được nối tiếp vào cuối tệp, bảo toàn dữ liệu cũ|
|Rủi ro mất dữ liệu|Cao|Thấp|
|Ngữ cảnh sử dụng thực tế|Phù hợp cho việc tạo mới báo cáo từ đầu|Phù hợp cho việc theo dõi hệ thống 24/7,thu thập và tích lũy,cập nhật liên tục mà không làm mất dữ liệu|
|Encoding file đầu ra|UTF-16<br />ANSI (Phụ thuộc vào hệ thống / Code Page)|UTF-16(Unicode, có BOM)|



Phần 2:

Giải pháp tối ưu trong PowerShell : Out-File -Append

Lý do: Bảo toàn dữ liệu lịch sử tránh mất file:

Trong hệ thống theo dõi lỗi liên tục (24/7), nhật ký của các thời điểm trước đó trong ngày rất quan trọng cho lập trình viên phân tích sự cố. Toán tử >> (và Out-File -Append) có cơ chế ghi nối tiếp vào cuối tệp, giúp dữ liệu không bị ghi đè hoặc mất mát mỗi khi kịch bản được kích hoạt chạy.

Đề xuất bổ sung: (Out-File -Append -Encoding utf8)

Get-Content server.log | Select-String "ERROR" | Out-File -FilePath "daily\_report.txt" -Append -Encoding utf8

## Tối ưu quy trình xử lý Log hằng ngày
<#
1.Header block:
Sử dụng thẻ comment nhiều dòng (<# ... #>) hoặc đơn dòng (#) ở đầu script để mô tả nội dung cần ghi
2.Biến cấu hình:Khai báo các đường dẫn tệp bằng  biến ($)
3.Thông báo tiến trình : Sử dụng Write-Host để hiển thị thông báo tiến trình ra màn hình (không lẫn vào output file)
4.Logic xử lý: khởi tạo file kết quả với tiêu đề (=== HE THONG TU DONG LOC LOG ===),sau đó dọc log (Get-Content), lọc các dòng chứa lỗi 404 (Select-String) và ghi kết quả >>
#>
# --- KHAI BÁO BIẾN CẤU HÌNH ---
$logFile = "server.log"
$reportFile = "report.txt"
$headerText = "=== HE THONG TU DONG LOC LOG ==="
# --- THÔNG BÁO TIẾN TRÌNH KHỞI TẠO ---
Write-Host " Bat dau qua trinh xu ly log..."
# --- THÔNG BÁO TIẾN TRÌNH LỌC ---
Write-Host "Dang loc file '$logFile' va loc loi 404..."
# --- LOGIC XỬ LÝ QUA PIPELINE ---
Get-Content -Path $logFile | Select-String "404" | Out-File -FilePath $reportFile -Append -Encoding utf8
# --- THÔNG BÁO HOÀN THÀNH ---
Write-Host " Success! da luu vao: $reportFile"

## Bài 6 : Rà soát Script bảo trì hệ thống
Phần 1: Phân tích
Điểm cực kỳ nguy hiểm trong đoạn mã:
Remove-Item -Path "C:\*" -Recurse -Force, đặc biệt -Path "C:\*" có dấu sao (*) xác định toàn bộ tệp
ý nghĩa:
-Path là xác định đường dẫn mục tiêu
-Recurse: Cho phép thực thi đệ quy, có thể vào các thư mục con trong thư mục cha
-Force:là tham số bắt buộc chạy mà không cần xác nhận
Hậu quả:
-Path "C:\*" có dấu sao (*) xác định toàn bộ tệp, Recurse có thể vào các thư mục con trong thư mục cha, và Force ép buộc chạy lệnh mà không có cảnh báo , khi sử dụng Remove-Item thì nó sẽ xóa toàn bộ tệp ổ C và thư mục con cũng sẽ bị xóa ,mất dữ liệu vĩnh viễn
-Sập hệ thống Windows
-Máy chủ sẽ bị tê liệt
Áp dụng 3 Nguyên tắc "Vàng" thẩm định mã AI:
Nguyên tắc 1: AI chỉ là trợ lý hỗ trợ, không quá phụ thuộc,tin tưởng vao AI quá nhiều, soi lệnh và rà soát các câu lệnh có nguy cơ xóa hoặc can thiệp sâu hệ thống 
Nguyên tắc 2: Tạo thư mục giả định/thư mục rác riêng biệt để chạy thử, kiểm tra kịch bản trước khi áp dụng vào dữ liệu thật
Nguyên tắc 3: Thực Thi Kèm Log: Chạy script chính thức và điều hướng ghi nhật ký (log) vào tệp tin (ví dụ dùng toán tử &gt;&gt; audit.log) để tiện kiểm tra, đối chiếu.
Phần 2: Triển khai 
1. Di chuyển  thư mục:
Set-Location -Path "D:\Lanfarm\Logs"
2. Lọc các dòng chữ:
Select-String -Path "system.log" -Pattern "WARNING" | Select-Object -ExpandProperty Line > issues.txt
3. xóa các tệp cần xóa bên trong thư mục dự án:
Remove-Item -Path "D:\Lanfarm\Logs\*" -Filter "*.tmp" -Force

Phần 3: Kiểm thử:
-Xem nội dung tệp báo cáo bằng Get-Content:kết quả hiển thị toàn bộ log từ khóa WARNING được lọc ra từ tệp system.log
Get-Content -Path "issues.txt"
-Get-ChildItem để liệt kê lại thư mục, xác nhận các tệp .tmp đã bị xóa:kết quả tệp .tmp bị xóa còn tệp khác vẫn nguyên vẹn
Get-ChildItem -Path "D:\Lanfarm\Logs"
-Kiểm tra sự tồn tại của tệp báo cáo bằng Test-Path: Trả về kết quả True báo cáo đã được tạo thành công
Test-Path "issues.txt"

#safe_cleanup
Set-Location -Path "D:\Lanfarm\Logs"
Select-String -Path "system.log" -Pattern "WARNING" | Select-Object -ExpandProperty Line > issues.txt
Remove-Item -Path "D:\Lanfarm\Logs\*" -Filter "*.tmp" -Force

# Phần IV - thiết kế file đặc tả (Readme.md)
## Bài 1 : Chuẩn hóa tài liệu Markdown cho dự án
--- 
 **Phần 1. Phân tích:** 
Lỗi cú pháp:
- Nhảy cấp độ tiêu đề (H1 nhảy xuống H3) mà bỏ qua H2 
Lý do kết quả render không như ý: Theo quy tắc , các cấp độ tiêu đề tiếp theo phải tuân theo thứ tự tuần tự (H1 $\rightarrow$ H2 $\rightarrow$ H3...).
- Lỗi cú pháp hình ảnh có thể bị thêm ký tự thoát `\` ở cuối `([Logo Dự án\])` hoặc có khoảng trắng giữa cặp ngoặc vuông `[]` và ngoặc tròn `()`
Lý do kết quả render không như ý: Markdown không nhận diện đây là cú pháp hình ảnh chuẩn `![Alt text](url)`, dẫn đến việc ảnh không hiển thị mà chỉ hiện dưới dạng văn bản thô hoặc liên kết lỗi.
- Lỗi in đậm văn bản:
**Lỗi:** Chỉ dùng 1 dấu sao đơn `*Rất quan trọng*` thay vì 2 dấu sao `**Rất quan trọng**`
Lý do kết quả render không như ý: Một dấu sao chỉ có tác dụng tạo chữ nghiêng

---

 Phần 2. Hoàn thiện mã nguồn Markdown:
# Lợi ích của rau sạch
## Danh sách các loại rau
![Logo Dự án](https://greentech.vn/logo.png)
**Rất quan trọng**

## Bài 2 :Chuẩn hóa tài liệu cài đặt hệ thống
## **Báo cáo phân tích (I/O):** 
- **Input (Đầu vào - Văn bản thô):**  Yêu cầu xây dựng tài liệu kỹ thuật cài đặt cảm biến độ ẩm cho trang trại hoa lan.

- Dữ liệu so sánh giữa cảm biến DHT22 và AM2302.

- Đoạn code Python điều khiển máy bơm tự động dựa trên độ ẩm.

- Danh sách công việc kiểm tra thiết bị (Task List) và các lưu ý an toàn chứa ký tự đặc biệt.

- **Output (Đầu ra - Giao diện render chuyên nghiệp):** 
- Tài liệu định dạng Markdown trực quan, phân tách rõ ràng giữa văn bản hướng dẫn thông thường, lệnh Terminal và mã nguồn lập trình.

- Bảng so sánh thông số kỹ thuật tối ưu hóa khả năng hiển thị.

- Sử dụng thành công ký tự Escape (`\`) để hiển thị các ký tự đặc biệt như `#` và `*` mà không bị lỗi cú pháp Markdown.

# Source code
Bảng so sánh:
| Tiêu chí                       | Cảm biến DHT22       | Cảm biến AM2302                      |
| :----------------------------- | :------------------- | :----------------------------------- |
| **Độ chính xác độ ẩm**         | $\pm 2-5\%$ RH       | $\pm 2\%$ RH                         |
| **Phạm vi hoạt động**          | 0 - 100% RH          | 0 - 100% RH                          |
| **Vỏ bảo vệ**                  | Nhựa cứng tiêu chuẩn | Có bọc vỏ chống nước chuyên dụng     |
| **Độ bền trong môi trường ẩm** | Trung bình           | Cao hơn                              |

---
## Task List Kiểm tra Thiết bị (Bảo trì hệ thống)

- [ ] Kiểm tra mã định danh thiết bị #1 trên sơ đồ mạch.
    
- [ ] Xác thực kết nối đường truyền mạng qua cổng giao tiếp `\*MAIN_PORT\*`.
    
- [ ] Vệ sinh đầu dò cảm biến để tránh rêu mốc bám vào bề mặt.
    
- [ ] Kiểm tra nguồn điện cấp cho relay máy bơm (Yêu cầu ổn định ở mức 12VDC).
---
python
# Chương trình điều khiển máy bơm cho trang trại Lan *v1.0*
import time

def kiem_tra_do_am(do_am):
    # Nếu độ ẩm dưới 30%, kích hoạt máy bơm nước
    if do_am < 30:
        print("Độ ẩm thấp! Bật máy bơm...")
    else:
        print("Độ ẩm ổn định.")

if __name__ == "__main__":
    do_am_hien_tai = 25
    kiem_tra_do_am(do_am_hien_tai)

## Bài 3 : Giảm chi phí vận hành Chatbot AI

Phần 1:

\- ưu thế Markdown 

Giảm tải số lượng Token bằng cách sử dụng cú pháp cực kỳ gọn như (\*\*) , (#) , (-).

\- Tốc độ xử lý của AI: LLM xử lý văn bản theo từng token (nhóm ký tự), markdown có token ít hơn html và markdown gần gũi với văn bản tự nhiên giúp AI xử lý nhanh hơn cú pháp html phức tạp.

Phần 2:So sánh \& Đánh giá

| Tiêu chí                | Markdown                                                            | HTML                                                                     |
| ----------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------------ |
| Số lượng ký tự \& Token | ngắn gọn, gần gũi văn bản tự nhiên Plain Text                       | Phức tạp (Nhiều thẻ đóng/mở rườm rà, lãng phí token)                     |
| Độ dễ đọc               | Dễ nhìn                                                             | Khó nhìn                                                                 |
| Hiệu quả xử lý của AI   | Tối ưu, LLM được huấn luyện sâu với Markdown nên ít lỗi cú pháp hơn | Kém hơn, dễ bị lỗi thiếu thẻ đóng như (</div>, </ul>) làm hỏng giao diện |
| Độ phức tạp cú pháp     | Đơn giản, dễ học và dễ chuyển đổi sang giao diện di động/Web        | Phức tạp, cần bộ phân tích cú pháp (Parser) nặng hơn ở phía client       |



Giải pháp tối ưu cho hệ thống "GreenTech"

**Giải pháp đề xuất:** Lựa chọn Markdown làm định dạng chính cho toàn bộ hệ thống đầu ra của "GreenTech"
Lập luận:
- Tiết kiệm chi phí token và tăng tốc độ xử lý của AI: sử dụng Markdown giúp giảm từ 20% đến 40% số lượng token đầu ra so với HTML và tối ưu LLM xử lý đưa câu trả lời nhanh hơn.
- Phù hợp cho nông dân sử dụng vì Markdown hiển thị thông tin trực quan,dễ nhìn .
- Độ ổn định cao cho AI: Markdown giúp AI dễ nhìn và xử lý và trả lời câu hỏi ổn định hơn HTML cú pháp phức tạp khiến AI dễ đưa ra câu trả lời bị thiếu cú pháp và lỗi cú pháp

## Bài 4 : Thiết kế Prompt tối ưu cho AI Assistant

## **Thiết kế Kiến trúc:** Bản Prompt viết bằng Markdown theo công thức 3 phần

- Ngữ cảnh \& Vai trò

Vai trò: Bạn đóng vai là một gia sư chuyên ngành Công nghệ Nông nghiệp, có khả năng biến các kiến thức kỹ thuật phức tạp,khó hiểu thành những ví dụ thực tế, gần gũi và dễ hiểu nhất.

Đối tượng người học: Sinh viên năm nhất mới bước chân vào đại học, chưa có nhiều kiến thức chuyên môn

Chủ đề: Giải thích khái niệm Mô hình IPO (Input - Process - Output) áp dụng cụ thể trong Trang trại thông minh (Smart Farm)
- Nhiệm vụ:
Giải thích rõ ý nghĩa của ba thành phần Input (Đầu vào), Process (Xử lý) và Output (Đầu ra) trong mô hình IPO.

- Nhiệm vụ: Giải thích rõ ý nghĩa của ba thành phần Input (Đầu vào), Process (Xử lý) và Output (Đầu ra) trong mô hình IPO.

- Yêu cầu: Lấy một ví dụ thực tế và trực quan về trang trại thông minh (ví dụ: Hệ thống tưới cây tự động hoặc điều hòa chuồng trại thông minh) để minh họa cho mô hình trên.

Trình bày bằng ngôn ngữ dễ hiểu, gần gũi, hạn chế tối đa các thuật ngữ chuyên ngành phức tạp, nếu bắt buộc phải dùng thuật ngữ tiếng Anh, phải có giải thích nghĩa tiếng Việt ngay lập tức.

Trình bày ngắn gọn, súc tích, độ dài câu trả lời không quá 300 từ để sinh viên dễ đọc và dễ ghi nhớ.

### AI_prompt
Sản phẩm:Mô Hình IPO Trong Trang Trại Thông Minh (Dành Cho Sinh Viên Năm Nhất)
--- 
## 1. Mô Hình IPO Là Gì?
Mô hình IPO chia bất kỳ hệ thống tự động nào thành 3 bước cơ bản: 
* **Input (Đầu vào):** Các cảm biến thu thập thông tin từ môi trường (giống như mắt, mũi, da của chúng ta). 
* **Process (Xử lý):** Bộ não trung tâm phân tích dữ liệu nhận được và đưa ra quyết định (giống như não bộ suy nghĩ). 
* **Output (Đầu ra):** Các thiết bị chấp hành thực hiện hành động dựa trên quyết định đó (giống như tay, chân hành động).
## 2. Ví Dụ Thực Tế: Hệ Thống Tưới Cây Tự Động
Để dễ hình dung, hãy xem một khu vườn thông minh tưới nước tự động hoạt động thế nào :
* **Input (Đầu vào):** 
* Cảm biến độ ẩm đất đo thấy đất đang bị khô (độ ẩm xuống dưới 30%). 
* **Process (Xử lý):** 
* Bộ điều khiển trung tâm (như chiếc "máy tính mini") nhận thông tin từ cảm biến, so sánh với mức cài đặt sẵn và ra lệnh: *"Đất khô rồi, cần bật bơm nước!"* 
* **Output (Đầu ra):** 
* Máy bơm nước tự động bật lên, phun nước cho cây đến khi độ ẩm vừa đủ thì tắt.
---
## Tổng Kết 
Chỉ đơn giản vậy thôi! Input là thu thập thông tin, Process là suy nghĩ tính toán, và Output là hành động thực tế. Mô hình này chính là gốc rễ của mọi công nghệ tự động hóa trong nông nghiệp hiện đại

## Bài 5 : Xây dựng bộ tài liệu kỹ thuật cho dự án Smart Farm
## **Phần 1. Phân tích:**
- **Input (Đầu vào):**
    
    - Cảm biến độ ẩm đất (kiểm tra độ ẩm trong chậu).
        
    - Cảm biến nhiệt độ và độ ẩm không khí.
        
    - Cảm biến ánh sáng .
        
    - Nút bấm thủ công trên hộp điều khiển.
        
- **Output (Đầu ra):**
    
    - Máy bơm nước mini 
        
    - Quạt thông gió (giảm nhiệt độ khi trời quá nóng).
        
    - Đèn báo hoặc màn hình nhỏ hiển thị trạng thái hệ thống.
### Chu kỳ xử lý lệnh tưới Lan của CPU (Fetch – Decode – Execute)

>  **Fetch (Lấy lệnh):** CPU đọc câu lệnh kiểm tra độ ẩm từ bộ nhớ chương trình. 
> **Decode (Giải mã):** CPU hiểu được ý nghĩa câu lệnh: Nếu độ ẩm dưới 40%, cần phải bật máy bơm nước. 
> **Execute (Thực thi):** CPU gửi tín hiệu điện ra chân điều khiển để bật rơ-le, kích hoạt máy bơm chạy tưới nước cho lan.
### Mô hình kim tự tháp DIKW (Chuyển hóa dữ liệu thành hành động tưới)

1. **Data (Dữ liệu thô):** Các con số rời rạc từ cảm biến trả về (`Nhiệt độ = 36°C`, `Độ ẩm đất = 28%`).
    
2. **Information (Thông tin có ý nghĩa):** Hệ thống gom nhóm lại và nhận diện: "Khu vực vườn lan đang bị khô hạn và nắng gắt vào buổi trưa".
    
3. **Knowledge (Tri thức/Hiểu biết):** Dựa vào đặc tính dữ liêệu của loại hoa lan đang trồng, nếu nhiệt độ trên 32°C và độ ẩm dưới 30% thì loại cây đó sẽ bị héo và cháy lá.
    
4. **Wisdom (Hành động khôn ngoan):** Ra quyết định tự động bật ngay hệ thống phun sương làm mát và máy bơm nước để bảo vệ vườn lan.
---
## Sơ đồ phối hợp phần cứng
* **Khối đầu vào (Cảm biến):**
* ├── `[ Cảm biến độ ẩm đất ]` ----\
* ├── `[ Cảm biến nhiệt độ/ẩm ]` ----+---> **[ Vi điều khiển trung tâm ]**
* └── `[ Cảm biến ánh sáng ]` -----/ │
                                     v
* **Khối đầu ra (Thiết bị chấp hành):** │ (Gửi lệnh kích hoạt)
* └── **[ Vi điều khiển trung tâm ]** ────────> `[ Mạch Rơ-le ]` ────────> `[ Máy bơm / Quạt ]` 
* (Hệ thống được cấp nguồn ổn định qua `[ Nguồn điện 5V/12V ]`)*

# README
### Phần 2:Triển khai
# 🚀 Tên Dự án: Smart-Farm Trang Trại Lan 
> *Mô tả:Hệ thống tự động hóa thông minh giúp chăm sóc hoa lan tối ưu, tiết kiệm nước và công sức cho người nông dân.
> * ![Sơ đồ tổng quan hệ thống Smart-Farm](https://rikkeiedu-storage.s3.ap-southeast-2.amazonaws.com/uploads/editor-images/1787648283613_687ec2e7-229c-4942-a347-080fae59560a.webp) ## ⚙️ Hướng dẫn cài đặt 
> * ```bash 
> * # Bước 1: Kết nối các cảm biến và thiết bị đầu ra vào bộ điều khiển trung tâm 
> * # Bước 2: Tải mã nguồn dự án về máy git clone [https://github.com](https://github.com) 
> * # Bước 3: Cài đặt các thư viện hỗ trợ cảm biến pip install -r requirements.txt 
> * # Bước 4: Khởi chạy chương trình điều khiển trang trại python main.py
---
## ✨ Tính năng

- [x] Tự động đo đạc độ ẩm đất và nhiệt độ không khí 24/7.
    
- [x] Tự động bật máy bơm khi đất khô và tắt khi đã đủ nước.
    
- [x] Cảnh báo bằng đèn khi môi trường quá nóng hoặc thiếu nước.
    
- [x] Điều khiển từ xa qua thiết bị điện thoại thông minh).
---
## Bảng thông số thiết bị

| **Tên thiết bị**       | **Chức năng chính**      | **Thông số hoạt động**          |
| ---------------------- | ------------------------ | ------------------------------- |
| **Cảm biến độ ẩm đất** | Đo lượng nước trong chậu | 0% - 100% (Tốt nhất: 40% - 70%) |
| **Cảm biến nhiệt độ**  | Đo nhiệt độ không khí    | -10°C đến 45°C                  |
| **Máy bơm nước**       | Cung cấp nước tưới       | lưu lượng 5L/phút               |
| **Vi điều khiển**      | Xử lý lệnh trung tâm     | RAM 512KB, Chip xử lý 32-bit    |

---
# Phần 3:Kiểm thử (Cập nhật mục Lưu ý khi RAM đầy)


## Lưu ý quan trọng khi vận hành & Xử lý sự cố RAM đầy 
* **Hiện tượng xảy ra:** Khi hệ thống chạy liên tục trong thời gian dài, các tệp nhật ký (ghi lại lịch sử nhiệt độ, độ ẩm, lịch sử tưới) sẽ tích tụ dần làm RAM bị đầy. Điều này sẽ khiến hệ thống bị đơ, phản hồi chậm,hoặc tự động khởi động lại. 
* **Cách xử lý an toàn:** 
  1. **Khởi động lại thiết bị (Restart):** Rút nguồn bộ điều khiển trung tâm trong vòng 5 giây rồi cắm lại để xóa sạch bộ nhớ đệm tạm thời. 
  2. **Xóa bớt nhật ký cũ:** Kết nối máy tính với bộ điều khiển hoặc bấm nút "Làm sạch bộ nhớ" trên giao diện để xóa các dữ liệu nhật ký cũ không còn cần thiết. 
  3. **Cài đặt giới hạn lưu trữ:** Nên chỉnh sửa cấu hình hệ thống chỉ lưu nhật ký trong vòng 7 ngày gần nhất, các dữ liệu cũ hơn sẽ tự động được xóa đi để tránh bị tràn bộ nhớ RAM trong tương lai.
## Bài 6 : Sự cố tài liệu dự án trên GitHub
## **Phần 1:Phân tích**
### 2 sai lầm  của Nam:
- Dùng định dạng văn bản có cấu trúc ẩn (Rich Text / .docx) cho hệ thống quản lý mã nguồn (Git) trong khi Git là công cụ quản lý văn bản thuần túy , không tối ưu cho docx/rtf
- Chủ quan về độ an toàn và cấu trúc "mong manh" của file nhị phân: vì file docx/rtf thực chất là một tệp nén (giống file zip) nên quá trình tải lên GitHub bị lỗi mạng giữa chừng và làm mất hoặc lệch **chỉ 1 byte dữ liệu**, cấu trúc bên trong sẽ bị phá vỡ
### Markdown lại an toàn và nhẹ hơn vì:
- Là văn bản thuần túy (Plain text) với vài ký cú pháp đơn giản như `#` để làm tiêu đề, `**...**` để in đậm khác so với docx hoặc rtf có nhiều mã ẩn (XML, định dạng phông chữ, màu sắc, hình ảnh...) và Git là công cụ sinh ra để quản lý văn bản thuần túy nên sẽ không tối ưu cho docx/rtf
- Khả năng chống chịu lỗi: nếu file Markdown bị lỗi mạng mất 1 byte, file chỉ bị mất vài ký tự hoặc một chữ cái, phần còn lại của văn bản vẫn đọc được bình thường, chứ không bị sập cả file như docx/rtf.
- GitHub tối ưu: vì là công cụ quản lý văn bản thuần túy nên trên Git vừa có thể xem trực tiếp trên Github khác docx/rtf sẽ hiện view raw và qua liên kết khác tốn thời gian. Và chỉnh sửa thì nhiều người có thể chỉnh sửa cùng lúc như làm trên gg docs

# Phần 2: greentech
# Dự án GreenTech: Giải pháp công nghệ xanh cho cộng đồng 
>## 1. Giới thiệu chung: GreenTech là dự án sinh viên tập trung phát triển các giải pháp công nghệ thân thiện với môi trường, giúp tối ưu hóa việc quản lý năng lượng và giảm thiểu rác thải điện tử tại các trường đại học. 
>## 2. Các tính năng chính: 
>* **Theo dõi tiêu thụ điện năng:** Giám sát thời gian thực lượng điện tiêu thụ của các phòng học. 
>* **Cảnh báo rác thải thông minh:** hệ thống hỗ trợ phân loại và báo cáo tình trạng đầy của thùng rác. 
>* **Báo cáo tác động môi trường:** Tổng hợp số liệu và trực quan hóa lượng khí thải carbon được cắt giảm.