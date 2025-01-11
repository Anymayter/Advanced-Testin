# Advanced-Testing

# 1. Tổng quan
Dự án này trình bày các kỹ thuật kiểm thử nâng cao sử dụng JUnit cho các thuật toán và cấu trúc dữ liệu phổ biến. Dự án cũng bao gồm các bước để đo lường và cải thiện phạm vi kiểm thử để đạt được phạm vi câu lệnh 100% bằng các công cụ như Jacoco.

# 2. Các Thuật Toán và Cấu Trúc Dữ Liệu Bao Gồm

  - Thuật Toán Sắp Xếp: Bubble Sort, Selection Sort, Insertion Sort, Quick Sort, Merge Sort, Heap Sort.

  - Danh Sách Liên Kết: Danh sách liên kết đơn và danh sách liên kết đôi.

  - Cây Nhị Phân: Cây tìm kiếm nhị phân (BST), Cây AVL.

  - Đồ Thị: BFS, DFS, Thuật toán Dijkstra.

  - Thuật Toán Tìm Kiếm: Tìm kiếm nhị phân, Tìm kiếm chuỗi con (Brute Force, KMP, Rabin-Karp).

  - Thuật Toán Đệ Quy: Giai thừa, Fibonacci, Backtracking (ví dụ: N-Queen, Giải Sudoku).

# 3. Đo lường độ bao phủ kiểm thử

 Công Cụ Sử Dụng: Jacoco cho Maven hoặc Gradle.

 Các Chỉ Số Bao Phủ:

  - Bao phủ lệnh (Instruction Coverage)

  - Bao phủ nhánh (Branch Coverage)

  - Bao phủ dòng (Line Coverage)

  - Bao phủ phương thức/lớp (Method/Class Coverage)

# 4. Đạt 100% bao phủ dòng lệnh

Phân tích các dòng chưa được bao phủ bằng Jacoco.

Thêm các trường hợp kiểm thử toàn diện cho tất cả điều kiện và nhánh.

# 5. Yêu cầu

Java 8+

Maven hoặc Gradle

IDE (IntelliJ IDEA, Eclipse, hoặc tương tự)

# 6. Cài đặt (thêm vào pom.xml)

```java
<plugin>
    <groupId>org.jacoco</groupId>
    <artifactId>jacoco-maven-plugin</artifactId>
    <version>0.8.8</version>
    <executions>
        <execution>
            <goals>
                <goal>prepare-agent</goal>
            </goals>
        </execution>
        <execution>
            <id>report</id>
            <phase>prepare-package</phase>
            <goals>
                <goal>report</goal>
            </goals>
        </execution>
    </executions>
</plugin>

```

# 7. Các trường hợp kiểm thử

MathUtils.java

```java

public class MathUtils {
    public int divide(int a, int b) {
        if (b == 0) {
            throw new IllegalArgumentException("Divider cannot be zero");
        }
        return a / b;
    }

    public int findMax(int[] numbers) {
        if (numbers == null || numbers.length == 0) {
            throw new IllegalArgumentException("Array cannot be null or empty");
        }
        int max = numbers[0];
        for (int num : numbers) {
            if (num > max) {
                max = num;
            }
        }
        return max;
    }
}

```

MathUtilsTest.java

```java

import static org.junit.jupiter.api.Assertions.*;
import org.junit.jupiter.api.Test;

class MathUtilsTest {

    @Test
    void testDivide() {
        MathUtils mathUtils = new MathUtils();

        // Kiểm thử trường hợp bình thường
        assertEquals(2, mathUtils.divide(4, 2));

        // Kiểm thử chia cho 0
        assertThrows(IllegalArgumentException.class, () -> mathUtils.divide(4, 0));
    }

    @Test
    void testFindMax() {
        MathUtils mathUtils = new MathUtils();

        // Kiểm thử trường hợp bình thường
        assertEquals(5, mathUtils.findMax(new int[]{1, 2, 5, 3}));

        // Kiểm thử mảng rỗng
        assertThrows(IllegalArgumentException.class, () -> mathUtils.findMax(new int[]{}));

        // Kiểm thử mảng null
        assertThrows(IllegalArgumentException.class, () -> mathUtils.findMax(null));
    }
}

```

# 8. Kết quả Test

![Screenshot 2025-01-11 165740](https://github.com/user-attachments/assets/96acfcf2-c943-43fd-b078-9c3e2bc9001f)


# 9. Mã nguồn chatgpt

https://chatgpt.com/c/6782ab1c-1708-800b-885f-ec702a9963ef

# 10. Sinh viên
Nguyễn Đức Toàn







