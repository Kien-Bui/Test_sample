<div class="hidden">

#kaoiri #ジャスティス

</div>

## List màn hình

|Màn hình|Note|
|:--|:--|
|Màn hình khởi động|Màn hình hiển thị khi chưa load được thông tin Khách hàng|
|Màn hình Liệu pháp đang chờ (Chia tab Schedule (スケジュール) và Hồ sơ (カルテタブ))|Màn hình hiển thị khi tất cả thủ thuật có mục Ngày giờ bắt đầu thủ thuật và Ngày giờ kết thúc thủ thuật đều NULL hoặc đều không NULL|
|Màn hình Liệu pháp đang thực hiện (Chia tab Schedule (スケジュール) và Hồ sơ (カルテタブ))|Màn hình hiển thị khi có thủ thuật có mục Ngày giờ bắt đầu thủ thuật không NULL và Ngày giờ kết thúc thủ thuật NULL|
|Màn hình chỉnh sửa Phụ trách|Màn hình hiển thị khi bấm vào tên của người phụ trách|
|Màn hình chờ thanh toán|Màn hình hiển thị khi đã hoàn thành tất cả thủ thuật|


## List tính năng theo màn hình

### Màn hình khởi động

![スタート画面.png](./attachments/スタート画面.png)

<table>
    <thead>
        <tr>
            <th>Area</th>
            <th>Tính năng</th>
            <th>Phân loại</th>
            <th>Giải thích</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <th>①</th>
            <td>Hiển thị tên khách hàng</td>
            <td>Hiển thị</td>
            <td>Thể hiện đang không đọc thông tin nào</td>
        </tr>
        <tr>
            <th>①</th>
            <td>Hiện thị người phụ trách</td>
            <td>Hiển thị</td>
            <td>Thể hiện đang không đọc thông tin nào</td>
        </tr>
        <tr>
            <th>①</th>
            <td>Hiển thị thông tin Hồ sơ</td>
            <td>Hiển thị</td>
            <td>Không hiển thị</td>
        </tr>
        <tr>
            <th>②</th>
            <td>Hiển thị status Liệu pháp</td>
            <td>Hiển thị</td>
            <td>
                <ul>
                    <li>Hiển thị nội dung「空席」</li>
                    <li>Status chia làm 3 loại, phân chia màu.</li>
                    <ul>
                        <li>空席 (Trống)</li>
                        <li>施術待機中 (Liệu pháp đang chờ)</li>
                        <li>施術中 (Liệu pháp đang thực hiện)</li>
                    </ul>
                </ul>
            </td>
        </tr>
        <tr>
            <th>③</th>
            <td>Thực hiện tiếp thao tác tiếp theo</td>
            <td>Button</td>
            <td>
            <ul>
                <li>Hiển thị nội dung「お客さまを座席に案内する」</li>
                <li>Thao tác được chia làm 3 loại sau, phân chia màu</li>
                <ul>
                    <li>施術客を座席に案内する (Hướng dẫn Khách hàng tới ghế chờ)</li>
                    <li>施術開始 (Bắt đầu Liệu pháp)</li>
                    <li>施術終了 (Kết thúc Liệu pháp)</li>
                </ul>
                <li>Khi bấm vào thì thực hiện những xử lý sau</li>
                <ul>
                    <li>Đọc ID Liệu pháp từ QR code bằng camera</li>
                    <li>Ghi thời gian bắt đầu Liệu pháp vào DB</li>
                    <li>Chuyển tới màn hình Liệu pháp đang chờ</li>
                </ul>
            </ul>
            </td>
        </tr>
        <tr>
            <th>④</th>
            <td>Edit schedule</td>
            <td>Thao tác, thay đổi, cập nhật data</td>
            <td>Không hiển thị hoặc thể hiện không thể edit được</td>
        </tr>
        <tr>
            <th>④</th>
            <td>Edit Hồ sơ</td>
            <td>Thao tác, thay đổi, cập nhật data</td>
            <td>Không hiển thị hoặc thể hiện không thể edit được</td>
        </tr>
    </tbody>
</table>

<div style="page-break-before:always"></div>

### Màn hình Liệu pháp đang chờ (Chia tab Schedule (スケジュール) và Hồ sơ (カルテタブ))

![施術待機画面（スケジュールタブ）.png](./attachments/施術待機画面（スケジュールタブ）.png)

![施術待機画面（カルテタブ）.png](./attachments/施術待機画面（カルテタブ）.png)

<table>
    <thead>
        <tr>
            <th>Area</th>
            <th>Tính năng</th>
            <th>Phân loại</th>
            <th>Giải thích</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <th>①</th>
            <td>Hiển thị tên Khách hàng</td>
            <td>Hiển thị</td>
            <td>Đọc thông tin Khách hàng từ DB bằng ID Khách hàng, hiển thị tên của Khách hàng tương ứng</td>
        </tr>
        <tr>
            <th>①</th>
            <td>Hiển thị, edit người phụ trách thủ thuật</td>
            <td>Hiển thị/Button</td>
            <td>Biểu hiện chưa có thông tin người phụ trách</td>
        </tr>
        <tr>
            <th>①</th>
            <td>Hiển thị thông tin Hồ sơ</td>
            <td>Hiển thị</td>
            <td>
                <ul>
                    <li>Đọc thông tin Khách hàng từ DB bằng ID Khách hàng, hiển thị nhưng thông tin dưới đây bằng icon</li>
                    <ul>
                        <li>Trải nghiệm trong salon</li>
                    </ul>
                </ul>
            </td>
        </tr>
        <tr>
            <th>②</th>
            <td>Hiển thị status Liệu pháp</td>
            <td>Hiển thị</td>
            <td>
                <ul>
                    <li>Đọc thông tin schedule Liệu pháp (list thủ thuật) từ DB bằng ID Khách hàng hoặc bằng ID Liệu pháp, hiển thị status hiện tại</li>
                    <li>Status chia làm 3 loại sau, phân chia màu</li>
                    <ul>
                        <li>空席 (Trống)</li>
                        <li>施術待機中 (Liệu pháp đang chờ)</li>
                        <li>施術中 (Liệu pháp đang thực hiện)</li>
                    </ul>
                    <li>Vì button hiển thị trên màn hình này được phân loại là 「施術開始」 (Bắt đầu Liệu pháp), nội dung hiển thị sẽ có bao gồm「.+待機中」</li>
                    <li>Trong trường hợp chưa có Thủ thuật thì hiển thị nội dung「カウンセリング待機中」</li>
                </ul>
            </td>
        </tr>
        <tr>
            <th>③</th>
            <td>Thực hiện tiếp thao tác tiếp theo</td>
            <td>Button</td>
            <td>
                <ul>
                    <li>Đọc thông tin schedule Liệu pháp (list thủ thuật) từ DB bằng ID Khách hàng hoặc bằng ID Liệu pháp, hiển thị thao tác tiếp theo</li>
                    <li>Thao tác được chia làm 3 loại sau, phân chia màu</li>
                <ul>
                    <li>施術客を座席に案内する (Hướng dẫn Khách hàng tới ghế chờ)</li>
                    <li>施術開始 (Bắt đầu Liệu pháp)</li>
                    <li>施術終了 (Kết thúc Liệu pháp)</li>
                    </ul>
                    <li>Vì nội dung hiển thị trên màn hình này được phân loại là Liệu pháp đang chờ nội dung hiển thị sẽ có bao gồm「.+待機中」</li>
                    <li>Khi bấm vào thì thực hiện những xử lý sau</li>
                    <ul>
                        <li>Đọc Staff ID từ QR code bằng camera</li>
                        <li>Ghi thời gian bắt đầu Thủ thuật vào DB</li>
                        <li>Đọc thông tin schedule Liệu pháp (list thủ thuật) từ DB bằng ID Khách hàng hoặc bằng ID Liệu pháp, chuyển sang màn hình Liệu pháp đang thực hiện theo đúng thông tin đó</li>
                    </ul>
                    <li>Trong trường hợp chưa tạo schedule cho Liệu pháp (chưa có Thủ thuật), hiển thị nội dung「カウンセリングを始める」</li>
                </ul>
            </td>
        </tr>
        <tr>
            <th>④</th>
            <td>Edit schedule</td>
            <td>Thao tác, thay đổi, cập nhật data</td>
            <td>
                <ul>
                    <li>Hiển thị list menu dưới đây</li>
                    <ul>
                        <li>カウンセリング</br>Counseling</li>
                        <li>カット</br>Cắt</li>
                        <li>シャンプー</br>Gội</li>
                        <li>トリートメント</br>Dưỡng</li>
                        <li>眉カット</br>Tỉa lông mày</li>
                        <li>カラー</br>Nhuộm</li>
                        <li>ブリーチ</br>Tẩy</li>
                        <li>パーマ</br>Uốn</li>
                        <li>ヘアセット</br>Tạo kiểu</li>
                        <li>マッサージ</br>Massage</li>
                    </ul>
                    <li>Hiển thị schedule đã đọc được từ ID Khách hàng hoặc ID Liệu pháp</li>
                    <li>Hiển thị highlight menu đang được thực hiện trong schedule Liệu pháp (cùng màu với status LIệu pháp)</li>
                    <li>Có thể edit được schedule bằng cách bấm vào tên menu hoặc kéo và thả menu</li>
                    <li>Khi schedule được edit thì lưu lại nội dung được sửa vào DB</li>
                </ul>
            </td>
        </tr>
        <tr>
            <th>④</th>
            <td>Edit Hồ sơ</td>
            <td>Thao tác, thay đổi, cập nhật data</td>
            <td>
                <ul>
                    <li>Hiểu thị thông tin Hồ sơ đọc được từ ID Khách hàng trên form</li>
                    <li>Khi form được edit thì lưu lại nội dung được sửa vào DB</li>
                    <li>Nội dung Hồ sơ như sau</li>
                    <ul>
                        <li>氏名：テキスト</br>Họ tên: text</li>
                        <li>フリガナ：テキスト</br>Furigana: text</li>
                        <li>郵便番号：テキスト</br>Mã bưu điện: text</li>
                        <li>住所：テキスト</br>Địa chỉ: text</li>
                        <li>生年月日：日付</br>Ngày sinh: ngày tháng năm</li>
                        <li>電話番号：テキスト</br>Số điện thoại: text</li>
                        <li>メールアドレス：テキスト</br>Địa chỉ email: text</li>
                        <li>職業：単一選択</br>Nghề nghiệp: chọn trong list dưới đây</li>
                        <ol>
                            <li>会社員</br>Nhân viên văn phòng</li>
                            <li>学生</br>Học sinh/Sinh viên</li>
                            <ul>
                                <li>高</br>Cấp 3</li>
                                <li>大</br>Đại học</li>
                                <li>専</br>Trường nghề</li>
                            </ul>
                            <li>その他：テキスト</br>Khác: nhập text</li>
                        </ol>
                        <li>店を知ったきっかけ：単一選択</br>Cách biết tới tiệm: chọn trong list dưới đây</li>
                        <ol>
                            <li>紹介：テキスト（紹介者名）</br>Giới thiệu: text (tên người giới thiệu)</li>
                            <li>美容学生：テキスト（学校名）</br>Sinh viên trường thẩm mĩ: text (tên trường)</li>
                            <li>Google検索</br>Google search</li>
                            <li>ホットペッパー</br>(HotPepper)[https://www.hotpepper.jp/]</li>
                            <li>Instagram</li>
                            <li>minimo</li>
                            <li>その他SNS：テキスト</br>SNS khác: nhập text</li>
                            <li>ホームページ</br>Website của tiệm</li>
                            <li>チラシ</br>Tờ rơi</li>
                            <li>通りすがり</br>Đi qua</li>
                        </ol>
                        <li>サロン内での過ごし方：複数選択</br>Trải nghiệm trong salon</li>
                        <ol>
                            <li>なるべく会話は控えたい</br>Muốn tránh nói chuyện nhiều nhất có thể</li>
                            <li>スタッフとの会話を楽しみたい</br>Muốn nói chuyện cùng các staff</li>
                            <li>タブレット端末でデジタル雑誌を読みたい</br>Muốn đọc tạp chí trên tablet</li>
                            <li>ご自身のスマホを利用したい</br>Muốn sử dụng smartphone của bản thân</li>
                            <li>施術内容についての説明を聞きたい</br>Muốn nghe giải thích về nội dung liệu pháp</li>
                        </ol>
                        <li>シャンプーやヘッドスパでの力加減：単一選択</br>Mức độ dùng sức mong muốn khi gội, ấp: lựa chọn dưới đây</li>
                        <ol>
                            <li>強め</br>Mạnh</li>
                            <li>やや強め</br>Mạnh vừa phải</li>
                            <li>普通</br>Thường</li>
                            <li>やや弱め</br>Nhẹ vừa phải</li>
                            <li>弱め</br>Nhẹ</li>
                            <li>その都度確認してほしい</br>Muốn được xác nhận khi thực hiện</li>
                        </ol>
                        <li>今までの美容室で気になったこと：複数選択</br>Những điểm có từng thắc mắc ở thẩm mĩ viện trước đây: lựa chọn nhiều</li>
                        <ol>
                            <li>仕上がり</br>Hoàn thành</li>
                            <li>技術</br>Kĩ thuật</li>
                            <li>接客</br>Tiếp khách</li>
                            <li>施術時間</br>Thời gian liệu pháp</li>
                            <li>店内の清潔さ</br>Mức sạch sẽ trong tiệm</li>
                            <li>その他：テキスト</br>Khác: nhập text</li>
                        </ol>
                        <li>なりたいイメージ：複数選択</br>Mong muốn trở nên ra sao: chọn nhiều</li>
                        <ol>
                            <li>かわいい</br>Đáng yêu</li>
                            <li>ナチュラル</br>Tự nhiên</li>
                            <li>モテ、愛され</br>Được chú ý, yêu mến</li>
                            <li>かっこいい</br>Cool, ngầu</li>
                            <li>大人っぽく</br>Trưởng thành hơn</li>
                            <li>似合うようにしてほしい</br>Muốn (kiểu tóc) trông hợp với mình</li>
                        </ol>
                        <li>髪についての悩み：複数選択</br>Điểm lo lắng về mái tóc bản thân</li>
                        <ol>
                            <li>ダメージ</br>Hư tổn</li>
                            <li>カラーの色持ち</br>Lên màu</li>
                            <li>パーマの持ち</br>Giữ nếp uốn</li>
                            <li>クセや広がり</br>Gãy, chẻ</li>
                            <li>ボリュームが出にくい</br>Lượng tóc trông không đủ nhiều</li>
                            <li>ホームケアの仕方</br>Cách dưỡng tóc ở nhà</li>
                            <li>スタイリングの仕方</br>Các tạo kiểu</li>
                            <li>その他：テキスト</br>Khác: nhập text</li>
                        </ol>
                        <li>当日の仕上がりイメージ：テキスト</br>Mong muốn hoàn thành ra sao: nhập text</li>
                        <li>施術履歴：データベースから</br>Lịch sử các liệu pháp: lấy từ DB</li>
                        <li>過去半年以内に行った施術：複数選択</br>Các liệu pháp thực hiện trong nửa năm trở lại: chọn nhiều</li>
                        <ol>
                            <li>黒染め</br>Nhuộm đen</li>
                            <li>ブリーチ</br>Tẩy</li>
                            <li>縮毛矯正</br>Duỗi</li>
                            <li>デジタルパーマ</br>Uốn kĩ thuật số</li>
                            <li>ストレートパーマ</br>Uốn thẳng</li>
                        </ol>
                        <li>希望の仕上がり時間：単一選択</br>Mong muốn thời gian hoàn thành: chọn một</li>
                        <ol>
                            <li>急いでいる：時刻（希望終了時刻）</br>Gấp: giờ (giờ kết thúc)</li>
                            <li>急いでいないが希望がある：時刻（希望終了時刻）</br>Không vội nhưng có giới hạn giờ: giờ (giờ kết thúc)</li>
                            <li>特にない</br>Không vội</li>
                        </ol>
                        <li>施術メニュー以外に興味のあるメニュー：複数選択</br>Có quan tâm menu khác ngoài Liệu pháp đang dùng: chọn nhiều</li>
                        <ol>
                            <li>カット</br>Cắt</li>
                            <li>カラー</br>Nhuộm</li>
                            <li>インナーカラー</br>Nhuộm trong</br></li>
                            <li>パーマ</br>Uốn</li>
                            <li>デジタルパーマ</br>Uốn kĩ thuật số</li>
                            <li>縮毛矯正</br>Duỗi</br></li>
                            <li>トリートメント</br>Dưỡng</li>
                            <li>ヘッドスパ</br>Hấp</li>
                            <li>眉カット</br>Tỉa lông mày</li>
                            <li>その他：テキスト</br>Khác: nhập text</li>
                        </ol>
                        <li>おすすめ商品の紹介を希望するか：単一選択</br>Có muốn được giới thiệu thêm sản phẩm không</li>
                        <ol>
                            <li>はい</br>Có</li>
                            <li>いいえ</br>Không</li>
                        </ol>
                        <li>自宅でのヘアケアについて：単一選択</br>Chăm sóc tóc tại nhà: chọn một</li>
                        <ol>
                            <li>サロンで購入したもの</br>Bằng sản phẩm mua từ salon</li>
                            <li>市販のもの</br>Bằng sản phẩm mua ngoài</li>
                            <li>特にしていない</br>Không làm gì</li>
                        </ol>
                        <li>利用しているSNS：複数選択</br>Đang dùng SNS: chọn nhiều</li>
                        <ol>
                            <li>Instagram</li>
                            <li>Twitter</li>
                            <li>TikTok</li>
                            <li>LINE</li>
                            <li>Facebook</li>
                            <li>YouTube</li>
                            <li>Clubhouse</li>
                            <li>その他：テキスト</br>Khác: nhập text</li>
                        </ol>
                        <li>その他の要望：テキストエリア</br>Mong muốn khác: khung nhập text</li>
                        <li>管理用メモ：テキストエリア</br>Note quản lý: khung nhập text</li>
                    </ul>
                </ul>
            </td>
        </tr>
        <tr>
            <th>⑤</th>
            <td>Quay lại với màn khởi động</td>
            <td>Button</td>
            <td>
                <ul>
                    <li>Khi bấm vào thì thực hiện xử lý sau</li>
                    <ul>
                        <li>Quay trở lại màn hình khởi động (Home)</li>
                    </ul>
                </ul>
            </td>
        </tr>
    </tbody>
</table>

<div style="page-break-before:always"></div>

### Màn hình Liệu pháp đang thực hiện (Chia tab Schedule (スケジュール) và Hồ sơ (カルテタブ))

![施術中画面（スケジュールタブ）.png](./attachments/施術中画面（スケジュールタブ）.png)

![施術中画面（カルテタブ）.png](./attachments/施術中画面（カルテタブ）.png)

<table>
    <thead>
        <tr>
            <th>Area</th>
            <th>Tính năng</th>
            <th>Phân loại</th>
            <th>Giải thích</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <th>①</th>
            <td>Hiển thị tên Khách hàng</td>
            <td>Hiển thị</td>
            <td>Đọc thông tin Khách hàng từ DB bằng ID Khách hàng, hiển thị tên của Khách hàng tương ứng</td>
        </tr>
        <tr>
            <th>①</th>
            <td>Hiển thị, edit người phụ trách thủ thuật</td>
            <td>Hiển thị/Button</td>
            <td>
                <ul>
                    <li>Đọc thông tin người phụ trách từ DB bằng ID Thủ thuật của thủ thuật đang thực hiện, hiển thị ra tên của tất cả người phụ trách của những thủ thuật chưa có giờ kết thúc</li>
                    <li>Khi bấm vào thì thực hiện xử lý sau</li>
                    <ul>
                        <li>Chuyển sang màn hình Chỉnh sửa phụ trách (担当者編集画面)</li>
                    </ul>
                </ul>
            </td>
        </tr>
        <tr>
            <th>①</th>
            <td>Hiển thị thông tin Hồ sơ</td>
            <td>Hiển thị</td>
            <td>
                <ul>
                    <li>Đọc thông tin Khách hàng từ DB bằng ID Khách hàng, hiển thị nhưng thông tin dưới đây bằng icon</li>
                    <ul>
                        <li>Trải nghiệm trong salon</li>
                    </ul>
                </ul>
            </td>
        </tr>
        <tr>
            <th>②</th>
            <td>Hiển thị status Liệu pháp</td>
            <td>Hiển thị</td>
            <td>
                <ul>
                    <li>Đọc thông tin schedule Liệu pháp (list thủ thuật) từ DB bằng ID Khách hàng hoặc bằng ID Liệu pháp, hiển thị status hiện tại</li>
                    <li>Status chia làm 3 loại sau, phân chia màu</li>
                    <ul>
                        <li>空席 (Trống)</li>
                        <li>施術待機中 (Liệu pháp đang chờ)</li>
                        <li>施術中 (Liệu pháp đang thực hiện)</li>
                    </ul>
                    <li>Vì button hiển thị trên màn hình này được phân loại là 「施術中」 (Đang thực hiện Liệu pháp), nội dung hiển thị sẽ có bao gồm「.+中」</li>
                </ul>
            </td>
        </tr>
        <tr>
            <th>③</th>
            <td>Thực hiện tiếp thao tác tiếp theo</td>
            <td>Button</td>
            <td>
                <ul>
                    <li>Đọc thông tin schedule Liệu pháp (list thủ thuật) từ DB bằng ID Khách hàng hoặc bằng ID Liệu pháp, hiển thị thao tác tiếp theo</li>
                    <li>Thao tác được chia làm 3 loại sau, phân chia màu</li>
                <ul>
                    <li>施術客を座席に案内する (Hướng dẫn Khách hàng tới ghế chờ)</li>
                    <li>施術開始 (Bắt đầu Liệu pháp)</li>
                    <li>施術終了 (Kết thúc Liệu pháp)</li>
                    </ul>
                    <li>Vì button hiển thị trên màn hình này được phân loại là 「施術終了」 (Kết thúc Liệu pháp), nội dung hiển thị sẽ có bao gồm「.+を終了する」</li>
                    <li>Khi bấm vào thì thực hiện những xử lý sau</li>
                    <ul>
                        <li>Ghi thời gian kết thúc thủ thuật vào DB</li>
                        <li>Đọc thông tin schedule Liệu pháp (list thủ thuật) từ DB bằng ID Khách hàng hoặc bằng ID Liệu pháp, chuyển sang những màn hình sau</li>
                        <ul>
                            <li>Trường hợp còn Thủ thuật sau: Màn hình Liệu pháp đang chờ (施術待機画面)</li>
                            <li>Trường hợp không còn Thủ thuật nào: Màn hình chờ thanh toán (会計待機画面)</li>
                        </ul>
                    </ul>
                </ul>
            </td>
        </tr>
        <tr>
            <th>④</th>
            <td>Edit schedule</td>
            <td>Thao tác, thay đổi, cập nhật data</td>
            <td>
                <ul>
                    <li>Hiển thị list menu dưới đây</li>
                    <ul>
                        <li>カウンセリング</br>Counseling</li>
                        <li>カット</br>Cắt</li>
                        <li>シャンプー</br>Gội</li>
                        <li>トリートメント</br>Dưỡng</li>
                        <li>眉カット</br>Tỉa lông mày</li>
                        <li>カラー</br>Nhuộm</li>
                        <li>ブリーチ</br>Tẩy</li>
                        <li>パーマ</br>Uốn</li>
                        <li>ヘアセット</br>Tạo kiểu</li>
                        <li>マッサージ</br>Massage</li>
                    </ul>
                    <li>Hiển thị schedule đã đọc được từ ID Khách hàng hoặc ID Liệu pháp</li>
                    <li>Hiển thị highlight menu đang được thực hiện trong schedule Liệu pháp (cùng màu với status LIệu pháp)</li>
                    <li>Có thể edit được schedule bằng cách bấm vào tên menu hoặc kéo và thả menu</li>
                    <li>Khi schedule được edit thì lưu lại nội dung được sửa vào DB</li>
                </ul>
            </td>
        </tr>
        <tr>
            <th>④</th>
            <td>Edit Hồ sơ</td>
            <td>Thao tác, thay đổi, cập nhật data</td>
            <td>
                <ul>
                    <li>Hiểu thị thông tin Hồ sơ đọc được từ ID Khách hàng trên form</li>
                    <li>Khi form được edit thì lưu lại nội dung được sửa vào DB</li>
                    <li>Nội dung Hồ sơ như sau</li>
                    <ul>
                        <li>氏名：テキスト</br>Họ tên: text</li>
                        <li>フリガナ：テキスト</br>Furigana: text</li>
                        <li>郵便番号：テキスト</br>Mã bưu điện: text</li>
                        <li>住所：テキスト</br>Địa chỉ: text</li>
                        <li>生年月日：日付</br>Ngày sinh: ngày tháng năm</li>
                        <li>電話番号：テキスト</br>Số điện thoại: text</li>
                        <li>メールアドレス：テキスト</br>Địa chỉ email: text</li>
                        <li>職業：単一選択</br>Nghề nghiệp: chọn trong list dưới đây</li>
                        <ol>
                            <li>会社員</br>Nhân viên văn phòng</li>
                            <li>学生</br>Học sinh/Sinh viên</li>
                            <ul>
                                <li>高</br>Cấp 3</li>
                                <li>大</br>Đại học</li>
                                <li>専</br>Trường nghề</li>
                            </ul>
                            <li>その他：テキスト</br>Khác: nhập text</li>
                        </ol>
                        <li>店を知ったきっかけ：単一選択</li>
                        <li>店を知ったきっかけ：単一選択</br>Cách biết tới tiệm: chọn trong list dưới đây</li>
                        <ol>
                            <li>紹介：テキスト（紹介者名）</br>Giới thiệu: text (tên người giới thiệu)</li>
                            <li>美容学生：テキスト（学校名）</br>Sinh viên trường thẩm mĩ: text (tên trường)</li>
                            <li>Google検索</br>Google search</li>
                            <li>ホットペッパー</br>(HotPepper)[https://www.hotpepper.jp/]</li>
                            <li>Instagram</li>
                            <li>minimo</li>
                            <li>その他SNS：テキスト</br>SNS khác: nhập text</li>
                            <li>ホームページ</br>Website của tiệm</li>
                            <li>チラシ</br>Tờ rơi</li>
                            <li>通りすがり</br>Đi qua</li>
                        </ol>
                        <li>サロン内での過ごし方：複数選択</br>Trải nghiệm trong salon</li>
                        <ol>
                            <li>なるべく会話は控えたい</br>Muốn tránh nói chuyện nhiều nhất có thể</li>
                            <li>スタッフとの会話を楽しみたい</br>Muốn nói chuyện cùng các staff</li>
                            <li>タブレット端末でデジタル雑誌を読みたい</br>Muốn đọc tạp chí trên tablet</li>
                            <li>ご自身のスマホを利用したい</br>Muốn sử dụng smartphone của bản thân</li>
                            <li>施術内容についての説明を聞きたい</br>Muốn nghe giải thích về nội dung liệu pháp</li>
                        </ol>
                        <li>シャンプーやヘッドスパでの力加減：単一選択</br>Mức độ dùng sức mong muốn khi gội, ấp: lựa chọn dưới đây</li>
                        <ol>
                            <li>強め</br>Mạnh</li>
                            <li>やや強め</br>Mạnh vừa phải</li>
                            <li>普通</br>Thường</li>
                            <li>やや弱め</br>Nhẹ vừa phải</li>
                            <li>弱め</br>Nhẹ</li>
                            <li>その都度確認してほしい</br>Muốn được xác nhận khi thực hiện</li>
                        </ol>
                        <<li>今までの美容室で気になったこと：複数選択</br>Những điểm có từng thắc mắc ở thẩm mĩ viện trước đây: lựa chọn nhiều</li>
                        <ol>
                            <li>仕上がり</br>Hoàn thành</li>
                            <li>技術</br>Kĩ thuật</li>
                            <li>接客</br>Tiếp khách</li>
                            <li>施術時間</br>Thời gian liệu pháp</li>
                            <li>店内の清潔さ</br>Mức sạch sẽ trong tiệm</li>
                            <li>その他：テキスト</br>Khác: nhập text</li>
                        </ol>
                        <li>なりたいイメージ：複数選択</br>Mong muốn trở nên ra sao: chọn nhiều</li>
                        <ol>
                            <li>かわいい</br>Đáng yêu</li>
                            <li>ナチュラル</br>Tự nhiên</li>
                            <li>モテ、愛され</br>Được chú ý, yêu mến</li>
                            <li>かっこいい</br>Cool, ngầu</li>
                            <li>大人っぽく</br>Trưởng thành hơn</li>
                            <li>似合うようにしてほしい</br>Muốn (kiểu tóc) trông hợp với mình</li>
                        </ol>
                        <li>髪についての悩み：複数選択</br>Điểm lo lắng về mái tóc bản thân</li>
                        <ol>
                            <li>ダメージ</br>Hư tổn</li>
                            <li>カラーの色持ち</br>Lên màu</li>
                            <li>パーマの持ち</br>Giữ nếp uốn</li>
                            <li>クセや広がり</br>Gãy, chẻ</li>
                            <li>ボリュームが出にくい</br>Lượng tóc trông không đủ nhiều</li>
                            <li>ホームケアの仕方</br>Cách dưỡng tóc ở nhà</li>
                            <li>スタイリングの仕方</br>Các tạo kiểu</li>
                            <li>その他：テキスト</br>Khác: nhập text</li>
                        </ol>
                        <li>当日の仕上がりイメージ：テキスト</br>Mong muốn hoàn thành ra sao: nhập text</li>
                        <li>施術履歴：データベースから</br>Lịch sử các liệu pháp: lấy từ DB</li>
                        <li>過去半年以内に行った施術：複数選択</br>Các liệu pháp thực hiện trong nửa năm trở lại: chọn nhiều</li>
                        <ol>
                            <li>黒染め</br>Nhuộm đen</li>
                            <li>ブリーチ</br>Tẩy</li>
                            <li>縮毛矯正</br>Duỗi</li>
                            <li>デジタルパーマ</br>Uốn kĩ thuật số</li>
                            <li>ストレートパーマ</br>Uốn thẳng</li>
                        </ol>
                        <li>希望の仕上がり時間：単一選択</br>Mong muốn thời gian hoàn thành: chọn một</li>
                        <ol>
                            <li>急いでいる：時刻（希望終了時刻）</br>Gấp: giờ (giờ kết thúc)</li>
                            <li>急いでいないが希望がある：時刻（希望終了時刻）</br>Không vội nhưng có giới hạn giờ: giờ (giờ kết thúc)</li>
                            <li>特にない</br>Không vội</li>
                        </ol>
                        <li>施術メニュー以外に興味のあるメニュー：複数選択</br>Có quan tâm menu khác ngoài Liệu pháp đang dùng: chọn nhiều</li>
                        <ol>
                            <li>カット</br>Cắt</li>
                            <li>カラー</br>Nhuộm</li>
                            <li>インナーカラー</br>Nhuộm trong</br></li>
                            <li>パーマ</br>Uốn</li>
                            <li>デジタルパーマ</br>Uốn kĩ thuật số</li>
                            <li>縮毛矯正</br>Duỗi</br></li>
                            <li>トリートメント</br>Dưỡng</li>
                            <li>ヘッドスパ</br>Hấp</li>
                            <li>眉カット</br>Tỉa lông mày</li>
                            <li>その他：テキスト</br>Khác: nhập text</li>
                        </ol>
                        <li>おすすめ商品の紹介を希望するか：単一選択</br>Có muốn được giới thiệu thêm sản phẩm không</li>
                        <ol>
                            <li>はい</br>Có</li>
                            <li>いいえ</br>Không</li>
                        </ol>
                        <li>自宅でのヘアケアについて：単一選択</br>Chăm sóc tóc tại nhà: chọn một</li>
                        <ol>
                            <li>サロンで購入したもの</br>Bằng sản phẩm mua từ salon</li>
                            <li>市販のもの</br>Bằng sản phẩm mua ngoài</li>
                            <li>特にしていない</br>Không làm gì</li>
                        </ol>
                        <li>利用しているSNS：複数選択</br>Đang dùng SNS: chọn nhiều</li>
                        <ol>
                            <li>Instagram</li>
                            <li>Twitter</li>
                            <li>TikTok</li>
                            <li>LINE</li>
                            <li>Facebook</li>
                            <li>YouTube</li>
                            <li>Clubhouse</li>
                            <li>その他：テキスト</br>Khác: nhập text</li>
                        </ol>
                        <li>その他の要望：テキストエリア</br>Mong muốn khác: khung nhập text</li>
                        <li>管理用メモ：テキストエリア</br>Note quản lý: khung nhập text</li>
                    </ul>
                </ul>
            </td>
        </tr>
        <tr>
            <th>⑤</th>
            <td>Quay lại với màn khởi động</td>
            <td>Button</td>
            <td>
                <ul>
                    <li>Khi bấm vào thì thực hiện xử lý sau</li>
                    <ul>
                        <li>Quay trở lại màn hình khởi động (Home)</li>
                    </ul>
                </ul>
            </td>
        </tr>
    </tbody>
</table>

<div style="page-break-before:always"></div>

### Màn hình chỉnh sửa Phụ trách

![担当者操作画面.png](./attachments/担当者操作画面.png)

<table>
    <thead>
        <tr>
            <th>Area</th>
            <th>Tính năng</th>
            <th>Phân loại</th>
            <th>Giải thích</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <th>①</th>
            <td>Bổ sung người phụ trách</td>
            <td>Button</td>
            <td>
                <ul>
                    <li>Khi tap sẽ thực hiện thao tác dưới đây.</li>
                    <ul>
                        <li>Scan Staff ID từ mã QR bằng camera</li>
                        <li>Lưu staff ID và thời gian bắt đầu phục trách là người phụ trách công việc vào data base</li>
                    </ul>
                </ul>
            </td>
        </tr>
        <tr>
            <th>①</th>
            <td>Thay đổi người phụ trách</td>
            <td>Button</td>
            <td>
                <ul>
                    <li>Khi tap sẽ thực hiện thao tác như dưới đây.</li>
                    <ul>
                        <li>Thêm thời gian kết thúc phụ trách vào người phụ trách công việc đã tap rồi update database</li>
                        <li>Scan staff ID từ mã QR bằng camera</li>
                        <li>Lưu staff ID và thời gian bắt đầu phục trách là người phụ trách công việc vào data base</li>
                    </ul>
                </ul>
            </td>
        </tr>
        <tr>
            <th>①</th>
            <td>Xóa người phụ trách</td>
            <td>Button</td>
            <td>
                <ul>
                    <li>Khi tap sẽ thực hiện thao tác như dưới đây.</li>
                    <ul>
                        <li>Thêm thời gian kết thúc phụ trách vào người phụ trách công việc đã tap rồi update database</li>
                    </ul>
                </ul>
            </td>
        </tr>
    </tbody>
</table>

<div style="page-break-before:always"></div>

### Màn hình chờ thanh toán

![会計待機画面.png](./attachments/会計待機画面.png)

<table>
    <thead>
        <tr>
            <th>Area</th>
            <th>Tính năng</th>
            <th>Phân loại</th>
            <th>Giải thích</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <th>①</th>
            <td>Hiển thị tên khách hàng</td>
            <td>Hiển thị</td>
            <td>Đọc thông tin khách hàng từ data base bằng ID khách hàng, và cho hiển thị tên khách hàng</td>
        </tr>
        <tr>
            <th>①</th>
            <td>Hiển thị・Edit người phụ trách công việc</td>
            <td>Hiển thị・Button</td>
            <td>Trình bày rõ người phụ trách chưa được đăng kí</td>
        </tr>
        <tr>
            <th>①</th>
            <td>Hiển thị thông tin Hồ sơ</td>
            <td>Hiển thị</td>
            <td>
                <ul>
                    <li>Đọc thông tin Hồ sơ từ data base bằng ID khách hàng, sau đó hiển thị thông tin dưới đây dưới dạng icon</li>
                    <ul>
                        <li>Cách dành thời gian ở salon</li>
                    </ul>
                </ul>
            </td>
        </tr>
        <tr>
            <th>②</th>
            <td>Hiển thị status liệu pháp</td>
            <td>Hiển thị</td>
            <td>
                <ul>
                    <li>HIển thị「会計待機中」(đang đợi thanh toán)</li>
                    <li>Status sẽ được phân làm 3 loại như dưới đây và được phân màu</li>
                    <ul>
                        <li>空席(trống)</li>
                        <li>施術待機中(Đang đợi thực hiện liệu pháp)</li>
                        <li>施術中(Đang thực hiện liệu pháp)</li>
                    </ul>
                </ul>
            </td>
        </tr>
        <tr>
            <th>③</th>
            <td>Thực hiện action tiếp theo</td>
            <td>Button</td>
            <td>
                <ul>
                    <li>Hiển thị「作業を終了して会計に進む」(Kết thúc liệu pháp, tiếp tục thanh toán)</li>
                    <li>Action sẽ được phân làm 3 loại như dưới đây, và được phân màu</li>
                    <ul>
                        <li>施術客を座席に案内する(Dẫn khách hàng vào chỗ ngồi)</li>
                        <li>施術開始(Bắt đầu liệu pháp)</li>
                        <li>施術終了(Kết thúc liệu pháp)</li>
                    </ul>
                    <li>Khi tap sẽ thực hiện xử lý như dưới đây</li>
                    <ul>
                        <li>Đăng kí thời gian kết thúc liệu pháp vào data base</li>
                        <li>Di chuyển sang「スタート画面」(màn start)</li>
                    </ul>
                </ul>
            </td>
        </tr>
        <tr>
            <th>④</th>
            <td>Edit schedule</td>
            <td>Thao tác, thay đổi, cập nhật data</td>
            <td>
                <ul>
                    <li>Hiển thị list menu dưới đây</li>
                    <ul>
                        <li>カウンセリング</br>Counseling</li>
                        <li>カット</br>Cắt</li>
                        <li>シャンプー</br>Gội</li>
                        <li>トリートメント</br>Dưỡng</li>
                        <li>眉カット</br>Tỉa lông mày</li>
                        <li>カラー</br>Nhuộm</li>
                        <li>ブリーチ</br>Tẩy</li>
                        <li>パーマ</br>Uốn</li>
                        <li>ヘアセット</br>Tạo kiểu</li>
                        <li>マッサージ</br>Massage</li>
                    </ul>
                    <li>Hiển thị schedule đã đọc được từ ID Khách hàng hoặc ID Liệu pháp</li>
                    <li>Hiển thị highlight menu đang được thực hiện trong schedule Liệu pháp (cùng màu với status LIệu pháp)</li>
                    <li>Có thể edit được schedule bằng cách bấm vào tên menu hoặc kéo và thả menu</li>
                    <li>Khi schedule được edit thì lưu lại nội dung được sửa vào DB</li>
                </ul>
            </td>
        </tr>
        <tr>
            <th>④</th>
            <td>Edit Hồ sơ</td>
            <td>Thao tác, thay đổi, cập nhật data</td>
            <td>
                <ul>
                    <li>Hiểu thị thông tin Hồ sơ đọc được từ ID Khách hàng trên form</li>
                    <li>Khi form được edit thì lưu lại nội dung được sửa vào DB</li>
                    <li>Nội dung Hồ sơ như sau</li>
                    <ul>
                        <li>氏名：テキスト</br>Họ tên: text</li>
                        <li>フリガナ：テキスト</br>Furigana: text</li>
                        <li>郵便番号：テキスト</br>Mã bưu điện: text</li>
                        <li>住所：テキスト</br>Địa chỉ: text</li>
                        <li>生年月日：日付</br>Ngày sinh: ngày tháng năm</li>
                        <li>電話番号：テキスト</br>Số điện thoại: text</li>
                        <li>メールアドレス：テキスト</br>Địa chỉ email: text</li>
                        <li>職業：単一選択</br>Nghề nghiệp: chọn trong list dưới đây</li>
                        <ol>
                            <li>会社員</br>Nhân viên văn phòng</li>
                            <li>学生</br>Học sinh/Sinh viên</li>
                            <ul>
                                <li>高</br>Cấp 3</li>
                                <li>大</br>Đại học</li>
                                <li>専</br>Trường nghề</li>
                            </ul>
                            <li>その他：テキスト</br>Khác: nhập text</li>
                        </ol>
                        <li>店を知ったきっかけ：単一選択</br>Cách biết tới tiệm: chọn trong list dưới đây</li>
                        <ol>
                            <li>紹介：テキスト（紹介者名）</br>Giới thiệu: text (tên người giới thiệu)</li>
                            <li>美容学生：テキスト（学校名）</br>Sinh viên trường thẩm mĩ: text (tên trường)</li>
                            <li>Google検索</br>Google search</li>
                            <li>ホットペッパー</br>(HotPepper)[https://www.hotpepper.jp/]</li>
                            <li>Instagram</li>
                            <li>minimo</li>
                            <li>その他SNS：テキスト</br>SNS khác: nhập text</li>
                            <li>ホームページ</br>Website của tiệm</li>
                            <li>チラシ</br>Tờ rơi</li>
                            <li>通りすがり</br>Đi qua</li>
                        </ol>
                        <li>サロン内での過ごし方：複数選択</br>Trải nghiệm trong salon</li>
                        <ol>
                            <li>なるべく会話は控えたい</br>Muốn tránh nói chuyện nhiều nhất có thể</li>
                            <li>スタッフとの会話を楽しみたい</br>Muốn nói chuyện cùng các staff</li>
                            <li>タブレット端末でデジタル雑誌を読みたい</br>Muốn đọc tạp chí trên tablet</li>
                            <li>ご自身のスマホを利用したい</br>Muốn sử dụng smartphone của bản thân</li>
                            <li>施術内容についての説明を聞きたい</br>Muốn nghe giải thích về nội dung liệu pháp</li>
                        </ol>
                        <li>シャンプーやヘッドスパでの力加減：単一選択</br>Mức độ dùng sức mong muốn khi gội, ấp: lựa chọn dưới đây</li>
                        <ol>
                            <li>強め</br>Mạnh</li>
                            <li>やや強め</br>Mạnh vừa phải</li>
                            <li>普通</br>Thường</li>
                            <li>やや弱め</br>Nhẹ vừa phải</li>
                            <li>弱め</br>Nhẹ</li>
                            <li>その都度確認してほしい</br>Muốn được xác nhận khi thực hiện</li>
                        </ol>
                        <li>今までの美容室で気になったこと：複数選択</br>Những điểm có từng thắc mắc ở thẩm mĩ viện trước đây: lựa chọn nhiều</li>
                        <ol>
                            <li>仕上がり</br>Hoàn thành</li>
                            <li>技術</br>Kĩ thuật</li>
                            <li>接客</br>Tiếp khách</li>
                            <li>施術時間</br>Thời gian liệu pháp</li>
                            <li>店内の清潔さ</br>Mức sạch sẽ trong tiệm</li>
                            <li>その他：テキスト</br>Khác: nhập text</li>
                        </ol>
                        <li>なりたいイメージ：複数選択</br>Mong muốn trở nên ra sao: chọn nhiều</li>
                        <ol>
                            <li>かわいい</br>Đáng yêu</li>
                            <li>ナチュラル</br>Tự nhiên</li>
                            <li>モテ、愛され</br>Được chú ý, yêu mến</li>
                            <li>かっこいい</br>Cool, ngầu</li>
                            <li>大人っぽく</br>Trưởng thành hơn</li>
                            <li>似合うようにしてほしい</br>Muốn (kiểu tóc) trông hợp với mình</li>
                        </ol>
                        <li>髪についての悩み：複数選択</br>Điểm lo lắng về mái tóc bản thân</li>
                        <ol>
                            <li>ダメージ</br>Hư tổn</li>
                            <li>カラーの色持ち</br>Lên màu</li>
                            <li>パーマの持ち</br>Giữ nếp uốn</li>
                            <li>クセや広がり</br>Gãy, chẻ</li>
                            <li>ボリュームが出にくい</br>Lượng tóc trông không đủ nhiều</li>
                            <li>ホームケアの仕方</br>Cách dưỡng tóc ở nhà</li>
                            <li>スタイリングの仕方</br>Các tạo kiểu</li>
                            <li>その他：テキスト</br>Khác: nhập text</li>
                        </ol>
                        <li>当日の仕上がりイメージ：テキスト</br>Mong muốn hoàn thành ra sao: nhập text</li>
                        <li>施術履歴：データベースから</br>Lịch sử các liệu pháp: lấy từ DB</li>
                        <li>過去半年以内に行った施術：複数選択</br>Các liệu pháp thực hiện trong nửa năm trở lại: chọn nhiều</li>
                        <ol>
                            <li>黒染め</br>Nhuộm đen</li>
                            <li>ブリーチ</br>Tẩy</li>
                            <li>縮毛矯正</br>Duỗi</li>
                            <li>デジタルパーマ</br>Uốn kĩ thuật số</li>
                            <li>ストレートパーマ</br>Uốn thẳng</li>
                        </ol>
                        <li>希望の仕上がり時間：単一選択</br>Mong muốn thời gian hoàn thành: chọn một</li>
                        <ol>
                            <li>急いでいる：時刻（希望終了時刻）</br>Gấp: giờ (giờ kết thúc)</li>
                            <li>急いでいないが希望がある：時刻（希望終了時刻）</br>Không vội nhưng có giới hạn giờ: giờ (giờ kết thúc)</li>
                            <li>特にない</br>Không vội</li>
                        </ol>
                        <li>施術メニュー以外に興味のあるメニュー：複数選択</br>Có quan tâm menu khác ngoài Liệu pháp đang dùng: chọn nhiều</li>
                        <ol>
                            <li>カット</br>Cắt</li>
                            <li>カラー</br>Nhuộm</li>
                            <li>インナーカラー</br>Nhuộm trong</br></li>
                            <li>パーマ</br>Uốn</li>
                            <li>デジタルパーマ</br>Uốn kĩ thuật số</li>
                            <li>縮毛矯正</br>Duỗi</br></li>
                            <li>トリートメント</br>Dưỡng</li>
                            <li>ヘッドスパ</br>Hấp</li>
                            <li>眉カット</br>Tỉa lông mày</li>
                            <li>その他：テキスト</br>Khác: nhập text</li>
                        </ol>
                        <li>おすすめ商品の紹介を希望するか：単一選択</br>Có muốn được giới thiệu thêm sản phẩm không</li>
                        <ol>
                            <li>はい</br>Có</li>
                            <li>いいえ</br>Không</li>
                        </ol>
                        <li>自宅でのヘアケアについて：単一選択</br>Chăm sóc tóc tại nhà: chọn một</li>
                        <ol>
                            <li>サロンで購入したもの</br>Bằng sản phẩm mua từ salon</li>
                            <li>市販のもの</br>Bằng sản phẩm mua ngoài</li>
                            <li>特にしていない</br>Không làm gì</li>
                        </ol>
                        <li>利用しているSNS：複数選択</br>Đang dùng SNS: chọn nhiều</li>
                        <ol>
                            <li>Instagram</li>
                            <li>Twitter</li>
                            <li>TikTok</li>
                            <li>LINE</li>
                            <li>Facebook</li>
                            <li>YouTube</li>
                            <li>Clubhouse</li>
                            <li>その他：テキスト</br>Khác: nhập text</li>
                        </ol>
                        <li>その他の要望：テキストエリア</br>Mong muốn khác: khung nhập text</li>
                        <li>管理用メモ：テキストエリア</br>Note quản lý: khung nhập text</li>
                    </ul>
                </ul>
            </td>
        </tr>
        <tr>
            <th>⑤</th>
            <td>Quay lại với màn khởi động</td>
            <td>Button</td>
            <td>
                <ul>
                    <li>Khi bấm vào thì thực hiện xử lý sau</li>
                    <ul>
                        <li>Quay trở lại màn hình khởi động (Home)</li>
                    </ul>
                </ul>
            </td>
        </tr>
    </tbody>
</table>
