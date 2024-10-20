## Esphome as an App on the MCH2022 badge
Very much a work in progress. Based on esp-idf.
#### Working features
* Wifi
* RGB Leds in the kite
* I2C
* Bosch bme680 climate sensor
* Display
* Buttons (internal only)
#### Not working (yet?)
* All the other I/O connected to the rpi204, USB charging, voltages, IR Led, LCD Backlight, etc
* Audio
* The BNO055 accelerometer, gyroscope, magnetometer sensor (no component in esphome for this (yet))
* FPGA connected i/o: RGB Led, pmod pins.
* Other GPIO

### Building
* Create a new esp32dev device in esphome
* Modify the generated yaml to include the sections from the mch2022-badge.yaml file in this repo.
* Make sure to upload the mch2022-partitions.csv file to the same folder as the yaml
* Install and select the manual upload option
* When done select the "OTA format" version of the binary. This will download the file mch2022-badge.ota.bin.
* Rename it to main.bin and use the [mch2022-tools package](https://github.com/badgeteam/mch2022-tools) to upload it to the mch2022 badge you have connected to your machine. Something like ```./mch2022-tools/app_push.py -r esphome/main.bin esphome Esphome 1``` should do the trick.
* This should run the application but you can also see the Esphome app in the Apps section of the BadgeOS launcher. 