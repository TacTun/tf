# Files to download from Xilinx: https://www.xilinx.com/support/download/index.html/content/xilinx/en/downloadNav/embedded-design-tools/2020-2.html
    - PetaLinux 2020.2 Installer (1.85 GB)
  All below files can be found under [PetaLinux Tools sstate-cache Artifacts - 2020.2 ] of above link
    - downloads_2020.2.tar.gz (36.01 GB)
    - sstate_mb-full_2020.2.tar.gz (3.2 GB)

# Updaing .xsa files
    # For QSPI
    cp ./ZX2/Mars_ZX2_wrapper.xsa ./MA-ZX2-20-2I-D9_ST3_QSPI/hardware/vivado_export/MA-ZX2-20-2I-D9_ST3.xsa
    cd MA-ZX2-20-2I-D9_ST3_QSPI 
    petalinux-config --get-hw-description=./hardware/vivado_export
    petalinux-build
    ./create_qspi_firmware

    # For SD Card
    cp ./ZX2/Mars_ZX2_wrapper.xsa ./MA-ZX2-20-2I-D9_ST3_SD/hardware/vivado_export/MA-ZX2-20-2I-D9_ST3.xsa
    cd MA-ZX2-20-2I-D9_ST3_SD 
    petalinux-config --get-hw-description=./hardware/vivado_export
    petalinux-build
    ./create_sdcard_firmware
    # Follow README.sdcard to program the firmware on SD Card

# To Create BSP projects from Enclustra's .bsp files which will not have any customizations made for TACTUN
    petalinux-create --type project -s Petalinux_MA-ZX2-20-2I-D9_ST3_SD.bsp
    petalinux-create --type project -s Petalinux_MA-ZX2-20-2I-D9_ST3_QSPI.bsp
