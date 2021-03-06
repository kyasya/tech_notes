# cuDNN5 から cuDNN6 へのアップデート
## cuDNN5 のアンインストール
以下のコードで、cuDNN5をアンインストールする。
```
cd /usr/local/cuda-8.0/lib64/
sudo rm libcudnn.so  libcudnn.so.5  libcudnn.so.5.1.10  libcudnn_static.a
cd /usr/local/cuda-8.0/include/
sudo rm cudnn.h
sudo ldconfig
```
## cuDNN6のインストール
[nvidiaホームベージ](https://developer.nvidia.com/rdp/cudnn-download)から、 一つの tar ファイルと、次の3つのdebパッケージをダウンロードする。
- cuDNN v6.0 Library for Linux (tar)
- cuDNN v6.0 Runtime Library for Ubuntu16.04 (Deb)
- cuDNN v6.0 Developer Library for Ubuntu16.04 (Deb)
- cuDNN v6.0 Code Samples and User Guide for Ubuntu16.04 (Deb)

ダウンロードしたフォルダで以下のコマンドを実行し、cuDNN のライブラリを CUDA がインストールされているディレクトリにコピーする。
```
tar -xzvf cudnn-8.0-linux-x64-v6.0.tgz
sudo cp -a cuda/lib64/* /usr/local/cuda-8.0/lib64/
sudo cp -a cuda/include/* /usr/local/cuda-8.0/include/
sudo ldconfig
```

また、ダウンロードしたフォルダで以下のコマンドを実行してインストールする。
```
# Install Runtime library
sudo dpkg -i libcudnn6_6.0*+cuda8.0_amd64.deb
# Install developer library
sudo dpkg -i libcudnn6-dev_6.0*+cuda8.0_amd64.deb
# Install code samples and user guide
sudo dpkg -i libcudnn6-doc_6.0*+cuda8.0_amd64.deb
```
その後、以下のコマンドで再起動する。
```
sudo shutdown -r now
```
