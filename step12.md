# Make a Search Bookmarkable

Hướng dẫn tìm kiếm employees trong table employees trên URL

Để search có thể bookmarkable, tôi sẽ thêm `#/employees/overview?search=mySearchQueryString`

ở file manifest.json
![thêm key](image.png)

Thêm tham số `:?query:` vào tuyến overview của employees

Muốn xử lý option query parameter từ employeesOverview route trong EmployeesOverviewContent controller. Nếu sẵn query, kết quả từ `oEvent.getParameter("arguments")` sẽ chưa property `?query` với tất cả các tham số URL chỉ định.
Nếu không có query parameter nào được xác định , chúng tôi luôn khởi tạo query và lưu nó thành `this.oRouterArgs['?query']`.Nếu có search query từ search key, chúng tôi sẽ tiếp tục gọi.

Sau khi lưu trữ đối số object trong controller, chúng ta sử dụng các đối số hiện tại khi gọi `NavTo()` , trong quá trình event handler `onSearchEmployees` và chuyển các đối số có cụm search được update .Giá trị tìm kiếm được lưu trữ trong this.\_oRouterArgs["?query"].search cùng với các query parameter khác và nó được chuyển trực tiếp đến bộ định tuyến một lần nữa

```js
webapp/index.html#/employees/overview

webapp/index.html#/employees/overview?search=

webapp/index.html#/employees/overview?search=an
```
