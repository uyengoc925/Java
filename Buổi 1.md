I. Tổng quan về java
    <!-- 1. JAVA là gì? -->
    <!-- 2. lí do ra đời java -->
    <!-- 3. cách hoạt động, điều gì xảy ra khi chạy code java(.java)` -->
   <!--  4. Cấu trúc một chương trình Java -->
   <!--  5. Package là gì  -->
<!-- II. syntax cơ bản
    1. khai báo biến nguyên thủy 
    2. làm quen với vòng lặp
    3. Câu lệnh rẽ nhánh 
    4. Mảng trong java  -->
III . tổng quan về Class và object 
    các từ khóa về <!-- this, construct -->, access, modifier, getter, setter, từ khóa static

# WELCOME TO JAVA 

## I. TỔNG QUAN VỀ JAVA
****
### 1. Ngôn ngữ Java là gì?
Java là một ngôn ngữ lập trình được sử dụng rộng rãi để viết mã các ứng dụng web. Java là một ngôn ngữ nền tảng, hướng đến đối tượng, lấy mạng làm trung tâm và có thể sử dụng như một nền tảng. Java là một ngôn ngữ có thể chạy trên nhiều nền tảng, nhiều hệ điều hành với tính an toàn và bảo mật.
### 2. Lí do ra đời Java
- Tối ưu hóa quá trình viết mã, viết một lần có thể chạy nhiều môi trường khác nhau.
- Mục đích tạo ra một ngôn ngữ lập trình mạnh mẽ, gần gũi với người dùng.
- Tăng cường bảo mật cho lập trình hướng đối tượng.
### 3. Cách hoạt động của Java
Java là ngôn ngữ với câu nói nổi tiếng **"Write-one/Run-anywhew"** là viết code một lần mà chạy trên tất cả mọi nơi, mọi thiết bị như: điện thoại, máy tính, laptop, máy tính bảng,...
Để chạy được trên đa nền tảng thì cách hoạt động của Java là:
![](https://phamanhduc.com/wp-content/uploads/2024/04/how-java-works.png)
1. File source code chạy bằng trình biên dịch. Khi chạy bằng trình biên dịch sẽ kiểm tra lỗi nếu không có lỗi sẽ đến bước tiếp theo.
2. Compiler tạo ra một file mới mã hóa thành **Javabytecode** mà bất kì thiết bị nào chạy Java đều có khả năng thông dịch.
(Thông dịch là dịch từng dòng code và chạy, Biên dịch là dịch tất cả code rồi chạy)
3. Khi chạy file mã hóa trong thiết bị sẽ cần hỗ trợ của máy ảo Java, giúp đọc và chạy file bytecode.
### 4. Cấu trúc của một chương trình Java
Cấu trúc của một chương trình Java bao gồm:
` `
``` CPP
// Khai báo một package 
package <package_name>;

import <other_package>;

public class ClassName {

  <Variables (also known as fields)>;

  <constructor method(s)>;

  <other methods>;
}

```
- ***Package:*** Mô tả không gian có tên chứa các lớp Java, có thể xem package như một thư mục, còn class là các file trực thuộc thư mục. Giúp cho việc đọc code dễ dàng, hay dễ dàng bảo trì.
- ***Class:*** Lớp trong Java. Tên lớp truong java có từ khóa pbulic hay private xác định phạm vi truy cập của lớp.
- ***Variables:*** Biến, chứa thông tin cụ thể liên quan đến đối tượng.
- ***Constructor:*** Phương thức khởi tạo, hình dạng của đối tượng được thể hiện tạo ra sẽ phụ thuộc vào phương thức này.
- ***Import:*** Để sử dụng lớp trong package thì ta phải import để nạp lớp trong package đó.
### 5. Package 
Package nó cung cấp các chức năng bảo vệ và truy và truy cập quản lý không gian. Giúp phân hoạch không gian tên lớp giao diện thành những vùng dễ quản lý hơn.
##### Các thao tác trên package:
- Kỹ thuật đặt tên(Sử dụng các từ viết thường, không bắt đầu bằng *Java* hoặc *Javax*, không được bắt đầu bằng số hoặc dấu nối "- ").
- Kỹ thuật truy xuất dữ liệu 
##### Đặc điểm
- Một package có thể chứa nhiều package con
- Không có hai package cùng tên trong một package
- Java có 2 loại gói:
    - Gói được định nghĩa trước 
    - Gói được định nghĩa bởi người dùng
##### Các bước định nghĩa gói:
- Đặt tên pacakge 
- Tạo thư mục cùng tên với package: Java sử dụng hệ thuống thư mục để lưu trữ package 
## II. Syntax cơ bản
### 1.  Khai báo biến nguyên thủy 
1. Biến là gì?
Biến đơn giản là một vùng chứa giá trị, có thể sử dụng nhiều nơi trong chương trình. Giá trị của biến có thể thay đổi được.
2. Quy tắc đặt tên biến
- Tên biến bắt đầu bằng một ***chữ cái, ký hiệu \$*** hoặc ***ký tự gạch dưới \-***; và sau đó có thể chỉ các chữ cái, chữ số, ký hiệu \$, gạch dưới  \_;
- Khai báo biến: chỉ ra định dạng kiểu ***dữ liệu \+ tên biến***
3. Kiểu dữ liệu 
    1. Kiểu dữ liệu nguyên thủy
    Các kiểu dữ liệu nguyên thủy: boolean, char, byte, short, int, long, float, double.
    
    2. Kiêu dữ liệu đối tượng 
    Các kiểu dữ liệu đối tượng: String, Array, Double, ....
### 2. Làm quen với vòng lặp 
1. ***Vòng lặp for*** 
Vòng lặp for đơn giản giống như trong C/C++. Chúng ta có thể khởi tạo biến, kiểm tra điều kiện và tăng/giảm giá trị của biến.
```CPP
for (khoi_tao_bien ; check_dieu_kien ; tang/giam_bien) {  
    // Khối lệnh được thực thi
}  
```
***vòng lặp for gán nhãn***
Chúng ta có để đặt tên cho mỗi vòng lặp for bằng cách gán nhãn trước vòng lặp for. Điều này rất hữu dụng khi chúng ta muốn thoát/tiếp tục(break/continues) chạy vòng lặp for.
- Cú pháp 
```Java
ten_nhan:
for (khoi_tao_bien ; check_dieu_kien ; tang/giam_bien) {  
    // Khối lệnh được thực thi
}
```
- Ví dụ:
```java
public class LabeledForExample {
    public static void main(String[] args) {
        aa: for (int i = 1; i <= 3; i++) {
            bb: for (int j = 1; j <= 3; j++) {
                if (i == 2 && j == 2) {
                    break aa;
                }
                System.out.println(i + " " + j);
            }
        }
    }
}
``` 
2. ***Vòng lặp while***
Vòng lặp while được sử dụng để lặp một phần của chương trình mà không biết trước số lần sẽ in ra. 
```java
while (condition) {
    //code
}
```
3. ***Vòng lặp do while***
Tương tự vòng lặp while và for thì do while cũng tương tự như trong C và CPP.
``` java
do { 
    // code 
} while(condition);
```
### 3. Câu lệnh rẽ nhánh 
1. __Câu lệnh if-else__

```java
if (condition) {
    // khối lệnh này được thực thi
} 
else if(){
    // khối lệnh này được thực thi
}
else {
    // khối lệnh này được thực thi
}
```
2. __Câu lệnh Switch case__
Thực thi 1 hoặc nhiều khối lệnh từ nhiều điều kiện.
```java
switch (bieu_thuc) {    
case gia_tri_1:
    // Khối lệnh 1
    break;  //tùy chọn
case gia_tri_2:    
    // Khối lệnh 2
    break;  //tùy chọn
......    
case gia_tri_n:    
    // Khối lệnh n
    break;  //tùy chọn    
default:     
    // Khối lệnh này được thực thi 
    // nếu tất cả các điều kiện trên không thỏa mãn 
}   
```
### 4. Mảng trong java
Sử dụng mảng trong java tương tự với sử dụng mảng trong C
```java
int [] a; // khai báo bảng 
int d []; // khai báo mảng
// khai báo và khởi tạo mảng 2 chiều 
int[][] c = {{1, 2}, { 3, 4}, { 3, 4}, { 3, 4}};
// khởi tạo mảng 2 chiều bằng vòng lặp for
int[][] b = new int[4][2];
for (int i = 0; i < 4; i++) {
    for (int j = 0; j < 2; j++) {
        b[i] = scanner.nextInt(); // nhập mảng từ bàn phím 
    }
}
// -> in ra mảng 

```
## III. Tổng quan về Class và Opject 

1. __Đối tượng__
Một đối tượng trong thực tế được hiểu là một trạng thái hành vi
Đặc điểm: 
- Trạng thái: địa diện cho dữ liệu, giá trị của một đối tượng 
- Hành vi: Đại diện cho chức năng của một đối tượng
- Danh tính: Danh tính của một đối tượng thường được cài đặt thông qua một ID duy nhất. ID này được ẩn đối với user bên ngoài. Tuy nhiên nó được sử dụng trong nội bộ máy ảo JVM để định danh từng đối tượng.
2. __Lớp__
Class là một cấu trúc có nhiều thành phần khai báo sẵn để có thể gọi ra dùng hoặc xử lý và Class thì có thể nhiều đối tượng tỏng 1 class.
3. __This__
Dùng để tham chiếu đến đối tượng hiện tại của class. Dùng để phân biệt đâu là thuộc tính, đâu là biến khi chúng trùng tên với nhau. 
cấu trúc:
```java

```
4. __Constructor__ 
Là một phương thức đặc biệt sử dụng để khởi tạo đối tượng.
Constructor cùng tên với class, không có kiểu trả về 
- Có hai kiểu constructor:
    - Constructor Tham số  (không có tham số truyền vào)
    ```java
    <class_name>() {
        // code
    }  
    ```
    - Constructor mặc định: Nếu không có constructor trong một lớp, trình biên dịch sẽ tự động tạo một constructor mặc định trong lớp đó.
5. __Accesss Modifer__
Access Modifer xác định phạm vi có thể truy cập của biến, phương thức, constructor hoặc lớp.
Có 4 phạm vi truy cập: 
    - Private: truy cập trong phạm vi lớp.
    - Default: truy cập trong cùng package.
    - Protected: truy cập bên trong package và bên ngoài package nhưng phải kế thừa.
    - Public: được truy cập ở mọi nơi.
6. __Getter và Setter__
Getter và Setter là 2 phương thức sử dụng để cập nhập hoặc lấy ra giá trị thuộc tính, đặc biệt dành cho thuộc tính ở phạm vi private.
Cú pháp:
```java
//setter
public void set<tên thuộc tính> (<tham số giá trị mới>) {
     return this. <tên thuộc tính> = <tham số giá trị mới>;
}
//getter
public <kiểu dữ liệu thuộc tính> get<tên thuộc tính> () {
      return this. <tên thuộc tính>;
}
```
7. __Biến Satic__
Static Variable là biến được khai báo trong một class, nhưng bên ngoài các phương thức, constructor hoặc khối lệnh. Biến này có thể được truy cập bởi bất kỳ phương thức, constructor hoặc khối lệnh nào của class đó. 
__Khởi tạo một lần duy nhất:__ Biến static chỉ được khởi tạo một lần duy nhất khi lớp được nạp vào bộ nhớ. Vì vậy, nó tiết kiệm bộ nhớ khi có nhiều đối tượng của lớp đó.
```Java
class Counter {
    static int count = 0; // Biến static

    Counter() {
        count++; // Tăng giá trị biến static
        System.out.println(count);
    }
}
// mỗi khi khởi tạo một giá trị mới thì biến count sẽ tăng lên 
public class Main {
    public static void main(String[] args) {
        Counter c1 = new Counter(); 
        Counter c2 = new Counter();
        Counter c3 = new Counter(); 
    }
}
```
