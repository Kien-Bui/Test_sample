# コードファイル名
main.py


## ディレクトリ構造
以下のようなディレクトリ構造を作成してください：


```sh
任意のフォルダ名 (MAIN_PATH)/
┣ correct_imgs/
┃ ┣ 任意の企画フォルダ名 (CORRECT_FOLDER)/
┃ ┃ ┣ グループ名_アーティスト名/
┃ ┃ ┃ ┗ 任意の画像のファイル名.png / .jpg / .tiff / .tif
┃ ┗ name_master.xlsx
┣ src/
┃ ┣ main.py
┃ ┗ ipaexg.ttf
┣ 任意の校正を行うデザイン画像が入ったフォルダ名 (INPUT_FOLDER)/
┃ ┗ 任意の画像のファイル名.png / .jpg / .tiff / .tif
```


### 各ディレクトリの説明
- `correct_imgs/`: 正解画像が格納されているディレクトリです。このフォルダの下には各企画フォルダが存在し、その中にグループ名_アーティスト名としたフォルダが含まれます。画像ファイルはpng, jpg, tiff, tif形式で保存してください。
 - `任意の企画フォルダ名 (CORRECT_FOLDER)/`: 各企画ごとのフォルダです。
   - `グループ名_アーティスト名/`: 各グループのアーティストごとのフォルダです。作成方法は[folder.py](#グループ名_アーティスト名の自動作成:folderpy)を参照してください。
     - `任意の画像のファイル名.png / .jpg / .tiff / .tif`: 画像ファイルです。
 - `name_master.xlsx`: 正解画像が持つ文字列を整理したものです。


- `src/`: プログラムのソースコードが格納されています。
 - `main.py`: メインのスクリプトファイルです。
 - `ipaexg.ttf`: OCRでの読み取った文字を画像に書くためのフォントファイルです。


- `任意の校正を行うデザイン画像が入ったフォルダ名 (INPUT_FOLDER)/`: 校正を行うデザイン画像が格納されています。画像ファイルはpng, jpg, tiff, tif形式で保存してください。


### ディレクトリ例
例えばデスクトップにおいたシステムで「居酒屋3弾」という企画名で「2024年6月」というフォルダに格納した画像を校正する場合は、以下のようになります：


```sh
/Users/(ユーザー名)/Desktop/
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
┃ ┗ 任意の画像のファイル名.png / .jpg / .tiff / .tif
```


## 使用方法
1. 必要な[ディレクトリ構造](#ディレクトリ構造)を作成し、対応する画像ファイルを配置します。
2. `MAIN_PATH`ディレクトリに移動します。
  ```sh
  cd /path/to/MAIN_PATH
3. 環境構築のために必要な依存関係をインストールします。
  ```sh
  pip install -r requirements.txt
4. `main.py`を実行して画像の校正を行います。
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


### 引数の説明
- --main_path: メインのフォルダパス（デフォルト: './'）
- --input_folder: 校正をするデザイン画像のフォルダ名（必須）
- --design: 校正を行うデザインがアニメかどうか（デフォルト: 'anime'）
- --correct_imgs: 正解画像が保存されているフォルダ名（デフォルト: 'correct_folder'）
- --correct_prj: 正解画像の企画名の指定（必須）
- --src: ソースフォルダのパス（デフォルト: 'src'）
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

