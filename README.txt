# BMP180_Driver
 Raspberry Pi 3b+
 BMP180

# 1. Phan cung

VCC ----> 3.3V power (Pin 1)|
GND ----> ground (Pin 6)

SCL ----> I2C1_SCL (Pin 5)|
SDA ----> I2C1_SDA (Pin 3)

# 2.CheCk i2c

	i2cdetect -y 1
	
```
# 3.Cai dat driver
```
- cai thu vien i2c
``` 
```
	sudo apt-get install libi2c-dev i2c-tools
```
- mo terminal thu muc hien chua file

chay lenh :
```
	 make
```
sau khi tao ra file bmp180.ko
```
```
- tien hanh nap module vao kernel
```
	sudo insmod bmp180.ko
```
- kiem tra thong bao tu kerel
```
	dmesg | tail
```
- hien thi thong bao nhu nay la thanh cong roi
```
	BMP180 driver loaded, device created at /dev/bmp180
```
 - kiem tra thiet bi
```
	s -l /dev/bmp180
```
doc du lieu tu thiet bi
```
	cat /dev/bmp180
```
go cai dat khi can thiet
```
	sudo rmmod bmp180
```
bien dich test file
```
	gcc -o test_bmp180 test_bmp180.c
``` chay
```	
	./test_bmp180
```
Nguyen Van Minh 22146351
Truong Manh Hung 22146321
Dinh Xuan Nam 22146353
Nguyen Nhu Hung 22146323





