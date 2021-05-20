# Raspberry Pi Security Camera
## อุปกรณ์
• Raspberry Pi 4 Model B 2GB RAM  
• Power Supply  
• Raspberry Pi NoIR Camera V2 8MP  
• 8GB Micro SD Card  
## ขั้นตอนการติดตั้ง
### 1. ติดตั้ง Raspberry Pi NoIR Camera บน Raspberry Pi 4
### 2. ติดตั้ง MotionEye OS
2.1 ดาวน์โหลดและติดตั้ง SD Memory Card Formatter จาก https://www.sdcard.org/downloads/formatter/  
2.2 ใส่ SD Card ใน SD Card Reader เพื่อเชื่อมต่อเข้ากับคอมพิวเตอร์  
2.3 ใช้โปรแกรม SD Memory Card Formatter ในการ Format SD Card  
(อย่าลืมเช็ค Drive Letter เช่น D:\ หรือ E:\ ว่าเป็นของ SD Card รึเปล่า)  
2.4 ดาวน์โหลดและติดตั้ง Win32DiskImager จาก https://sourceforge.net/projects/win32diskimager/  
2.5 ดาวน์โหลด motioneyeos-raspberrypi4-20200606.img.xz หรือ MotionEye OS SD Card Image เวอร์ชั่นล่าสุด จาก https://github.com/ccrisan/motioneyeos/releases  
2.6 แตกไฟล์ MotionEye OS SD Card Image ที่ได้ทำการดาวน์โหลดมา  
2.7 เปิดโปรแกรม Win32DiskImager แล้วทำการเลือกไฟล์นามสกุล .img ที่ได้จากการแตกไฟล์  
2.8 กดปุ่ม Write เพื่อทำการติดตั้ง
### 3. ตั้งค่าการเชื่อมต่อแบบไร้สาย
3.1 ดาวน์โหลดและติดตั้ง Notepad++ จาก https://notepad-plus-plus.org/downloads/  
3.2 เปิดโปรแกรม Notepad++ แล้วคัดลอกข้อความต่อไปนี้วางลงในไฟล์
```
country=TH  
ctrl_interface=DIR=/var/run/wpa_supplicant GROUP=netdev  
update_config=1  
network={  
  ssid="NETWORK-NAME"  
  psk="NETWORK-PASSWORD"  
}
```  
3.3 เปลี่ยนข้อความ NETWORK-NAME และ NETWORK-PASSWORD เป็นชื่อ WiFi แล้วรหัสผ่านของเราตามลำดับ  
(ไม่ต้องลบ " ออก)  
3.4 กด Save As ไปไว้ในหน้าแรกของ SD Card Drive (จะมีไฟล์ต่าง ๆ เช่น bcm2711-rpi-4-b.dtb, bootcode.bin, cmdline)
### 4. ถอด SD Card ที่เชื่อมต่อกับคอมพิวเตอร์แล้วนำไปใส่ในช่อง SD Card ของ Raspberry Pi 4
### 5. เสียบสาย Power Supply เข้ากับ Raspberry Pi 4
### 6. ค้นหา IP Address ของ Raspberry Pi 4
6.1 ดาวน์โหลด Wireless Network Watcher จาก https://www.nirsoft.net/utils/wnetwatcher.zip  
6.2 แตกไฟล์ wnetwatcher.zip ที่ได้ทำการดาวน์โหลดมา  
6.3 เปิดโปรแกรม Wireless Network Watcher เพื่อค้นหา IP Address ของ Raspberry Pi 4  
(Network Adapter Company = "Raspberry Pi ...")
### 7. นำ IP Address ที่ได้ไปใส่ในช่องค้นหาของ Browser
### 8. กดปุ่ม switch user เพื่อทำการ Login (ปุ่มที่ 2 จากมุมซ้ายบน)
#### ในช่อง Username ให้ใส่ว่า admin ส่วนช่อง Password ให้เว้นว่างเอาไว้
### 9. ตั้งค่าเบื้องต้น
9.1 กดปุ่ม settings (ปุ่มที่ 1 จากมุมซ้ายบน)  
9.2 ในหัวข้อ Preferences > Layout Columns เปลี่ยนจาก 3 เป็น 1  
9.3 ในหัวข้อ General Settings > Time Zone เปลี่ยนจาก UTC เป็น Asia/Bangkok  
9.4 ในหัวข้อ Video Device  
• Automatic Brightness เปลี่ยนจาก OFF เป็น ON  
• Frame Rate เปลี่ยนจาก 2 เป็น 30  
9.5 ในหัวข้อ Text Overlay > Text Scale เปลี่ยนจาก 1 เป็น 2  
9.6 ในหัวข้อ Still Images > Capture Mode เปลี่ยนจาก Manual เป็น Motion Triggered (One Picture)  
9.7 ในหัวข้อ Movies > Movie Format เปลี่ยนจาก H.264/OMX เป็น MPEG4  
9.8 ในหัวข้อ Motion Detection  
• Frame Change Threshold เปลี่ยนจาก 0.7% เป็น 2.5%  
• Auto Noise Detection เปลี่ยนจาก ON เป็น OFF และเปลี่ยน Noise Level เป็น 25%  
9.9 กดปุ่ม Apply เพื่อ Reboot System
