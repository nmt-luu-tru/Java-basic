**Chuyển đổi dữ liệu từ String ra kiểu mong muốn** là vấn đề rất thường gặp khi làm việc với Java. Dưới đây là một số phương pháp chuyển đổi phổ biến:

**1. Parse Int**  
Chuyển đổi **String** sang **int** trong Java thường được sử dụng khi cần chuyển giá trị đầu vào dạng **String** thành kiểu **int** để tính toán. Để làm điều này, chúng ta sử dụng phương thức **`parseInt()`** của lớp **`Integer`**:
```java
int i = Integer.parseInt(s);
```
Ngoài ra, có thể dùng **`Integer.valueOf()`**. Điểm khác biệt là **`valueOf()`** trả về **đối tượng của lớp Integer**, trong khi **`parseInt()`** trả về **giá trị `int` nguyên thủy**. Tùy vào trường hợp mà chọn hàm phù hợp.

**Một số phương thức chuyển đổi khác:**

- **Parse Long**  
  ```java
  long l = Long.parseLong(s);
  ```

- **Parse Float**  
  ```java
  float f = Float.parseFloat(s);
  ```

- **Parse Double**  
  ```java
  double d = Double.parseDouble(s);
  ```

- **Parse Date**  
  Chuyển đổi từ **String** sang **Date** bằng cách sử dụng **`SimpleDateFormat`**:
  ```java
  try {
      String sDate = "30/04/2022";
      Date date = new SimpleDateFormat("dd/MM/yyyy").parse(sDate);
      System.out.println(sDate + "\t" + date);
  } catch (Exception e) {
      e.printStackTrace();
  }
  ```
  ---
  ### Chuyển Đổi Chuỗi Thành Giá Trị Số Trong Java

Trong nhiều trường hợp, chúng ta cần phải chuyển đổi một chuỗi (String) thành một kiểu dữ liệu khác như số nguyên (int) hoặc số thực (double). Điều này thường gặp khi bạn cần đọc đầu vào từ người dùng, ví dụ sau khi người dùng nhập dữ liệu qua giao diện hoặc từ bàn phím.

Chúng ta sẽ tìm hiểu cách chuyển đổi một chuỗi thành số nguyên hoặc số thực thông qua phương thức **parse**.

### Chuyển Đổi Chuỗi Thành Số Nguyên (`int`)
Để bắt đầu, chúng ta sẽ tạo một chuỗi chứa một số và sau đó chuyển nó thành kiểu số nguyên (`int`) bằng cách sử dụng phương thức `parseInt()` của lớp `Integer`.

```java
public class Main {
    public static void main(String[] args) {
        // Định nghĩa chuỗi chứa số
        String numberAsString = "2018";
        
        // In chuỗi ra màn hình
        System.out.println("Number as string = " + numberAsString);

        // Chuyển đổi chuỗi thành số nguyên
        int number = Integer.parseInt(numberAsString);
        
        // In số nguyên ra màn hình
        System.out.println("Number = " + number);

        // Thực hiện phép tính với số nguyên
        numberAsString += 1; // Nối thêm '1' vào chuỗi
        number += 1;         // Tăng số nguyên thêm 1
        
        // In kết quả sau khi thực hiện phép tính
        System.out.println("Number as string after concatenation = " + numberAsString);
        System.out.println("Number after incrementing = " + number);
    }
}
```

### Giải Thích Code
- **`Integer.parseInt(numberAsString);`**: Chuyển đổi chuỗi `numberAsString` thành số nguyên bằng phương thức `parseInt()`.
- **`numberAsString += 1;`**: Khi thêm `1` vào chuỗi, Java sẽ nối thêm '1' vào cuối chuỗi, tạo thành `"20181"`.
- **`number += 1;`**: Khi thêm `1` vào `number`, Java sẽ thực hiện phép toán tăng số nguyên lên 1, từ 2018 thành 2019.

### Kết Quả
```
Number as string = 2018
Number = 2018
Number as string after concatenation = 20181
Number after incrementing = 2019
```

### Xử Lý Trường Hợp Chuỗi Không Hợp Lệ
Nếu chuỗi chứa các ký tự không phải là số hợp lệ, chẳng hạn như `"2018a"`, khi bạn cố gắng chuyển đổi nó sang số nguyên, Java sẽ ném ra một ngoại lệ **`NumberFormatException`**. Dưới đây là ví dụ:

```java
public class Main {
    public static void main(String[] args) {
        String numberAsString = "2018a"; // Chuỗi không hợp lệ

        try {
            // Thử chuyển đổi chuỗi thành số nguyên
            int number = Integer.parseInt(numberAsString);
        } catch (NumberFormatException e) {
            System.out.println("Error: " + e.getMessage());
        }
    }
}
```

### Chuyển Đổi Chuỗi Thành Số Thực (`double`)
Tương tự, chúng ta có thể chuyển đổi chuỗi thành số thực bằng phương thức `parseDouble()` của lớp `Double`.

```java
public class Main {
    public static void main(String[] args) {
        // Định nghĩa chuỗi chứa số thực
        String numberAsString = "2018.125";
        
        // Chuyển đổi chuỗi thành số thực
        double number = Double.parseDouble(numberAsString);
        
        // In kết quả
        System.out.println("Number as string = " + numberAsString);
        System.out.println("Number = " + number);

        // Thực hiện phép tính với số thực
        number += 1; // Tăng số thực thêm 1
        
        // In kết quả sau khi thực hiện phép tính
        System.out.println("Number after incrementing = " + number);
    }
}
```

### Kết Quả
```
Number as string = 2018.125
Number = 2018.125
Number after incrementing = 2019.125
```

### Lưu Ý Về Phép Nối Chuỗi
- Khi thực hiện phép nối chuỗi và số bằng toán tử `+`, Java sẽ tự động chuyển đổi số thành chuỗi trước khi thực hiện phép nối.

### Tổng Kết
Chuyển đổi chuỗi thành số nguyên hoặc số thực trong Java rất dễ dàng với các phương thức như `parseInt()` và `parseDouble()`. Tuy nhiên, bạn cần cẩn thận với các chuỗi không hợp lệ, vì chúng có thể gây ra ngoại lệ `NumberFormatException`.

Các phương thức trên giúp bạn **chuyển đổi** dữ liệu từ **chuỗi** sang các kiểu dữ liệu khác nhau phù hợp với nhu cầu tính toán và xử lý trong Java.
