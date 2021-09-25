
* Creating BSP projects from scratch
petalinux-create --type project -s Petalinux_MA-ZX2-20-2I-D9_ST3_SD.bsp
petalinux-create --type project -s Petalinux_MA-ZX2-20-2I-D9_ST3_QSPI.bsp

* Updaing .xsa files

cp ./ZX2/Mars_ZX2_wrapper.xsa ./MA-ZX2-20-2I-D9_ST3_SD/hardware/vivado_export/MA-ZX2-20-2I-D9_ST3.xsa
cp ./ZX2/Mars_ZX2_wrapper.xsa ./MA-ZX2-20-2I-D9_ST3_QSPI/hardware/vivado_export/MA-ZX2-20-2I-D9_ST3.xsa
petalinux-config --get-hw-description=./hardware/vivado_export

* Building the project
petalinux-build

* Creat boot image
petalinux-package --boot --fsbl images/linux/zynq_fsbl.elf --fpga ../ZX2/Mars_ZX2.bit --u-boot --force

