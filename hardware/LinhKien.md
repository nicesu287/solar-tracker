# Danh mục Linh kiện (Bill of Materials — BOM)

**Đề tài:** Hệ thống tích trữ năng lượng mặt trời tích hợp bám sáng tự động (*Energy Storage with Solar Tracker System*)  
**Môn học:** Thiết kế Hệ thống Nhúng (`EE3003`) — **Lớp:** `L01` — **Nhóm:** `7` — **HK:** `261`  
**Ngân sách dự toán:** `1.000.000 – 1.500.000 VNĐ`

---

## Bảng tổng hợp linh kiện phần cứng

| STT | Ref Des | Hạng mục | Mô tả / Thông số | SL | Đơn giá (VNĐ) | Thành tiền (VNĐ) |
| :---: | :--- | :--- | :--- | :---: | :---: | :---: |
| 1 | `U1` | Vi điều khiển trung tâm | `STM32F103C8T6` Blue Pill (Cortex-M3 `72 MHz`, `64 KB` Flash, `20 KB` SRAM) | 1 | 65.000 | 65.000 |
| 2 | `STLINK` | Mạch nạp & gỡ lỗi | Mạch nạp `ST-Link V2` Mini (giao tiếp `SWD`) | 1 | 55.000 | 55.000 |
| 3 | `B1` | Tấm pin năng lượng mặt trời | `Waveshare` Polycrystalline `18V - 10W` (cạnh ~`34 cm`) | 1 | 240.000 | 240.000 |
| 4 | `M1, M2` | Động cơ Servo bám sáng | `Servo MG996R` công suất lớn `20 kg·cm` (`Pan 0°–180°`, `Tilt 0°–90°`) | 2 | 95.000 | 190.000 |
| 5 | `OLED1` | Màn hình hiển thị | `OLED 0.96"` I2C (`SSD1306`, `128×64`, địa chỉ `0x3C / 0x78`) | 1 | 65.000 | 65.000 |
| 6 | `U2` | Mạch hạ áp DC-DC | Module Buck `LM2596` (`18V → 5V`, tối đa `3A`) | 1 | 25.000 | 25.000 |
| 7 | `U3, U4` | Mạch sạc pin Li-ion | Module sạc `TP4056` `1A` tích hợp IC bảo vệ `DW01A` | 2 | 15.000 | 30.000 |
| 8 | `U5` | Mạch tăng áp DC-DC | Module Boost `XL6009` (nâng áp khối `2× 18650` `3.7V → 5V` nuôi mạch & Servo) | 1 | 30.000 | 30.000 |
| 9 | `BT1..BT4` | Pin sạc lưu trữ đầu ra | Cell Li-ion `18650 High-Drain` (`3.7V–4.2V`, `2500 mAh` — Output độc lập) | 4 | 55.000 | 220.000 |
| 10 | `BT5, BT6` | Pin nguồn nuôi hệ thống | Cell Li-ion `18650` (cấp vào `XL6009` nuôi `STM32`, `OLED` & `2× Servo`) | 2 | 45.000 | 90.000 |
| 11 | `BH1, BH2` | Đế pin `18650` | Đế 4 cell + Đế 2 cell `18650` (dây ra `20 AWG`) | 2 | 20.000 | 40.000 |
| 12 | `RL1, Q1, D1, C1` | Khối kích Relay & lọc nguồn | `Relay 5V` + BJT `2N2222` + Diode `1N4007` + Tụ `1000 µF / 16V` | 1 bộ | 25.000 | 25.000 |
| 13 | `LDR, R, SW` | Cảm biến & thụ động | 4× `LDR GL5528`, trở `10k/100k/4.7k/1kΩ`, tụ `10 nF`, 2 nút nhấn | 1 bộ | 35.000 | 35.000 |
| 14 | `J, WIRE` | Đầu nối, bo & dây dẫn | PCB/Testboard đồng, Header `2.54 mm`, Domino `KF301`, dây động lực | 1 bộ | 50.000 | 50.000 |
| 15 | `MECH` | Khung cơ khí & gá Pan-Tilt | Giá đỡ Pan-Tilt hợp kim + đế `250×250×400 mm` & vách chữ thập | 1 bộ | 120.000 | 120.000 |
| **Tổng** | — | **Tổng chi phí dự toán (BOM)** | **Đạt định mức ngân sách `1.000.000 – 1.500.000 VNĐ`** | — | — | **1.280.000** |

---

## Lưu ý lắp ráp & đấu nối thực tế
- **Cầu phân áp bảo vệ chân ADC (`≤ 3.3V`):** Lắp cầu phân áp `100 kΩ / 10 kΩ` (`11:1`) tại `PA4` (đo tấm pin `18V-10W`) và `10 kΩ / 10 kΩ` (`2:1`) tại `PA5` (`2× 18650` nguồn nuôi), `PA6` (`4× 18650` pin sạc đầu ra).
- **Nối đất hình sao (`Star Ground`):** Gom dây `GND` dòng cao của Servo về thẳng cực âm tụ `1000 µF`/nguồn chính, tách riêng với `GND` tín hiệu `LDR` và `OLED` để tránh nhiễu.
- **Dây dẫn công suất:** Sử dụng dây tiết diện tối thiểu `20 AWG` cho đường pin `18650`, `LM2596`, `XL6009` và nguồn `5V` cấp `2× Servo MG996R`.

> Bản Excel/CSV tương ứng: [LinhKien.csv](LinhKien.csv)
