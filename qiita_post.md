# はじめに


# 準備するもの
- PC(筆者はMac)
- ESP32開発ボード(NodeMCU, ESP-WROOM-32等)
- MAX98357A I2S DACモジュール(Adafruit製や類似品)
- スピーカユニット（使用するDACに適したもの。0.5～3W程度の小さいもの）



# 環境構築
## ESP-ADFの導入

```bash
# 事前に https://dl.espressif.com/dl/xtensa-esp32-elf-osx-1.22.0-80-g6c4433a-5.2.0.tar.gz を~/Downloadsへダウンロードしておく。
mkdir -p ~/esp
cd ~/esp
tar -xzf ~/Downloads/xtensa-esp32-elf-osx-1.22.0-80-g6c4433a-5.2.0.tar.gz
git clone -b v3.3.1 --recursive https://github.com/espressif/esp-idf.git
git clone --recursive https://github.com/espressif/esp-adf.git

# pipでパッケージをインストールする。（pipが無ければ別途インストール必要）
# また、環境変数$IDF_PATHを設定する必要あり。
python -m pip install --user -r $IDF_PATH/requirements.txt
```



## Githubからプログラムを入手（git clonoe）

```bash
cd ~/esp
git clone ...
```



## 回路の製作
　[先日の投稿](https://qiita.com/moppii/items/e109324d21429f12e2bd)の回路と同じです。再掲します。  

![Wiring](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/603551/20ed0e84-7233-4fa5-71ab-d0998ecd68af.png)



# とりあえず動作させる
　まず、`make menuconfig`を実行し、シリアルポートの設定をします。  

```bash
cd ~/esp/ESPADF_geneSig/
make menuconfig
```

　設定方法は[公式の説明](https://docs.espressif.com/projects/esp-idf/en/v3.3.1/get-started/index.html#configure)の通りですが、menuconfigの画面が出たら`Serial flasher config` > `Default serial port` と選び、ポート名を入力し、save, exitします。なおポート名は、以下の方法で調べることができます。私の環境(mac)では、`/dev/tty.SLAB_USBtoUART`です。  

```bash
ls /dev/tty.*
```  

　ポートの設定が完了したら、ESP32をPCへ接続し、プログラムを書き込みます。  

```bash
make flash
```

　プログラムの書き込みが終わり、スピーカから音楽が鳴れば成功です。  


# プログラムの説明


# さいごに

