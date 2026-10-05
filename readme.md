Phân tích lỗi

Dòng sai:

js
const basePrice = bookingReservation.priceKey;

Nguyên nhân kỹ thuật:

Dot Notation (obj.priceKey) luôn hiểu phần sau dấu chấm là tên thuộc tính viết sẵn bằng chữ. JavaScript tìm thuộc tính có tên đúng là "priceKey", không đọc giá trị của biến priceKey.
Đối tượng bookingReservation không có thuộc tính "priceKey", nên kết quả là undefined.
Bracket Notation (obj[priceKey]) thì tính giá trị biểu thức trong ngoặc trước ("roomPrice"), rồi mới dùng chuỗi đó làm tên thuộc tính.

Hệ quả nghiệp vụ (chuỗi lỗi dây chuyền):

basePrice = undefined
Nếu nhận phòng trước 12h: surcharge = undefined * 0.3 = NaN
totalAmount = undefined + NaN = NaN
Hóa đơn của khách hiển thị NaN.
Bảng Test Cases
Trường hợp kiểm thử	Dữ liệu đầu vào	Kết quả sai thực tế	Kết quả đúng mong đợi
TC1: Nhận phòng sớm (có phụ thu 30%)	roomPrice: 1500000, checkInHour: 9, priceKey = "roomPrice"	Phụ thu: NaN; Tổng tiền: NaN	Phụ thu: 450000; Tổng tiền: 1950000
TC2: Nhận phòng đúng giờ (không phụ thu)	roomPrice: 1500000, checkInHour: 14, priceKey = "roomPrice"	Phụ thu: undefined; Tổng tiền: NaN (do undefined + 0)	Phụ thu: 0; Tổng tiền: 1500000