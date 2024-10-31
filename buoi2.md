# Tìm hiểu về OBJECT

## 1. Object
#### 1.1 Object là gì?
Class là một nhóm các đối tượng có đặc điểm chung. 
Ví dụ: Một con vật: bao gồm
- Đặc điểm: có lông, không lông, kích thước,...
- Hành vi: Ngủ, săn mồi, ăn, ...
__Object__ là một thể hiện rõ ràng cụ thể của một lớp.
Ví dụ: con ngựa: bao gồm
- Đặc điểm: có lông, to, màu trắng,...
- Hành vi: Chạy, ăn cỏ, ...
thì *con ngựa là một object của class con vật.*
Trừ các kiểu dữ liệu nguyên thủy
#### 1.2 Object được lưu thế nào trong Java?
Trong Java, khi một đối tượng được tạo ra, nó sẽ được lưu trữ trong bộ nhớ `heap,` và Java sử dụng cơ chế `tham chiếu` để quản lý đối tượng này.
Các đối tượng sẽ được lưu trữ trên bộ nhớ `heap`. Khi đối tượng được tạo, Java sẽ tọa một biến `tham chieeus` trên bộ nhớ `stack` để lưu địa chỉ đối tượng đó trên `heap`
_Ví Dụ_
``` Java
Person person = new Person();
```
`person` là một biến tham chiếu lưu trữ địa chỉ của đối tượng `Person`
## 2.Wrapper Class
Wrapper Class cung cấp một cách để sử dụng các kiểu dữ liệu nguyên thủy như các Object. Ví dụ: 
| Primitive Data Type | Wrapper Class |
|---------------------|---------------|
| byte                | Byte          |
| short               | Short         |
| int                 | Integer       |
| long                | Long          |
| float               | Float         |
| double              | Double        |
| boolean             | Boolean       |
| char                | Character     |

Khi làm việc với các Collection object, như ArrayList (các danh sách mà chỉ để lưu trữ các đối tượng) mà không thể sử dụng các kiểu dữ liệu nguyên thủy, khi mình cần giá trị null, phương thức lớp Object mà warper class cung cấp mà kiểu dữ liệu nguyên thủy không có.
Wrapper Class lưu trữ các biến nguyên thủy tượng tự với cách lưu object, là lưu địa chỉ của object.
 _String không phải Wrapper class_
#### 2.1 Một số phương thức của Wrapper Class
- __Khởi tạo__
Sử dụng valueOf, có thể truyền vào một giá trị kiểu giá trị nguyên thủy hoặc một xâu có thể chuyển thành dạng giá trị nguyên thủy cần nhập. Nếu xâu truyền vào giá trị không hợp lệ với kiểu dữ liệu sẽ báo lỗi.
``` Java
Integer a = Integer.valueOf(42); // Tạo từ giá trị nguyên thủy
Integer b = Integer.valueOf("42"); // Tạo từ chuỗi
```
- __TypeValue()__
Trả về giá trị nguyên thủy tương ứng đối với Warpper class
```Java
int k = a.intValue(); // 42
```
Nếu biến chưa nhập gì thì sẽ trả về giá trị mặc định là `null`.
- __equals()__
Khi các đối tượng được so sánh với nhau bằng `==` thì sẽ giống như so sánh địa chỉ của 2 đối tượng. Vì vậy để so sánh được giá trị của 2 đối tượng Warpper ta sử dụng `equal()`.
Trả về giá trị True or False
``` Java
Integer c = Integer.valueOf(42); // 
boolean d = a.equals(c); // true
```
#### 2.2 Auto Boxing và Auto Unboxing
Điều này giúp đơn giản hóa mã và làm cho việc xử lý các kiểu dữ liệu nguyên thủy.
- __Auto-boxing__ là quá trình chuyển đổi từ kiểu dữ liệu nguyên thuỷ thành dạng object.
```java
int num = 10;
Integer boxedNum = num; // Auto-boxing: int -> Integer
```
_Sử dụng phổ biến:_ Khi thêm một giá trị nguyên thủy vào một Collection như ArrayList. 
- __Auto-unboxing__ là quá trình chuyển đổi từ kiểu dữ liệu lưu dạng object thành dữ liệu nguyên thuỷ.
```java
Integer boxedNum = 20;
int num = boxedNum; // Auto-unboxing: Integer -> int
```
_Sử dụng phổ biến:_ khi thực hiện phép tính các đối tượng kiểu nguyên thủy hoặc so sánh các giá trị.
__Lưu ý:__
- Khi sử dụng và so sánh các đối tượng có thể dây ra lỗi khi sử dụng toán tử `==`.
```java
Integer a=1;
Integer b=1;
Integer c=128;
Integer d=128;
System.out.println(a == b); // true
System.out.println(c == d); // false
```
- Quá trình boxing và unboxing tạo ra đối tượng mới mỗi khi chuyển đổi làm tốn bộ nhớ và tăng thời gian chạy nếu phải sử dụng vòng lặp nhiều lần.
- Khi unboxing một đối tượng có giá trị `null` thì Java sẽ báo lỗi và không chạy được chương trình.
``` Java
Integer boxedNum = null;
int num = boxedNum; // Lỗi 
```
## 3.String và String Builder trong Java
#### 3.1 String
String trong Java là immutable (không thể thay đổi). Tức là khi bạn thay đổi 1 String Object trong Java thì 1 String object được tạo mới hoàn toàn mỗi lần thay đổi. 
Sử dụng khi bạn cần chuỗi cố định không thay đổi hoặc xử lý chuỗi ít thay đổi.
``` Java
String s1 = "Xin chao cac ban!"; // cách 1
String s2 = new String("HẾ nhố các bạn =))"); // cách 2
s1 = s1 + " Lêu lêu"; // Một String mới được tạo
```
Sự khác nhau giữa hai cách khai báo: 
- Cách 1: 1 String Object mới được tạo trong bộ nhớ heap
- Cách 2: Nếu đối tượng này tồn tại trong bộ nhớ heap rồi thì dùng lại. 
##### Một số phương thức 
- __substring()__
Trả về một chuỗi con (substring) từ vị trí `beginIndex` đến hết chuỗi hoặc đến vị trí `endIndex - 1`.
``` java
String str = "Hello World";
String subStr1 = str.substring(6);         // "World"
String subStr2 = str.substring(0, 5);      // "Hello"
```
- __charAt()__
Trả về ký tự tại vị trí `index` trong chuỗi. 
``` java
String str = "Hello";
char ch = str.charAt(1);                  // 'e'
```
- __length()__
Trả về độ dài chuỗi 
```java
String str = "Hello";
int len = str.length();                  // 5
```
- __So sánh chuỗi__
`equals()` So sánh chuỗi hiện tại với chuỗi khác.
`equalsIgnoreCase` So sánh mà không phân biệt hoa thường.
```java
String str1 = "Hello";
String str2 = "hello";
boolean ss1 = str1.equals(str2);       // false
boolean ss2 = str1.equalsIgnoreCase (str2); // true
```
- __Nối chuỗi__ 
`concat()` nối chuỗi hiện tại với một chuỗi mới 
```java
String str1 = "Hello";
String str2 = " World";
String result = str1.concat(str2);    // "Hello World"
```
- __Replace()__
Thay thế toàn bộ ký tự hoặc chuỗi con bằng kí tự mới hoặc chuỗi con mới.
``` java
String str = "Hello World";
String replacedStr1 = str.replace('o', 'a'); // "Hella Warld"
String replacedStr2 = str.replace("World", "Java");// "Hello Java"
```
- __trim()__
Xóa các khoảng trắng ở đầu và ở cuối 
``` java 
String str = "   Hello World   ";
String trimmedStr = str.trim();    // "Hello World"
```
- __split()__ 
Tách chuỗi thành các chuỗi con với phân cách, gần giống stringstream
``` java 
String str = "Hello,World,Java";
String[] parts = str.split(","); // ["Hello", "World", "Java"]
```
- __Chuyển in hoa và in thường__ 
`toUpperCase()` chuyển chuỗi hiện tại thành in hoa 
`toLowerCase()` Chuyển chuỗi hiện tại thành in thường
``` java
String str = "Hello World";
String upperStr = str.toUpperCase();   // "HELLO WORLD"
String lowerStr = str.toLowerCase();   // "hello world"
```
___Tổng hợp:___
| Phương thức        | Công dụng                                     |
|--------------------|-----------------------------------------------|
| `substring()`      | Lấy chuỗi con                                 |
| `charAt()`         | Lấy ký tự tại vị trí chỉ định                 |
| `length()`         | Trả về độ dài của chuỗi                       |
| `equals()`         | So sánh hai chuỗi                             |
| `concat()`         | Nối hai chuỗi                                 |
| `replace()`        | Thay thế ký tự hoặc chuỗi con                 |
| `trim()`           | Xóa khoảng trắng ở đầu và cuối chuỗi         |
| `split()`          | Tách chuỗi thành mảng dựa trên ký tự phân tách|
| `toUpperCase()`    | Chuyển thành chữ in hoa                       |
| `toLowerCase()`    | Chuyển thành chữ in thường                    |
#### 3.2 String Builder 
String builder là một class trong Java, nó được sử dụng để lưu trữ một chuỗi các ký tự. String Builder ở dạng mutable, tức là có thể thay đổi được. Vì vậy khi ta thay đổi giá trị của String Builder không tạo ra một String Builder mới mà chỉ thay đổi giá trị của nó.
```java
StringBuilder sb = new StringBuilder("Hello");
sb.append(" World"); // Chuỗi gốc được thay đổi trực tiếp
System.out.println(sb.toString()); // In ra "Hello World"
```
Sử dụng khi thao tác nhiều hay chuỗi quá dài vì nhanh hơn và tiết kiệm bộ nhớ hơn rất nhiều.
##### Một số phương thức 

| Phương thức                          | Công dụng                                               |
|--------------------------------------|--------------------------------------------------------|
| `insert(int index, String str)`     | Thêm chuỗi `str` tại vị trí chỉ định `index`        |
| `delete(int start, int end)`         | Xóa các ký tự trong khoảng từ `start` đến `end - 1` |
| `reverse()`                           | Đảo ngược chuỗi                                       |
| `append(String str)`                 | Thêm chuỗi `str` vào cuối                            |
| `capacity()`                          | Trả về dung lượng hiện tại của đối tượng             |
| `setLength(int newLength)`           | Thiết lập độ dài của chuỗi                            |
| `substring(int start, int end)`      | Lấy chuỗi con từ vị trí `start` đến `end - 1`       |
| `charAt(int index)`                  | Lấy ký tự tại vị trí chỉ định                         |
| `toString()`                          | Chuyển đổi thành chuỗi                                |
## 4. Phương thức equals() và hashCode() 
Lớp Object định nghĩa hai phương thức equal() và hashCode().
#### 4.1 Phương thức equals() 
Sự khác nhau giữa equals() và == đã được nói ở trên.
Thường sẽ sử dụng ghi đè phương thức equal() trong lớp để định nghĩa tiêu chí so sánh các thuộc tính của đối tượng.
Trả về True or False
Ví dụ:
``` java
public class Person {
    private String name;
    private int age;

    public boolean equals(Object obj) {
        Person other = (Person) obj; // Ép kiểu đối tượng
        // So sánh thuộc tính name và age
        return this.name.equals(other.name) && this.age == other.age;
    }
}
```
#### 4.2 Phương thức hashCode()
Định nghĩa phương thức:
```java
public native int hashCode();
```
Phương thức `hashCode()` được sử dụng để trả về một giá trị mã băm cho đối tượng. Mã băm là một số nguyên, và nó được sử dụng trong cấu trung dữ liệu như `HashMap`, `HashSet`, `Hashtable` để xác định và lưu trữ đối tượng là "nhóm". Mỗi nhóm sẽ được liên kết với một mã băm và nhóm chỉ chứa các đối tượng có mã băm giống hệt nhau.
Sự sắp xếp giúp tìm kiếm và truy vấn một phần tử nhanh hơn.

__Lưu ý:__
- Hai đối tượng bằng nhau mã băm của chúng bằng nhau 
- Hai đối tượng không bằng nhau, không có ràng buộc về mã băm 
- Hai đối tượng mã băm giống nhau, thì không có ràng buộc về sự bằng nhau của chúng. 
- Hai đối tượng mã băm khác nhau thì không được bằng nhau
- Khi phương thức` equals()` được ghi đè, phương thức `hashCode()` cũng phải được ghi đè.
## 5. Cách Java truyền tham số _ Pass-by-value
#### 5.1 Pass-by-value
Khi một tham số được truyền vào phương thức, Java sẽ tạo một bản sao của tham số đó. Khi thay đổi giá trị của tham số trong phương thức thì sẽ không ảnh hưởng đến giá trị của tham số gốc truyền vào phương thức. Áp dụng được cho cả kiểu nguyên thủy và đối tượng 
__Ví dụ:__
``` java
class Person {
    String name;
    Person(String name) {
        this.name = name;
    }
}

public class Main {
    public static void main(String[] args) {
        int num = 10;
        khac(num);
        System.out.println("Num: " + num); // Kết quả: 10
        Person person = new Person("Alice");
        khac1(person);
        System.out.println("Person : " + person.name); // Kết quả: Bob
    }
    public static void khac(int number) {
        number = 20; // Chỉ thay đổi bản sao của số
    }
    public static void khac1(Person p) {
        p.name = "Bob"; // Thay đổi thuộc tính của đối tượng
    }
}
```
__Lưu ý:__
- Giá trị của các kiểu nguyên thủy được sao chép.
- Đối với đối tượng, địa chỉ tham chiếu đến đối tượng được sao chép, cho phép bạn thay đổi nội dung của đối tượng, nhưng không thể thay đổi tham chiếu của nó.
#### 5.2 Tại sao pass-by-value mà String lại thay đổi được?
Vì String là một class, được lưu trữ như một Object, khi truyền tham chiếu sẽ truyền vào địa chỉ của đối tượng đó, nên có thể thay đổi được. 
## 6. Garbage collector
Garbage collection  trong máy ảo Java (JVM) là quá trình xác định và loại bỏ các Object không được sử dụng khỏi bộ nhớ Heap. Không gian trống này sẽ được cấp phát cho những Object mới. 
Quá trình này gồm 3 bước cơ bản: 
1. __Marking:__ đánh dấu những object còn sử dụng và object không còn sử dụng
![](https://images.viblo.asia/full/70713868-22b1-40c9-853b-4bade54c0c5d.png)

2. __Normal deleting: __Trình Garbage Collector sẽ xóa cá Object không còn sử dụng.

![](https://images.viblo.asia/full/24d99c89-1631-4c33-9e88-6b22f37c8a1f.png)

3. __Gom:__ Sau khi nhưng object không còn suer dụng được xóa, object còn dử dụng sẽ được gom lại. Làm tăng bộ nhớ trống để cấp phát cho object mới.

![](https://images.viblo.asia/e8667a54-e7fa-4521-9b5c-536085d8f95b.png)

