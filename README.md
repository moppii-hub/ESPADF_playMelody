# Summary / 概要

en

---

jp

---

zh

# Required / 必要環境
## Hardware / ハード
* ESP32 board (ESP32-DevKitC, ESP-WROVER-KIT, etc.) or ESP-ADF boards
* MAX98357A I2S amplifer (If you use ESP-ADF boards, it already has ES8388 codec-chip so no need.)
* Speaker unit


## Sofware / ソフト
* [ESP-IDF v3.3](https://docs.espressif.com/projects/esp-idf/en/v3.3.1/index.html) ([Github](https://github.com/espressif/esp-idf))
* [ESP-ADF](https://docs.espressif.com/projects/esp-adf/en/latest/) ([Github](https://github.com/espressif/esp-adf))


# Pin Assgin / ピンアサイン
| pin name (MAX98357A board print) | function | gpio_num |
|:---:|:---:|:---:|
| WS (LRC) | word select (L/R Clock) | GPIO_NUM_25 |
| SCK (BCLK) | continuous serial clock (Block CLocK) | GPIO_NUM_5 |
| SD (DIN) | serial data (Data IN) | GPIO_NUM_26 |

![Wiring](https://github.com/moppii-hub/ESPADF_geneSig/blob/master/ESPADF_geneSig.png)


# Usage / 使用方法
## Prepare for dev-env / 環境構築

See [Get Started page](https://docs.espressif.com/projects/esp-adf/en/latest/get-started/index.html) for install ESP-ADF.  
If you don't have installed ESP-IDF v3.3.1, see [ESP-IDF v3.3.1 Get Started page](https://docs.espressif.com/projects/esp-idf/en/v3.3.1/get-started/index.html) to get it.  
  
Example commands(for mac):  
```bash
# First, need to download https://dl.espressif.com/dl/xtensa-esp32-elf-osx-1.22.0-80-g6c4433a-5.2.0.tar.gz to ~/Downloads
mkdir -p ~/esp
cd ~/esp
tar -xzf ~/Downloads/xtensa-esp32-elf-osx-1.22.0-80-g6c4433a-5.2.0.tar.gz
git clone -b v3.3.1 --recursive https://github.com/espressif/esp-idf.git
git clone --recursive https://github.com/espressif/esp-adf.git


# First, need to set up some Env-variables.
python -m pip install --user -r $IDF_PATH/requirements.txt
```


## Download projects(git clone) / プロジェクトのダウンロード(git clone)
```bash
cd ~/esp
git clone https://github.com/moppii-hub/*.git
```


## Flash program / プログラムの書き込み
```bash
cd ~/esp/ESPADF_geneSig/
make menuconfig
# For flashing, it is need to setup correct USB-serial port in menuconfig.

make flash
```

