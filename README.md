# Dự Án Kiểm Thử Thuật Toán và Cấu Trúc Dữ Liệu với JUnit

## Mục Tiêu
Dự án này nhằm kiểm thử các thuật toán sắp xếp, tìm kiếm, cấu trúc dữ liệu và tính toán cơ bản bằng cách sử dụng JUnit. Các bài kiểm thử được thiết kế để đạt mức độ bao phủ kiểm thử cao nhất, bao gồm việc đo mức độ bao phủ dòng lệnh (statement coverage) và nhánh (branch coverage).

## Cấu Trúc Dự Án
- **Thuật toán và Cấu trúc dữ liệu**:
  - Sắp xếp: Bubble Sort, Merge Sort.
  - Tìm kiếm: Tìm kiếm tuyến tính, tìm kiếm nhị phân.
  - Cấu trúc dữ liệu: Ngăn xếp (Stack), Hàng đợi (Queue).
  - Tính toán: Fibonacci, Giai thừa.

- **Kiểm thử**:
  - Các ca kiểm thử được viết bằng JUnit để đảm bảo độ chính xác và đầy đủ của từng thuật toán và cấu trúc dữ liệu.
  - Đo mức độ bao phủ kiểm thử bằng công cụ JaCoCo.

## Cài Đặt

### Cài Đặt Môi Trường
1. **Cài đặt JDK**: Đảm bảo rằng bạn đã cài đặt JDK 8 trở lên.
2. **Cài đặt Maven**: Cài đặt Maven để quản lý dự án.
3. **Cài đặt IDE**: Sử dụng IDE yêu thích như IntelliJ IDEA hoặc Eclipse.

### Cài Đặt Công Cụ Bao Phủ Kiểm Thử (Test Coverage)
- **JaCoCo**: Công cụ được sử dụng để đo mức độ bao phủ kiểm thử (coverage).

**Cài đặt JaCoCo cho Maven**:
Thêm cấu hình JaCoCo vào file `pom.xml`:

```xml
<build>
    <plugins>
        <plugin>
            <groupId>org.jacoco</groupId>
            <artifactId>jacoco-maven-plugin</artifactId>
            <version>0.8.7</version>
            <executions>
                <execution>
                    <phase>prepare-package</phase>
                    <goals>
                        <goal>prepare-agent</goal>
                        <goal>report</goal>
                    </goals>
                </execution>
            </executions>
        </plugin>
    </plugins>
</build>

```

## Chạy dự án

1. Biên dịch và chạy kiểm thử

mvn clean test

2. Kiểm tra báo cáo bao phủ kiểm thử:
   Sau khi chạy kiểm thử, báo cáo bao phủ kiểm thử sẽ được tạo trong thư mục target/site/jacoco/. Mở file index.html trong trình duyệt để xem báo cáo chi tiết về mức độ bao phủ.

## Các thuật toán kiểm thử

# 1. Sắp xếp (Sorting Algorithms)
Bubble Sort: Thuật toán sắp xếp bằng cách hoán đổi các phần tử liên tiếp nếu chúng không đúng thứ tự.
Merge Sort: Thuật toán chia để trị (divide and conquer) sắp xếp mảng.
# 2. Tìm kiếm (Search Algorithms)
Tìm kiếm nhị phân (Binary Search): Thuật toán tìm kiếm trong mảng đã được sắp xếp.
Tìm kiếm tuyến tính (Linear Search): Thuật toán tìm kiếm trong mảng không sắp xếp.
# 3. Cấu trúc Dữ Liệu (Data Structures)
Ngăn xếp (Stack): Cấu trúc dữ liệu theo nguyên lý LIFO (Last In, First Out).
Hàng đợi (Queue): Cấu trúc dữ liệu theo nguyên lý FIFO (First In, First Out).
# 4. Tính toán (Computations)
Fibonacci Sequence: Tính số Fibonacci thứ n.
Giai thừa (Factorial): Tính giai thừa của một số nguyên dương.

## Kiểm Thử với JUnit

Các bài kiểm thử được thiết kế với JUnit và có các ca kiểm thử cho mỗi thuật toán và cấu trúc dữ liệu. Ví dụ về kiểm thử Bubble Sort:

```java

import static org.junit.jupiter.api.Assertions.*;
import org.junit.jupiter.api.Test;

class SortingTest {

    @Test
    void testBubbleSort() {
        int[] input = {5, 3, 8, 4, 2};
        int[] expected = {2, 3, 4, 5, 8};
        
        BubbleSort.sort(input);
        
        assertArrayEquals(expected, input);
    }

    @Test
    void testBubbleSortEmptyArray() {
        int[] input = {};
        int[] expected = {};
        
        BubbleSort.sort(input);
        
        assertArrayEquals(expected, input);
    }

    @Test
    void testBubbleSortSingleElement() {
        int[] input = {1};
        int[] expected = {1};
        
        BubbleSort.sort(input);
        
        assertArrayEquals(expected, input);
    }
}

```

## Các Ca Kiểm Thử Bổ Sung Để Đạt 100% Statement Coverage

Các ca kiểm thử đã được thiết kế để bao phủ tất cả các dòng lệnh trong mã nguồn. Ví dụ, với phương thức findMax, các ca kiểm thử bổ sung sẽ bao gồm:

- Mảng rỗng hoặc null.
- Mảng có một phần tử.
- Mảng có nhiều phần tử.

```java

@Test
void testFindMaxWithEmptyArray() {
    int[] arr = {};  // Mảng rỗng
    assertThrows(IllegalArgumentException.class, () -> {
        findMax(arr);
    });
}

@Test
void testFindMaxWithSingleElement() {
    int[] arr = {5};  // Mảng với một phần tử
    assertEquals(5, findMax(arr));
}

@Test
void testFindMaxWithMultipleElements() {
    int[] arr = {5, 3, 8, 4, 2};  // Mảng với nhiều phần tử
    assertEquals(8, findMax(arr));
}

```

## Kết Quả Kiểm Thử

Sau khi chạy tất cả các ca kiểm thử, mức độ bao phủ kiểm thử dòng lệnh (statement coverage) sẽ đạt 100%. Điều này có nghĩa là mọi dòng lệnh trong mã nguồn đều đã được kiểm thử ít nhất một lần.

## 🔍 Tính năng nổi bật

- ✅ Hỗ trợ nhiều thuật toán nâng cao.
- 📊 Công cụ đo lường kiểm thử hiện đại (Jacoco).
- 🔧 Hỗ trợ cấu hình linh hoạt với Maven/Gradle.

## Kết quả kiểm thử

Sau khi chạy tất cả các ca kiểm thử, mức độ bao phủ kiểm thử dòng lệnh (statement coverage) sẽ đạt 100%. Điều này có nghĩa là mọi dòng lệnh trong mã nguồn đều đã được kiểm thử ít nhất một lần.


## Đóng góp

1. Tạo một issue nếu bạn gặp lỗi hoặc có ý tưởng mới.
2. Fork dự án và gửi pull request.

## Mã nguồn chatgpt

https://chatgpt.com/c/6782ab1c-1708-800b-885f-ec702a9963ef









