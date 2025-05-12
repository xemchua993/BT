
# BMP180_Driver

**Nền tảng**: Raspberry Pi 3B+  
**Thiết bị cảm biến**: BMP180 (Cảm biến áp suất và nhiệt độ)

---

## 1. Kết nối phần cứng

| BMP180 Pin | Raspberry Pi Pin |
|------------|------------------|
| VCC        | 3.3V (Pin 1)     |
| GND        | GND (Pin 6)      |
| SCL        | I2C1_SCL (Pin 5) |
| SDA        | I2C1_SDA (Pin 3) |

---

## 2. Kiểm tra kết nối I2C

Mở terminal và chạy lệnh:

```bash
i2cdetect -y 1
```

BMP180 thường có địa chỉ là `0x77`.

---

## 3. Cài đặt driver

### 3.1 Cài đặt thư viện cần thiết

```bash
sudo apt-get install libi2c-dev i2c-tools
```

### 3.2 Biên dịch module kernel

Chuyển vào thư mục chứa mã nguồn:

```bash
make
```

Sau khi biên dịch thành công sẽ tạo ra file `bmp180.ko`.

### 3.3 Nạp module vào kernel

```bash
sudo insmod bmp180.ko
```

### 3.4 Kiểm tra thông báo kernel

```bash
dmesg | tail
```

Nếu hiển thị dòng sau nghĩa là đã thành công:

```
BMP180 driver loaded, device created at /dev/bmp180
```

---

## 4. Đọc dữ liệu từ thiết bị

### 4.1 Kiểm tra thiết bị

```bash
ls -l /dev/bmp180
```

### 4.2 Đọc dữ liệu

```bash
cat /dev/bmp180
```

### 4.3 Gỡ module khi không cần thiết

```bash
sudo rmmod bmp180
```

---

## 5. Biên dịch và chạy file test

### Biên dịch:

```bash
gcc -o test_bmp180 test_bmp180.c
```

### Chạy chương trình:

```bash
./test_bmp180
```

---

## Tác giả

- Nguyễn Văn Minh - 22146351  
- Trương Mạnh Hùng - 22146321  
- Đinh Xuân Nam - 22146353  
- Nguyễn Như Hưng - 22146323  
