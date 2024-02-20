<div class="hidden">

#kaoiri #ジャスティス

</div>

## ER Diagram

```mermaid
erDiagram

"Khách hàng" }o--o| "Hội viên": "Khách hàng }o--o| Hội viên"
"Khách hàng" ||--|| "Hồ sơ": "Khách hàng ||--|| Hồ sơ"
"Hội viên" ||--|| "Hồ sơ": "Hội viên ||--|| Hồ sơ"
"Khách hàng" ||--|| "Liệu pháp": "Khách hàng ||--|| Liệu pháp"
"Liệu pháp" ||--o{ "Thủ thuật": "Liệu pháp ||--o{ Thủ thuật"
"Thủ thuật" ||--|| "Menu": "Thủ thuật ||--|| Menu"
"Thủ thuật" ||--|{ "Phụ trách": "Thủ thuật ||--|{ Phụ trách"
"Phụ trách" ||--|| "Staff": "Phụ trách ||--|| Staff"
"Liệu pháp" ||--o{"Thời gian chờ Thủ thuật"

"Hội viên" {
    id string PK
    email string
    password_hashed string
    created_at timestamp
}

"Khách hàng" {
    id string PK
    member_id string FK
}

"Hồ sơ" {
    id string PK
    client_id string FK "ID Khách hàng"
    member_id string FK "ID Hội viên"
    name string "Họ tên"
    infomation any "Thông tin của Khách hàng Liệu pháp"
}

"Liệu pháp" {
    id string PK
    client_id string FK "ID Khách hàng"
    day_of_week string "Ngày trong tuần"
    weekday boolean "Phân biệt weekday hay weekend"
    recepted_at timestamp "Ngày giờ tiếp nhận"
    will_start_at timestamp "Ngày giờ dự kiến bắt đầu"
    started_at timestamp "Ngày giờ bắt đầu"
    finished_at timestamp "Ngày giờ kết thúc"
}

"Menu" {
    id integer PK
    name string "Tên menu"
    fee integer "Chi phí"
}

"Thủ thuật" {
    id string PK
    treatment_id string FK "ID Liệu pháp"
    menu_id string FK "ID Menu"
    order integer "Thứ tự"
    started_at timestamp "Ngày giờ bắt đầu thủ thuật"
    finished_at timestamp "Ngày giờ kết thúc thủ thuật"
}

"Staff" {
    id string PK
    pos_id integer "ID trên POS"
    name string "Họ tên"
}

"Phụ trách" {
    id string PK
    job_id string FK "ID Thủ thuật"
    staff_id string FK "Staff ID"
    started_at timestamp "Ngày giờ bắt đầu phụ trách"
    finished_at timestamp "Ngày giờ kết thúc phụ trách"
}

"Thời gian chờ Thủ thuật" {
    id string PK
    prev_menu_id string FK "ID menu trước"
    next_menu_id string FK "ID menu sau"
    started_at timestamp "Ngày giờ bắt đầu tính thời gian chờ"
    finished_at timestamp "Ngày giờ kết thúc thời gian chờ"
}
```

## Legend

|Kí hiệu|Ý nghĩa|
|:--:|:--|
|--\||one|
|--{|many|
|--\|\||one and only one|
|--o\||zero or one|
|--\|{|one or many|
|--o{|zero or many|
