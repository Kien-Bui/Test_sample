# Tên code file
main.py


## Cấu trúc directory
Hãy tạo cấu trúc directory như sau:


```sh
Tên folder bất kì (MAIN_PATH)/
┣ correct_imgs/
┃ ┣ Tên folder dự án bất kì (CORRECT_FOLDER)/
┃ ┃ ┣ Tên group_tên họa sĩ/
┃ ┃ ┃ ┗ Tên file bất kì.png / .jpg / .tiff / .tif
┃ ┗ name_master.xlsx
┣ src/
┃ ┣ main.py
┃ ┗ ipaexg.ttf
┣ Tên bất kì cho folder chứa ảnh cần hiệu đính (INPUT_FOLDER)/
┃ ┗ Tên file ảnh tùy ý.png / .jpg / .tiff / .tif
```


### Giải thích từng directory
- `correct_imgs/`: Directory chứa các ảnh đúng. Dưới directory này là folder của các dự án, dưới đó nữa là các folder `tên group`_`tên họa sĩ`. Các file ảnh cần lưu trữ dưới dạng png, jpg, tiff, tif.
 - `Tên folder dự án bất kì (CORRECT_FOLDER)/`: Folder theo từng dự án.
   - `Tên group_tên họa sĩ/`: Folder theo từng họa sĩ của group. Về cách tạo, hãy tham khảo file [folder.py](#グループ名_アーティスト名の自動作成:folderpy).
     - `Tên file ảnh tùy ý.png / .jpg / .tiff / .tif`: Các file ảnh.
 - `name_master.xlsx`: Tập hợp sắp xếp string của ảnh đúng.


- `src/`: Directory lưu trữ source code.
 - `main.py`: Main script file.
 - `ipaexg.ttf`: File chứa font để viết nội dung text đọc được từ OCR.


- `Tên bất kì cho folder chứa ảnh cần hiệu đính (INPUT_FOLDER)/`: Directory chứa file ảnh cần hiệu đính. Các file ảnh cần lưu trữ dưới dạng png, jpg, tiff, tif.


### Ví dụ directory
Ví dụ như khi cần hiệu đính file ảnh lưu trong folder `2024年6月` nằm trong dự án `居酒屋3弾` trên hệ thống đặt ở desktop, cấu trúc sẽ như sau:


```sh
/Users/(tên user)/Desktop/
┣ correct_imgs/
┃ ┗ 居酒屋3弾/
┃ ┃ ┣ EXILE_EXILE ATSUSHI/
┃ ┃ ┃ ┣ 01_BigAK_EX_01_ATSUSHI.jpg
┃ ┃ ┃ ┗ 01_BigAK_EX-01.jpg
┃ ┃ ┗ LIL LEAGUE_岡尾真虎/
┃ ┃ ┃ ┗ LIL_Hunter_0714修正-04.jpg
┃ ┃  …
┣ src/
┃ ┣ main.py
┃ ┗ ipaexg.ttf
┣ 2024年6月/
┃ ┗ Tên file ảnh tùy ý.png / .jpg / .tiff / .tif
```


## Cách sử dụng
1. Tạo [cấu trúc directory](#ディレクトリ構造) cần thiết, và đặt vào các file ảnh cần đối ứng.
2. Di chuyển directory tới `MAIN_PATH`.
  ```sh
  cd /path/to/MAIN_PATH
  ```
3. Install các dependencies cần thiết để dựng môi trường.
  ```sh
  pip install -r requirements.txt
  ```
4. Chạy `main.py` và hiệu đính file ảnh.
  ```sh
  python src/main.py \
   --main_path /your/main/path \
   --input_folder /your/input/folder \
   --design anime \
   --correct_imgs /your/correct_folder \
   --correct_prj /your_correct_project \
   --src /your/src \
   --threshold_value 5 \
   --shift_range 2 \
   --alert_thresh 99.94 \
   --hit 50
   ```


### Giải thích các parameter
- --main_path: Path tới main folder (default: './')
- --input_folder: Tên folder chứa ảnh design cần hiệu đính (required)
- --design: File ảnh cần hiệu đính có file anime hay không (defalut: 'anime')
- --correct_imgs: Tên folder chứa ảnh đúng (default: 'correct_folder')
- --correct_prj: Chỉ định tên dự án của ảnh đúng (required)
- --src: Path tới folder source (default: 'src')
- --threshold_value: ピクセルのズレの閾値（デフォルト: 5）
- --shift_range: 輪郭のズレの許容範囲（デフォルト: 2）
- --alert_thresh: アラートの閾値（デフォルト: 99.94）
- --hit: 特徴マッチング時のヒット値（デフォルト: 50）


#### 実行例
- デフォルト設定を使用して実行する例：


```sh
python src/main.py \
--input_folder anime_sample \
--correct_prj new
```


- すべての引数を指定して実行する例：


```sh
コードをコピーする
python src/main.py \
--main_path /home/user/project \
--input_folder /data/images \
--design anime \
--correct_imgs /data/correct_images \
--correct_prj project_123 \
--src /home/user/src \
--threshold_value 10 \
--shift_range 3 \
--alert_thresh 95.0 \
--hit 100
```




# コードファイル名
folder.py


## 処理の説明
このスクリプトは、以下の処理を行います：


必要なライブラリのインポートと警告の無視設定。
引数を解析するためのargparseモジュールの設定。
指定されたmain_pathとcorrect_imgsパスからname_master.xlsxを読み込みます。
name_master.xlsxから`「グループ名1_アーティスト名」`のフォルダを作成します。
<blockquote>name_master.xlsxの列名（１行目）に「グループ名1」と「アーティスト名」が存在する必要があります。</blockquote>


## 引数の説明
--main_path: メインのフォルダパス（デフォルト: './'）
--input_folder: 入力フォルダのパス（必須）


## 実行方法
スクリプトを実行するには、以下のコマンドを使用します：


```sh
python src/folder.py --main_path /your/main/path --input_folder /your/input/folder
```
これにより、指定されたmain_pathとcorrect_imgsのパスに基づいてフォルダ構造が作成されます。

