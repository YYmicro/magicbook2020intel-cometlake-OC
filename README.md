# Honor magicbook 2020 intel hackintosh EFI

this is the catalina branch

## Configuration

| 描述     | 详情                               |
| :------: | :--------------------------------: |
| 电脑型号 | Honor Magicbook 14 intel           |
| CPU      | Intel i7-10510U                    |
| RAM      | 16GB 2400MHz DDR4                  |
| Disk     | WD SN730 512GB                     |
| GPU      | Intel UHD Graphics                 |
| 声卡     | Realtek ALC256                     |
| 键盘     | PS/2                               |
| 无线网卡 | Intel Wireless-AC 9560 160MHz 板载 |
| 触控板   | HID I2C                            |



## 2025.05.21 ACPI问题记录
ACPI似乎无法识别特别大的SSDT文件或者比较新的版本，目前使用的文件是淘宝买的EFI中的SSDT文件。后续需要仔细研究ACPI文件的问题。
```
00:000 00:000 OCA: Inserted ACPI table has length mismatch 281875 vs 557582858, ignoring
00:000 00:000 OC: Failed to add ACPI SSDT-XOSI.aml - Invalid Parameter
00:002 00:001 OCA: Inserted ACPI table has length mismatch 281754 vs 557582858, ignoring
00:002 00:000 OC: Failed to add ACPI SSDT-AWAC.aml - Invalid Parameter
00:004 00:001 OCA: Inserted ACPI table has length mismatch 282112 vs 557582858, ignoring
00:005 00:000 OC: Failed to add ACPI SSDT-EC-USBX-LAPTOP.aml - Invalid Parameter
00:007 00:001 OCA: Inserted ACPI table has length mismatch 282045 vs 557582858, ignoring
00:007 00:000 OC: Failed to add ACPI SSDT-PLUG.aml - Invalid Parameter
00:009 00:001 OCA: Inserted ACPI table has length mismatch 282190 vs 557582858, ignoring
00:009 00:000 OC: Failed to add ACPI SSDT-PMC.aml - Invalid Parameter
00:011 00:001 OCA: Inserted ACPI table has length mismatch 281892 vs 557582858, ignoring
00:011 00:000 OC: Failed to add ACPI SSDT-PNLF.aml - Invalid Parameter
```

## 2025.05.27 ACPI问题记录
按照国光酱的方式配置常见的ACPI后，会遇到一些I2C无法找到bus配置的问题，导致PS2 kext驱动在寻找触控板的时候会出问题，导致报错。  
根据deepseek的分析，可能是ACPI传过来的东西就有问题。  
因此我直接照搬了淘宝EFI所有的ACPI文件以及配置。  
后面需要研究一下ACPI什么配置会导致I2C获取bus config失败。


## TODO list  

- [ ] ACPI版本更新  
- [ ] ACPI研究什么配置会导致I2C获取bus config失败