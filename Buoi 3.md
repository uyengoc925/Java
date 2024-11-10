<!-- MỌI THỨ ĐỀU LÀ ĐỐI TƯỢNG -->
<!-- Tính đóng gói ? -->
<!-- Tính kế thừa (đặc điểm, constructor, variable hiding, đa kế thừa, ...) ? -->
<!-- Upcasting và Downcasting. -->
<!-- Class Object -->
<!-- Tính đa hình ? -->
Đa hình compile time và runtime
Phân biệt Overload và Override.

# Mọi thứ đều là đối tượng
## I. Tính đóng gói
### 1. Tính đóng gói là gì?
Tính đóng gói  là một trong những nguyên tắc quan trọng trong Lập Trình Hướng Đối Tượng (OOP). Nguyên tắc này đề cập đến việc che giấu thông tin và hành vi bên trong đối tượng, chỉ tiết lộ những gì cần thiết và quy định cách truy cập thông qua các phương thức công khai.
### 2. Ví dụ
```Java
class NhanVien {
    // Thuộc tính được đặt là private để bảo vệ dữ liệu
    private String ten;
    private double luong;
    public void setTen(String ten) {
        this.ten = ten;
    }
    public String getTen() {
        return ten;
    }
    public void setLuong(double luong) {
        if (luong > 0) {
            this.luong = luong;
        } else {
            System.out.println("Lương phải là một số dương.");
        }
    }
    public double getLuong() {
        return luong;
    }
}

public class Main {
    public static void main(String[] args) {
        NhanVien nv = new NhanVien();
        nv.setTen("Nguyễn Văn A");
        nv.setLuong(5000);

        System.out.println("Tên nhân viên: " + nv.getTen());
        System.out.println("Lương nhân viên: " + nv.getLuong());
    }
}
```
__Nhận xét:__
Hai thuộc tính `ten`, `luong` của lớp `NhanVien` được khai báo là `private`. Tức là ta không thể thay đổi thông trực tiếp mà phải thông qua các phuong thức `get`, `set`. 
Trong `setLuong`, có kiểm tra lương phải là một số dương mới cho nhập. Điều này giúp bảo vệ dữ liệu của nhân viên tránh đặt giá trị không hợp lệ.
### 3. Ý nghĩa
1. __Bảo mật dữ liệu:__ Giúp bảo vệ dữ liệu bên trong đối tượng, tránh việc truy cập hoặc thay đổi từ bên ngoài mà không qua các quy tắc đã được đặt ra.
2. __Dễ bảo trì và thay đổi:__ Khi các chi tiết nội bộ được ẩn đi, việc thay đổi bên trong đối tượng sẽ ít ảnh hưởng đến mã nguồn bên ngoài sử dụng đối tượng đó.
3. __Tăng tính rõ ràng và dễ hiểu:__ Chỉ những phương thức nào cần thiết mới được công khai (public), những chi tiết không cần thiết sẽ được giữ kín (private hoặc protected), giúp giảm sự phức tạp của chương trình.
___Kết Luận:___ 
Để áp dụng tính đóng gói ta có thể sử dụng các mức truy cập như `private`, `protected`, `public` hoặc cung cấp các phương thức `getters` và `seters` để thao tác với dữ liệu bên trong tránh mất dữ liệu và dễ bảo trì. 
## II. Tính kế thừa

Tính kế thừa là một trong những đặc điểm quan trọng của lập trình hướng đối tượng (OOP), cho phép một lớp mới kế thừa các thuộc tính và phương thức của một lớp hiện có. Lớp mới này được gọi là lớp con, trong khi lớp hiện có gọi là lớp cha.

### 1.Ví dụ

```Java
public class Vehicle {
    protected String model = "Ford";
    protected String color = "Red";

    public void run() {
        System.out.println("Tuut, tuut!");
    }
}

public class Car extends Vehicle {
    private String modelName = "Hello";    // Car attribute

    public static void main(String[] args) {
        Car myCar = new Car();
        myCar.run();
        System.out.println(myCar.color + " " + myCar.model + " " + myCar.modelName);
    }
}
// Tuut, tuut!
// Red Ford Hello

```
Lớp cha `Vehicle` có 2 thuộc tính là `model` và `color`. Lớp con `Car` kế thừa từ lớp cha, nghĩa là sẽ có các thuộc tính và phương thức của `Vehicle`. Ngoài ra `Car` còn có thuộc tính đặc trưng riêng.
### 2. Đặc điểm 
1. Tái sử dụng: Kế thừa cho phép sử dụng lai các thuộc tính và phương thức của lớp cha mà không cần định nghĩa lại.
2. Mở rộng tính năng: Có thể tạo một đối tượng mới kế thừa các tính năng của đối tượng cũ và thêm các tính năng mới
3. Không hỗ trợ đa kế thừa với các lớp trong java.
4. Quan hệ này là quan hệ một chiều, lớp con có phương thức của lớp cha, nhưng lớp cha thì không.
### 3. Từ khóa Super
- Chỉ sử dụng trong lớp con.
- Sử dụng để phân biệt thành phần cùng tên của lớp cha và lớp con
- Để gọi hàm tạo của lớp cha từ lớp con.
- `super()` để gọi contrucstor, `super.<tên phuong thức>()` gọi phương thức , `super.<tên thuộc tính>` gọi thuộc tính ở lớp cha
__Ví dụ:__
```Java
class Animal {
    protected String name;
    public void sound() {
        System.out.println("Animal sound");
    }
}
class Dog extends Animal {
    private String breed;
    public void sound() {
        super.sound();  // phương thức lớp cha
        System.out.println("Dog barks");
    }
    public void display() {
        super.name = "Buddy";  // thuộc tính lớp cha
        System.out.println("Name: " + super.name + ", Breed: " + breed);
    }

public class Main {
    public static void main(String[] args) {
        Dog myDog = new Dog();
        myDog.sound();
        myDog.display();
    }
}
// Animal sound
// Dog barks
// Name: Buddy, Breed: null

```
### 4. Contrustor trong kế thừa
Phương thức khởi tạo mặc định của lớp cha luôn luôn được gọi mỗi khi có 1 đối tượng thuộc lớp con khởi tạo. Và được gọi trước phương thức khởi tạo của lớp con.
- Cách gọi contructor của lớp cha: `super()` nếu bạn gọi không tường mình thì sẽ tự động gọi contructor mặc định của lớp cha.
- Lớp con có thể có nhiều constructor

``` Java
class Animal {
    public Animal(){
        System.out.println("Mac dinh");
    }
    public Animal(String name) {
        System.out.println("Animal constructor called for " + name);
    }
}

class Dog extends Animal {
    public Dog(String name) {
        System.out.println("Dog constructor called for " + name);
    }
}

public class Main {
    public static void main(String[] args) {
        Dog myDog = new Dog("Buddy");
    }
}
class Animal {
    public Animal(){
        System.out.println("Mac dinh");
    }
    public Animal(String name) {
        System.out.println("Animal constructor called for " + name);
    }
}

class Dog extends Animal {
    public Dog(String name) {
        System.out.println("Dog constructor called for " + name);
    }
}

public class Main {
    public static void main(String[] args) {
        Dog myDog = new Dog("Buddy");
    }
}
class Animal {
    public Animal(){
        System.out.println("Mac dinh");
    }
    public Animal(String name) {
        System.out.println("Animal constructor called for " + name);
    }
}
class Dog extends Animal {
    public Dog(String name) {
        System.out.println("Dog constructor called for " + name);
    }
}
public class Main {
    public static void main(String[] args) {
        Dog myDog = new Dog("Buddy");
    }
}
// Mac dinh
// Dog constructor called for Buddy
```
Nếu trong Animal không có constructor mặc định thì trương trình sẽ báo lỗi 
### 5. Upcasting và Downcasting 
Cho chương trình 
```Java
class Animal {
    public void eat() {
        System.out.println("eating");
    }
}
public class Cat extends Animal {
    public void meow() {
        System.out.println("meow meow");
    }
}
```
#### a. Upcasting 
Upcasting là quá trình chuyển đổi một đối tượng từ kiểu con thành kiểu cha. Vì một đối tượng của lớp con luôn có thể được xem là một đối tượng của lớp cha, nhưng ngược lại thì không.
__Đặc điểm:__ Bạn chỉ có thể truy cập các phương thức của lớp cha, không thể truy cập các phương thức hoặc thuộc tính của lớp con.
```Java
public class Upcasting {
 
    public static void main(String[] args) {
        Cat cat = new Cat();
        Animal animal1 = cat; // Chuyển kiểu không tường minh
        Animal animal2 = (Animal) cat; // Chuyển kiểu tường minh
        cat.eat();
        cat.meow();
        animal1.eat();
        animal2.eat();
        // animal2.meow(); // Không thể gọi phương thức meow()
    }
    // eating
    // meow meow
    // eating
    // eating
}
```
#### b. Downcasting 
Downcasting là quá trình chuyển đổi một đối tượng từ kiểu cha thành kiểu con. Downcasting là một phép ép kiểu và có thể gây lỗi nếu không đúng, do đó cần phải kiểm tra loại kiểu đối tượng trước khi thực hiện phép downcast.

__Đặc điểm:__ 
- Không an toàn 
- Cần kiểm tra loại của đối tượng trước khi thực hiện
```Java
public class Downcating {
 
    public static void main(String[] args) {
        Animal animal = new Cat();
        Cat cat = (Cat) animal; // downcasting
        cat.meow();
    }
 
}
```
## III. Class Object
Lớp Object là __lớp cha của tất cả các lớp__ trong Java, do đó mọi đối tượng trong Java đều có thể được đối xử như một đối tượng của lớp Object. Điều này có nghĩa là bạn có thể lưu trữ bất kỳ đối tượng nào trong một biến kiểu Object, điều này cho phép tính linh hoạt khi xử lý các đối tượng.
```Java
Object obj = new String("Hello");
```
Java cho phép bạn viết các phương thức và thư viện mà không cần quan tâm đến kiểu cụ thể của đối tượng.
- Class Object có các phương thức như `equals(), toString(), hashCode(), clone(), finalize(), wait(), notify(), notifyAll(), …`
Các phương thức này được các class khác kế thừa, và có thể sử dụng lại.
## IV. Tính đa hình
Đa hình cho phép các đối tượng thuộc các lớp khác nhau có thể trả về cùng một kiểu phương thức, nhưng thực thi khác nhau dựa trên lớp thực tế của đối tượng. Tính đa hình giúp làm cho mã nguồn trở nên linh hoạt, mở rộng và dễ bảo trì hơn.
#### ***Compile Time & Runtime Time***
![](https://i.imgur.com/6EXBXks.png)
- Compile time là giai đoạn chuyển source code java về file bytecode từ .java về class. Kiếm tra code trong đoạn này
- Runtime Time là giai đoạn chạy hcuowng trình từ bytecode .class sau khi đã có compile trên môi trường JVM. Các lỗi dữ liệu có thể xảy ra

 __Có hai loại đa hình:__
- Đa hình lúc biên dịch
- Đa hình lúc chạy
### 1. Đa hình lúc chạy
Đa hình lúc runtime là quá trình gọi phương thức đã được ghi đè trong thời gian thực thi chương trình. Trong quá trình này, một phương thức được ghi đè được gọi thông qua biến tham chiếu của một lớp cha.
Ví Dụ: 
```Java
public class Bike {
    public void run() {
        System.out.println("running");
    }
}
public class Splender extends Bike {
    public void run() {
        System.out.println("running safely with 60km");
    }
 
    public static void main(String args[]) {
        Bike b = new Splender(); // upcasting 
        b.run();
    }
}
```
Lớp Splendar kế thừa lớp Bike và ghi đè phương thức run() của nó. Chúng ta gọi phương thức run bởi biến tham chiếu của lớp cha. Khi nó tham chiếu tới đối tượng của lớp con và phương thức lớp con ghi đè phương thức của lớp cha, phương thức lớp con được triệu hồi tại runtime. Nên gọi là đa hình tại runtime.
### 2. Đa hình lúc biên dịch
Loại đa hình này được giải quyết trong quá trình biên dịch mã khi mã trở thành lệnh máy. Nó thường đạt được thông qua quá tải khi nhiều phương thức trong cùng một lớp có cùng tên nhưng tham số khác nhau. Điều này cho phép một lớp thực hiện một hoạt động tương tự theo cách khác nhau, tùy thuộc vào đầu vào. 
## V. Phân biệt Overload và Override
1. Overload
Xảy ra khi chúng ta định nghĩa nhiều phương thức trong cùng một lớp với cùng tên nhưng khác biệt về số lượng hoặc kiểu dữ liệu của tham số.
__Sử dụng overload khi:__  thực hiện các phép toán hoặc hành động giống nhau nhưng với các tham số khác nhau.
_Quy tắc:_
- Phương thức nạp chồng phải có cùng tên nhưng khác nhau về số lượng hoặc kiểu tham số.
- Trả về kiểu dữ liệu có thể giống hoặc khác nhau.
- Việc quyết định phương thức nào được gọi sẽ được thực hiện tại thời điểm biên dịch.
```java
class Calculator {
    public int add(int a, int b) {
        return a + b;
    }
    public double add(double a, double b) {
        return a + b;
    }
    public int add(int a, int b, int c) {
        return a + b + c;
    }
}
public class Main {
    public static void main(String[] args) {
        Calculator calc = new Calculator();
        System.out.println(calc.add(10, 20));      
        System.out.println(calc.add(10.5, 20.5));  
        System.out.println(calc.add(10, 20, 30));  
    }
}
// 30
// 31.0
// 60
```
2. Override
Overriding xảy ra khi một lớp con cung cấp một phương thức mới cho phương thức đã có trong lớp cha. Lớp con sẽ ghi đè phương thức của lớp cha để thực hiện hành động cụ thể của lớp con.
__Sử dụng khi:__ bạn muốn thay đổi hành vi của một phương thức đã được định nghĩa trong lớp cha cho đối tượng của lớp con.
__Quy tắc:__
- Phương thức ghi đè trong lớp con phải có __cùng tên, cùng kiểu tham số và cùng kiểu trả__ về như phương thức trong lớp cha.
- Việc quyết định phương thức nào được gọi sẽ được thực hiện tại thời điểm chạy.
- Chỉ lớp con được ghi đè lên phương thức lớp cha
- Không thể ghi đè lên phương thức final hay staic. Vì final được triển khai cuối cùng và không được thay đổi, staic thuộc về lớp mà không thuộc về đối tượng nào.
- Khả năng quy trập lên phương thức ghi đè không được hạn chế hơn phương thức bị ghi đè
```Java
class Animal {
    public void sound() {
        System.out.println("Hello dog");
    }
}

class Dog extends Animal {
    @Override
    public void sound() {
        System.out.println("leu leu");
    }
}
public class Main {
    public static void main(String[] args) {
        Animal myAnimal = new Animal();
        Animal myDog = new Dog();  // Lớp con Dog

        myAnimal.sound();  // Gọi phương thức của lớp Animal
        myDog.sound();     // Gọi phương thức ghi đè của lớp Dog
    }
}
// Hello dog
// leu leu
```