# APIドキュメント

## エリアAPI

・API名
エリア作成/更新

・概要  
このAPIは、ターゲットエリア、不可侵領域（FA）、何か意味を持つ場所（SA）を含むエリア情報を新規作成または更新するために使用されます。

・エンドポイント  
`POST /api/v1/area`

・リクエスト  
ヘッダー:

```http
Accept: application/json, text/plain, */*
Authorization: Bearer <token>
Content-Type: application/json
```

リクエストボディ:

```json
{
  "app_id": 0,
  "area_id": 0,
  "area_name": "string",
  "areas": {
    "special_areas": [],
    "forbidden_areas": [],
    "target_areas": []
  }
}
```

| フィールド名               | データ型      | 必須 | 説明                             |
|----------------------|-----------|----|--------------------------------|
| `app_id`             | `integer` | 必須 | 操作対象のアプリケーションを特定するためのID        |
| `area_id`            | `integer` | 任意 | 特定のエリア（area）のID（エリアを更新する場合に使用） |
| `area_name`          | `string`  | 必須 | エリア名                           |
| `areas`              | `object`  | 必須 | 関連するエリアタイプのグループ                |
| ├─ `special_areas`   | `array`   | 任意 | 何か意味を持つ場所（SA）のリスト              |
| ├─ `forbidden_areas` | `array`   | 任意 | 不可侵領域（FA）のリスト                  |
| └─ `target_areas`    | `array`   | 任意 | ターゲットエリアのリスト                   |

・レスポンス

```json
{
  "id": 1990,
  "app_id": 100,
  "area_name": "area_name",
  "fba_count": 1,
  "spa_count": 1,
  "wall_count": null,
  "area_type": 1
}
```

・サンプル  
リクエスト:

```bash
curl --location '{domain}/api/v1/area' \
--header 'Authorization: Bearer <token>' \
--header 'Accept: application/json' \
--header 'Content-Type: application/json' \
--data '{
  "app_id": "100",
  "area_name": "Area name 1",
  "areas": {
    "target_areas": [
      {
        "points": [50, 53, 50, 685, 1875, 685, 1875, 53],
        "konvaId": "d35a069c-ccf9-4cf7-851d-2890e4d3e37e"
      }
    ],
    "special_areas": [
      {
        "points": [254, 316, 254, 524, 1744, 524, 1744, 316],
        "konvaId": "f493e056-67b3-494e-bff8-d954577df25a"
      }
    ],
    "forbidden_areas": [
      {
        "points": [183, 121, 183, 267, 1754, 267, 1754, 121],
        "konvaId": "3a08bcad-fdcf-43a6-98ab-8ab0afa80128"
      }
    ]
  },
  "area_id": "1990"
}'

```

レスポンス:

```json
{
  "id": 1990,
  "app_id": 100,
  "area_name": "Area name 1",
  "fba_count": 1,
  "spa_count": 1,
  "wall_count": null,
  "area_type": 1
}
```

## グリッドAPI

・API名
グリッド作成/更新

・概要
このAPIは、グリッド情報（グリッド名、画像サイズ、座標リストを含む）を新規作成または更新するために使用されます。

・エンドポイント
`POST /api/v1/grid`

・リクエスト

```http
Accept: application/json
Authorization: Bearer <token>
Content-Type: application/json
{
  "app_id": "100",
  "grid_name": "Grid test",
  "grid_data": [
    ["(0,0)", 77.12, 73.22, 80],
    ["(1,0)", 157.12, 73.22, 80]
  ],
  "grid_id": "1000",
  "img_width": 1928,
  "img_height": 735
}
```

| フィールド名     | データ型    | 必須 | 説明               |
|------------|---------|----|------------------|
| app_id     | string  | 必須 | アプリケーションのID      |
| grid_name  | string  | 必須 | グリッド名            |
| grid_data  | array   | 必須 | 座標およびグリッドデータのリスト |
| grid_id    | string  | 任意 | グリッドID（更新時に使用）   |
| img_width  | integer | 必須 | 画像の幅             |
| img_height | integer | 必須 | 画像の高さ            |

・レスポンス

```
{
  "id": 1000,
  "app_id": 100,
  "grid_name": "Grid test",
  "grid_size": 80,
  "origin_x": 77.12,
  "origin_y": 73.22,
  "img_width": 1928,
  "img_height": 735
}
```

・サンプル

```bash
curl --location '{domain}/api/v1/grid' \
--header 'Authorization: Bearer <token>' \
--header 'Content-Type: application/json' \
--data '{
  "app_id": "100",
  "grid_name": "Grid test",
  "grid_data": [
    ["(0,0)", 77.12, 73.22, 80],
    ["(1,0)", 157.12, 73.22, 80]
  ],
  "grid_id": "1000",
  "img_width": 1928,
  "img_height": 735
}'
```

## ウォールAPI

・API名
ウォール（Wall）エリア新規作成

・概要
このAPIは、アプリケーション内のウォール（Wall）エリアの情報を作成または更新することを可能にします。座標情報や識別情報（konvaId）を含みます。

・エンドポイント

`POST /api/v1/wall`

・リクエスト  
ヘッダー:

```http
Accept: application/json
Authorization: Bearer <token>
Content-Type: application/json
{
    "app_id": "100",
    "area_name": "Wall",
    "areas": {
        "walls": [
            {
                "points": [
                    605,
                    346,
                    935,
                    341
                ],
                "konvaId": "791c106f-a6b3-413e-aedb-0bc5c3ec4d4c"
            }
        ]
    },
    "area_id": "2000"
}
```

| フィールド名               | データ型         | 必須 | 説明                          |
|----------------------|--------------|----|-----------------------------|
| app_id               | int / string | 必須 | アプリケーションのID                 |
| area_id              | int / string | 任意 | エリアID（ウォールを含むエリアを更新する場合に使用） |
| area_name            | string       | 必須 | エリア名                        |
| areas.walls[].points | array[int]   | 必須 | 座標リスト（x, y）                 |

・サンプル

```bash
curl "http://127.0.0.1:8001/api/v1/wall" \
  -H "Accept: application/json" \
  -H "Authorization: Bearer <token>" \
  -H "Content-Type: application/json" \
  --data '{"app_id":"100","area_name":"Wall","areas":{"walls":[{"points":[605,346,935,341],"konvaId":"791c106f-a6b3-413e-aedb-0bc5c3ec4d4c"}]},"area_id":"2000"}'
```

## ルートデータAPI

・API名
ルート計算用データ新規作成

・概要
このAPIは、エリア情報、グリッド情報、ウォール情報、およびアルゴリズム設定を送信することで、システムがルート計算用データを生成できるようにします。

・エンドポイント

`POST /api/v1/data`

・リクエスト
ヘッダー:

```http
Accept: application/json
Authorization: Bearer <token>
Content-Type: application/json
```

リクエストボディ:

```json
{
  "applicationClusterId": 100,
  "areaId": 1989,
  "gridId": 1000,
  "wallId": 1999,
  "routeDateFrom": "2025-09-16 00:00",
  "routeDateTo": "2025-10-21 00:00",
  "algorithmId": 2,
  "title": "Route 1",
  "memo": "",
  "isBookmark": false
}
```

| フィールド名                 | データ型             | 必須 | 説明              |
|------------------------|------------------|----|-----------------|
| `applicationClusterId` | `integer`        | 必須 | アプリケーションクラスターID |
| `areaId`               | `integer`        | 必須 | エリアID           |
| `gridId`               | `integer`        | 必須 | グリッド（Grid）のID   |
| `wallId`               | `integer`        | 必須 | ウォール（Wall）のID   |
| `routeDateFrom`        | `string(datetime)` | 必須 | ルート計算開始日時       |
| `routeDateTo`          | `string(datetime)` | 必須 | ルート計算終了日時       |
| `algorithmId`          | `integer`        | 必須 | 使用するアルゴリズムのID   |
| `title`                | `string`         | 必須 | データ／ルートのタイトル    |
| `memo`                 | `string`         | 任意 | メモ              |
| `isBookmark`           | `boolean`        | 任意 | ブックマーク          |

・サンプル

```bash
curl "{domain}/api/v1/data" \
  -H "Accept: application/json" \
  -H "Authorization: Bearer <token>" \
  -H "Content-Type: application/json" \
  --data '{
    "applicationClusterId": 100,
    "areaId": 1989,
    "gridId": 1000,
    "wallId": 1999,
    "routeDateFrom": "2025-09-16 00:00",
    "routeDateTo": "2025-10-21 00:00",
    "algorithmId": 2,
    "title": "Route 1",
    "memo": "",
    "isBookmark": false
  }'
```

レスポンス：
`{"message": "Route data endpoint is under construction."}`

# ルートデータ再作成API

## エンドポイント

`POST /api/v1/data/rebuild`

### リクエスト

### ヘッダー

```http
Accept: application/json
Authorization: Bearer <token>
Content-Type: application/json
```

### リクエストボディー

```json
{
  "route_data_id": 78
}
```

| フィールド名          | データ型      | 必須 | 説明              |
|-----------------|-----------|----|-----------------|
| `route_data_id` | `integer` | 必須 | 再作成するルートデータID |

### レスポンス

```json
{
  "message": "Route data rebuild started.",
  "route_data_id": 78,
  "task_id": "3b896cc4-6d91-4f2b-8c07-0f9d2f6f23a1"
}
```

# リアルタイム経路データ取得API

## エンドポイント

`POST /api/v1/data/realtime_route_data`

### リクエスト

### ヘッダー

```http
Accept: application/json
Authorization: Bearer <token>
Content-Type: application/json
```

### リクエストボディー

```json
{
  "start_date": "2026-02-02 13:26:26",
  "end_date": "2026-02-02 13:31:26",
  "route_data_id": 78,
  "device_ids": "35f4294a-5663-4707-87e7-7ca743c6a8fc",
  "wall_consideration": false
}
```

| フィールド名               | データ型      | 必須 | 説明                    |
|----------------------|-----------|----|-----------------------|
| `start_date`         | `string`  | 必須 | 開始時間                  |
| `end_date`           | `string`  | 必須 | 終了時間                  |
| `route_data_id`      | `integer` | 任意 | ルートデータID              |
| `device_ids`         | `string`  | 任意 | デバイスID一覧（カンマ区切り）      |
| `wall_consideration` | `boolean` | 任意 | ルート計算時にウォールを考慮するかどうか |

### レスポンス

```json
[
  {
    "deviceId": "35f4294a-5663-4707-87e7-7ca743c6a8fc",
    "data": [
      {
        "detectedAt": "2026-02-02T13:26:26",
        "position": "(1,32)",
        "x": 1310,
        "y": 520,
        "hokan": false
      }
    ]
  }
]
```

データが存在しない場合:

```json
{
  "message": "No data found for the given parameters."
}
```

# クラスター単位で position log を取得するAPI

## エンドポイント

`GET /api/v1/data/position_logs`

### リクエスト

### ヘッダー

```http
Accept: application/json
```

クエリパラメータ

```http
cluster_id=6ec48ca4-90d5-4609-a9c7-a4aa28b9c80a&start_date=2026-02-02+00:00:00&end_date=2026-02-02+23:59:59
```

| フィールド名       | データ型     | 必須 | 説明     |
|--------------|----------|----|--------|
| `cluster_id` | `string` | 必須 | クラスターID |
| `start_date` | `string` | 必須 | 開始時間   |
| `end_date`   | `string` | 必須 | 終了時間   |

### レスポンス

```json
{
  "data": [
    {
      "cluster_id": "6ec48ca4-90d5-4609-a9c7-a4aa28b9c80a",
      "device_id": "6f92ab3b-2eec-43d4-865a-e9570e94e50c",
      "nearest": "bb2a9ca7-e3b3-4503-8fe7-c36d24c22732",
      "x": 1310.0000000000002,
      "y": 520,
      "h": 120,
      "r": 0,
      "detected": "2025-10-15T18:25:38Z"
    }
  ],
  "meta": {
    "total": 382100
  }
}
```

# ヒートマップデータ取得API

## エンドポイント

`POST /api/v1/data/heatmap_data`

### リクエスト

### ヘッダー

```http
Accept: application/json
Authorization: Bearer <token>
Content-Type: application/json
```

### リクエストボディー

```json
{
  "start_time": "2026-01-29 00:00",
  "end_time": "2026-01-29 23:59",
  "heatmap": 2,
  "route_data_id": 78,
  "min_dwell_seconds": 60,
  "max_dwell_seconds": 3600,
  "device_ids": "35f4294a-5663-4707-87e7-7ca743c6a8fc"
}
```

| フィールド名              | データ型      | 必須 | 説明                      |
|---------------------|-----------|----|-------------------------|
| `start_time`        | `string`  | 必須 | 開始時間（YYYY-MM-DD HH:MM）  |
| `end_time`          | `string`  | 必須 | 終了時間（YYYY-MM-DD HH:MM）  |
| `heatmap`           | `integer` | 必須 | ヒートマップ種別（1：デバイス、2：滞在時間） |
| `route_data_id`     | `integer` | 必須 | ルートデータID                |
| `min_dwell_seconds` | `integer` | 任意 | 最小滞在時間（秒）              |
| `max_dwell_seconds` | `integer` | 任意 | 最大滞在時間（秒）              |
| `device_ids`        | `string`  | 任意 | デバイスID一覧（カンマ区切り）        |

### レスポンス

```json
{
  "data": [
    {
      "position": "(1,32)",
      "duration": 0
    }
  ],
  "device_dwell_seconds_chart": {
    "0ed83280-aaeb-4833-a826-a47b18670ac0": 0,
    "184e2c95-c448-48a0-9cab-be3d583a0b31": 0.06666666666666667
  },
  "summary": {
    "device_counts": 12,
    "overall_avg_speed": 105.63,
    "avg_dwell_time": 0.38,
    "total_dwell_time": 3,
    "avg_dwell_time_per_section": 0.25,
    "min_speed": 12,
    "max_speed": 414
  }
}
```

データが存在しない場合:

```json
{
  "status": "no data"
}
```

# ポジションログチャート取得API

## エンドポイント

`POST /api/v1/data/position_log_chart`

### リクエスト

### ヘッダー

```http
Accept: application/json
Authorization: Bearer <token>
Content-Type: application/json
```

### リクエストボディー

```json
{
  "target_date": "2026-02-02 13:15:52",
  "route_data_id": 78,
  "device_ids": "1c930de2-342b-41e0-8497-ac5af8a60acb"
}
```

| フィールド名          | データ型      | 必須 | 説明                        |
|-----------------|-----------|----|---------------------------|
| `target_date`   | `string`  | 必須 | 対象日時（YYYY-MM-DD HH:MM:SS） |
| `route_data_id` | `integer` | 必須 | ルートデータID                  |
| `device_ids`    | `string`  | 任意 | デバイスID一覧（カンマ区切り）          |

### レスポンス

```json
[
  {
    "date": "02-01",
    "data": [
      {
        "time": 13,
        "value": 0
      }
    ]
  },
  {
    "date": "02-02",
    "data": [
      {
        "time": 23,
        "value": 0
      }
    ]
  },
  {
    "date": "02-03",
    "data": [
      {
        "time": 0,
        "value": 0
      }
    ]
  }
]
```

# AIサイトへのデータ送信API

## エンドポイント

`GET /api/v1/data/AI_site`

### リクエスト

### ヘッダー

```http
Accept: application/json
Authorization: Bearer <token>
```

クエリパラメータ

```http
route_data_id=78&start_time=2026-02-02+00:00:00&end_time=2026-02-02+23:59:59
```

| フィールド名          | データ型      | 必須 | 説明                 |
|-----------------|-----------|----|--------------------|
| `route_data_id` | `integer` | 必須 | ルートデータID           |
| `start_time`    | `string`  | 任意 | データを絞り込む開始時間      |
| `end_time`      | `string`  | 任意 | データを絞り込む終了時間      |

### レスポンス

```json
{
  "message": "ok"
}
```

エラーの場合:

```json
{
  "error": "Setting BLE Analytics API failed"
}
```

# AIサイト用CSVエクスポートAPI

## エンドポイント

`GET /api/v1/data/AI_site/{data_id}/csv`

### リクエスト

### ヘッダー

```http
Accept: application/zip
Authorization: Bearer <token>
```

パスパラメータ

| フィールド名    | データ型      | 必須 | 説明        |
|-----------|-----------|----|-----------|
| `data_id` | `integer` | 必須 | ルートデータID  |

クエリパラメータ

```http
start_time=2026-02-02+00:00:00&end_time=2026-02-02+23:59:59
```

| フィールド名       | データ型     | 必須 | 説明            |
|--------------|----------|----|---------------|
| `start_time` | `string` | 任意 | データを絞り込む開始時間 |
| `end_time`   | `string` | 任意 | データを絞り込む終了時間 |

### レスポンス

`Content-Type: application/zip` で `ai_site_{data_id}_csv.zip` ファイルを返します。

ZIP内のCSVファイル:

| ファイル                         | 主な内容              |
|------------------------------|-------------------|
| `grid_path.csv`               | グリッド別の経路データ      |
| `obj_area.csv`                | セクション、属性、エリア種別データ |
| `refine_grid.csv`             | 精製済みグリッドデータ       |
| `map.csv`                     | ルートデータ別のマップURL    |
| `corrected_location_data.csv` | 補正済み位置データ         |

# ポジションログに基づくデバイス一覧取得API

## エンドポイント

`GET /api/v1/device`

### リクエスト

### ヘッダー

```http
Accept: application/json
Authorization: Bearer <token>
```

クエリパラメータ

```http
start_time=2026-02-02+13:26:26&end_time=2026-02-02+13:31:26&route_data_id=78
```

| フィールド名          | データ型      | 説明                     |
|-----------------|-----------|------------------------|
| `start_time`    | `string`  | 開始時間（YYYY-MM-DD HH:MM） |
| `end_time`      | `string`  | 終了時間（YYYY-MM-DD HH:MM） |
| `route_data_id` | `integer` | ルートデータID               |

### レスポンス

```json
{
  "total_devices": 1,
  "data": [
    {
      "device_id": "35f4294a-5663-4707-87e7-7ca743c6a8fc",
      "device_name": null,
      "count": 4
    }
  ]
}
```

# セクション単位のデバイス一覧API

## エンドポイント

`GET /api/v1/device/grid_path`

### リクエスト

### ヘッダー

```http
Accept: application/json
Authorization: Bearer <token>
```

クエリパラメータ

```http
route_data_id=78&section=(1,32)
```

| フィールド名          | データ型      | 必須 | 説明                 |
|-----------------|-----------|----|--------------------|
| `route_data_id` | `integer` | 任意 | ルートデータID          |
| `section`       | `string`  | 任意 | デバイス一覧を取得するセクション |

### レスポンス

```json
[
  {
    "device_id": "35f4294a-5663-4707-87e7-7ca743c6a8fc",
    "device_name": "Device 001"
  }
]
```

# GNN予測API

## エンドポイント

`POST /api/v1/gnn/predict`

### リクエスト

### ヘッダー

```http
Accept: application/json
Authorization: Bearer <token>
Content-Type: application/json
```

### リクエストボディー

```json
{
  "route_data_id": 78,
  "routeDateFrom": "2026-02-02 00:00:00",
  "routeDateTo": "2026-02-02 23:59:59",
  "device_ids": [
    "35f4294a-5663-4707-87e7-7ca743c6a8fc"
  ],
  "device_attribute": "staff",
  "inflow_scale": 1.0,
  "speed_unit": 1,
  "start_speed": 0,
  "end_speed": 20
}
```

| フィールド名              | データ型           | 必須 | 説明                   |
|---------------------|----------------|----|----------------------|
| `route_data_id`     | `integer`      | 必須 | ルートデータID             |
| `routeDateFrom`     | `string(datetime)` | 任意 | データを絞り込む開始時間        |
| `routeDateTo`       | `string(datetime)` | 任意 | データを絞り込む終了時間        |
| `device_ids`        | `array<string>` | 任意 | デバイスUUID一覧           |
| `device_attribute`  | `string`       | 任意 | 絞り込み対象のデバイス属性       |
| `inflow_scale`      | `number`       | 任意 | inflow係数             |
| `speed_unit`        | `integer`      | 任意 | backend enumに基づく速度単位 |
| `start_speed`       | `number`       | 任意 | edgeを絞り込む最小速度       |
| `end_speed`         | `number`       | 任意 | edgeを絞り込む最大速度       |

### レスポンス

```json
{
  "nodes": [
    {
      "id": "(1,32)",
      "label": "(1,32)"
    }
  ],
  "edges": [
    {
      "from": "(1,32)",
      "to": "(1,33)",
      "value": 12.5
    }
  ],
  "device_count": 10,
  "speed_unit": "km/h",
  "speed_unit_flag": 1,
  "average_speed": 4.52,
  "charts": []
}
```

# テナント作成API

## エンドポイント

`POST /create_tenant`

### リクエスト

### ヘッダー

```http
Accept: application/json
```

クエリパラメータ

```http
sub_domain=tenant_demo
```

| フィールド名       | データ型     | 必須 | 説明              |
|--------------|----------|----|-----------------|
| `sub_domain` | `string` | 必須 | 作成するschema/tenant名 |

### レスポンス

```json
{
  "message": "Tenant 'tenant_demo' created and migrated successfully."
}
```

# ログインAPI

## エンドポイント

`POST /login`

### リクエスト

### ヘッダー

```
Accept: application/json, text/plain, */*
Content-Type: application/json
```

### リクエストボディー

```json
{
  "email": "user@rooking.co.jp",
  "password": "password123@"
}
```

| フィールド名     | データ型     | 必須  | 説明      |
|------------|----------|-----|---------|
| `email`    | `string` | 必須　 | メールアドレス |
| `password` | `string` | 必須　 | パスワード   |

### レスポンス

```json
{
  "two_factor": false
}
```

| フィールド名       | データ型      | 説明                                        |
|--------------|-----------|-------------------------------------------|
| `two_factor` | `boolean` | 二要素認証の状態<br/>**false**：無効<br/>**true**：有効 |

# 新規JWT発行API

## エンドポイント

`POST /api/refresh-jwt`

### リクエスト

### ヘッダー

```http
Accept: application/json, text/plain, */*
Authorization: Bearer <token>
```

### レスポンス

```json
{
  "message": "Token has expired"
}
```

| フィールド名    | データ型     | 説明        |
|-----------|----------|-----------|
| `message` | `string` | メッセージ（英語） |

# パスワード再設定要求API

メール経由でパスワード再設定のリクエストを送信します。

## エンドポイント

`POST /forgot-password`

### リクエスト

### ヘッダー

```
Accept: application/json, text/plain, */*
Content-Type: application/json
```

### リクエストボディー

```json
{
  "email": "user@rooking.co.jp"
}
```

| フィールド名  | データ型     | 必須  | 説明      |
|---------|----------|-----|---------|
| `email` | `string` | 必須　 | メールアドレス |

### レスポンス

```json
{
  "message": "パスワードリセットのリンクをメールで送信しました。"
}
```

| フィールド名    | データ型     | 説明         |
|-----------|----------|------------|
| `message` | `string` | メッセージ（日本語） |

# パスワード再設定API

## エンドポイント

`POST /reset-password`

### リクエスト

### ヘッダー

```
Accept: application/json, text/plain, */*
Content-Type: application/json
```

### リクエストボディー

```json
{
  "email": "user@rooking.co.jp",
  "password": "password123@",
  "token": "eeb656408c657baff50ce427cdf9c90072141dde7a560082fd189600cd11d521"
}
```

| フィールド名     | データ型     | 必須  | 説明            |
|------------|----------|-----|---------------|
| `email`    | `string` | 必須　 | メールアドレス       |
| `password` | `string` | 必須　 | パスワード         |
| `token`    | `string` | 必須　 | パスワード再設定用トークン |

### レスポンス

```json
{
  "message": "パスワードがリセットされました。"
}
```

| フィールド名    | データ型     | 説明         |
|-----------|----------|------------|
| `message` | `string` | メッセージ（日本語） |

# 初回パスワード設定API

## エンドポイント

`POST /api/set-password`

### リクエスト

### ヘッダー

```
Accept: application/json, text/plain, */*
Content-Type: application/json
```

### リクエストボディー

```json
{
  "email": "user@rooking.co.jp",
  "password": "password123@",
  "token": "eeb656408c657baff50ce427cdf9c90072141dde7a560082fd189600cd11d521"
}
```

| フィールド名     | 型        | 必須 | 説明             |
|------------|----------|----|----------------|
| `email`    | `string` | 必須 | メールアドレス        |
| `password` | `string` | 必須 | パスワード          |
| `token`    | `string` | 必須 | 初回パスワード設定用トークン |

### レスポンス

Status: `204 No Content`

レスポンスボディは空です。

# アカウント情報API

## エンドポイント

`GET /api/user`

### リクエスト

### ヘッダー

```
Accept: application/json, text/plain, */*
Authorization: Bearer <token>
```

### レスポンス

```json
{
  "id": 2,
  "is_active": true,
  "email": "user@rooking.co.jp",
  "created_at": "2026-01-09 13:50:34",
  "updated_at": "2026-01-12 18:54:57",
  "tenant_id": 1,
  "user_type": 3,
  "last_name": "林",
  "first_name": "彩花",
  "last_name_kana": "はやし",
  "first_name_kana": "あやか",
  "company_name": "ROOKING, Inc.",
  "memo": null,
  "user_created": 1,
  "user_updated": null,
  "has_update_application": false,
  "has_update_app_cluster": false
}
```

| フィールド名                   | データ型      | 説明                                                                        |
|--------------------------|-----------|---------------------------------------------------------------------------|
| `id`                     | `integer` | アカウントID                                                                   |
| `is_active`              | `boolean` | アカウントの状態<br/>**false**：利用不可<br/>**true**：利用可能                             |
| `email`                  | `string`  | メールアドレス                                                                   |
| `created_at`             | `string`  | アカウント作成日時                                                                 |
| `updated_at`             | `string`  | アカウント更新日時                                                                 |
| `tenant_id`              | `integer` | テナントID                                                                    |
| `user_type`              | `integer` | アカウント種別<br/>**1**：Beacrewアカウント<br/>**2**：テナント管理者アカウント<br/>**3**：ユーザーアカウント |
| `last_name`              | `string`  | 姓（漢字）                                                                     |
| `first_name`             | `string`  | 名（漢字）                                                                     |
| `last_name_kana`         | `string`  | 姓（カナ）                                                                     |
| `first_name_kana`        | `string`  | 名（カナ）                                                                     |
| `company_name`           | `string`  | 会社名                                                                       |
| `memo`                   | `string`  | メモ                                                                        |
| `user_created`           | `integer` | 当該アカウントを作成したテナント管理者のID（一般ユーザーのみ）                                          |
| `user_updated`           | `integer` | 当該アカウントを更新したテナント管理者のID（一般ユーザーのみ）                                          |
| `has_update_application` | `boolean` | テナント管理者向けのアプリケーション作成／更新権限（Beacrewアカウントのみ）                                 |
| `has_update_app_cluster` | `boolean` | 一般ユーザー向けのアプリケーションクラスター作成／更新権限（テナント管理者アカウントのみ）                             |

# アプリケーションクラスター一覧API

## エンドポイント

`GET /api/application-clusters`

### リクエスト

### ヘッダー

```
Accept: application/json, text/plain, */*
Authorization: Bearer <token>
```

### クエリ:

```http request
page=1&app_name=駅すぱあと本番用&cluster_name=大阪駅1F&attribute=トイレ
```

| フィールド名         | データ型      | 説明             |
|----------------|-----------|----------------|
| `page`         | `integer` | 現在のページ         |
| `app_name`     | `string`  | アプリケーション名で絞り込み |
| `cluster_name` | `string`  | クラスター名で絞り込み    |
| `attribute`    | `string`  | 属性名で絞り込み       |

### レスポンス

```json
{
  "total": 1,
  "last_page": 1,
  "data": [
    {
      "id": 63,
      "app_id": 83,
      "cluster_id": "6ec48ca4-90d5-4609-a9c7-a4aa28b9c80a",
      "created_at": "2025-10-15 18:29:04",
      "updated_at": "2026-01-12 19:27:01",
      "cluster": {
        "cluster_id": "6ec48ca4-90d5-4609-a9c7-a4aa28b9c80a",
        "cluster_name": "大阪駅1F"
      },
      "application": {
        "id": 83,
        "app_name": "駅すぱあと本番用"
      },
      "routes": [
        {
          "id": 1,
          "app_cluster_id": 63
        }
      ]
    }
  ]
}
```

| フィールド名                                     | データ型      | 説明              |
|--------------------------------------------|-----------|-----------------|
| `total`                                    | `integer` | アプリケーション総件数     |
| `last_page`                                | `integer` | 総ページ数           |
| `data`                                     | `array`   | アプリケーション一覧      |
| ├─`id`                                     | `integer` | アプリケーションクラスターID |
| ├─`app_id`                                 | `integer` | アプリケーションID      |
| ├─`cluster_id`                             | `string`  | クラスターID         |
| ├─`created_at`                             | `string`  | クラスター同期日時       |
| ├─`updated_at`                             | `string`  | クラスター更新日時       |
| ├─`cluster`                                | `object`  | クラスター詳細         |
| &nbsp;&nbsp;&nbsp;&nbsp;├─`cluster_id`     | `string`  | クラスターID         |
| &nbsp;&nbsp;&nbsp;&nbsp;└─`cluster_name`   | `string`  | クラスター名          |
| ├─`application`                            | `object`  | アプリケーション詳細      |
| &nbsp;&nbsp;&nbsp;&nbsp;├─`id`             | `integer` | アプリケーションID      |
| &nbsp;&nbsp;&nbsp;&nbsp;└─`app_name`       | `string`  | アプリケーション名       |
| └─`routes`                                 | `array`   | 経路データ一覧         |
| &nbsp;&nbsp;&nbsp;&nbsp;├─`id`             | `integer` | 経路データID         |
| &nbsp;&nbsp;&nbsp;&nbsp;└─`app_cluster_id` | `integer` | アプリクラスターID      |

# ポジションログ一覧API

## エンドポイント

`GET /api/position-logs`

### リクエスト

### ヘッダー

```http
Accept: application/json, text/plain, */*
Authorization: Bearer <token>
```

### クエリ:

```http request
page=1&start_time=2026-02-02+00:00:00&end_time=2026-02-02+23:59:59&beacons[]=bb2a9ca7-e3b3-4503-8fe7-c36d24c22732&device_ids[]=6f92ab3b-2eec-43d4-865a-e9570e94e50c
```

| フィールド名       | データ型           | 必須 | 説明           |
|--------------|----------------|----|--------------|
| `page`       | `integer`      | 任意 | 現在のページ       |
| `start_time` | `string`       | 任意 | 開始時間         |
| `end_time`   | `string`       | 任意 | 終了時間         |
| `beacons`    | `array<string>` | 任意 | 絞り込み対象のビーコン一覧 |
| `device_ids` | `array<string>` | 任意 | 絞り込み対象のデバイス一覧 |

### レスポンス

```json
{
  "total": 1,
  "last_page": 1,
  "data": [
    {
      "cluster_id": "6ec48ca4-90d5-4609-a9c7-a4aa28b9c80a",
      "device_id": "6f92ab3b-2eec-43d4-865a-e9570e94e50c",
      "detected": "2026-02-02 13:15:52",
      "coordinate_preview": "(1310, 520)",
      "cluster": {
        "cluster_id": "6ec48ca4-90d5-4609-a9c7-a4aa28b9c80a",
        "cluster_name": "大阪駅1F"
      },
      "device": {
        "device_id": "6f92ab3b-2eec-43d4-865a-e9570e94e50c",
        "device_name": "Device 001"
      }
    }
  ]
}
```

# position logs のビーコン一覧API

## エンドポイント

`GET /api/position-logs/beacons`

### リクエスト

### ヘッダー

```http
Accept: application/json, text/plain, */*
Authorization: Bearer <token>
```

### レスポンス

```json
[
  {
    "label": "bb2a9ca7-e3b3-4503-8fe7-c36d24c22732",
    "value": "bb2a9ca7-e3b3-4503-8fe7-c36d24c22732"
  }
]
```

# position logs のデバイス一覧API

## エンドポイント

`GET /api/position-logs/devices`

### リクエスト

### ヘッダー

```http
Accept: application/json, text/plain, */*
Authorization: Bearer <token>
```

### レスポンス

```json
[
  {
    "label": "Device 001",
    "value": "6f92ab3b-2eec-43d4-865a-e9570e94e50c"
  }
]
```

# エリア一覧API

アプリケーションクラスタに紐づくエリア一覧を取得します。

## エンドポイント

`GET /api/applications/{application_cluster}/areas`

### リクエスト

### ヘッダー

```
Accept: application/json, text/plain, */*
Authorization: Bearer <token>
```

### クエリ

```http request
page=1&area_name=対象エリア&attribute=トイレ
```

| フィールド名      | データ型      | 説明        |
|-------------|-----------|-----------|
| `page`      | `integer` | 現在のページ    |
| `area_name` | `string`  | エリア名で絞り込み |
| `attribute` | `string`  | 属性名で絞り込み  |

### レスポンス

```json
{
  "total": 1,
  "last_page": 1,
  "data": [
    {
      "id": 1,
      "area_name": "対象エリア",
      "fba_count": 1,
      "spa_count": 1,
      "created_at": "2026-01-05 13:03:07",
      "updated_at": "2026-01-05 14:00:21",
      "forbidden_areas": [
        {
          "area_type": "special",
          "points": [
            105,
            842,
            105,
            1213,
            936,
            1213,
            936,
            842
          ],
          "property": null
        }
      ]
    }
  ]
}
```

| フィールド名                                | データ型             | 説明                                                                           |
|---------------------------------------|------------------|------------------------------------------------------------------------------|
| `total`                               | `integer`        | エリア総件数                                                                       |
| `last_page`                           | `integer`        | 総ページ数                                                                        |
| `data`                                | `array`          | エリア一覧                                                                        |
| ├─`id`                                | `integer`        | エリアID                                                                        |
| ├─`area_name`                         | `string`         | エリア名                                                                         |
| ├─`fba_count`                         | `integer`        | 不可侵領域（FA）の数                                                                  |
| ├─`spa_count`                         | `integer`        | 何か意味を持つ場所（SA）の数                                                              |
| ├─`created_at`                        | `string`         | エリア作成日時                                                                      |
| ├─`updated_at`                        | `string`         | エリア更新日時                                                                      |
| └─`forbidden_areas`                   | `array`          | エリア一覧                                                                        |
| &nbsp;&nbsp;&nbsp;&nbsp;├─`area_type` | `string`         | エリア種別<br/>**special**：何か意味を持つ場所<br/>**forbidden**：不可侵領域<br/>**target**：対象エリア |
| &nbsp;&nbsp;&nbsp;&nbsp;├─`points`    | `array<integer>` | 座標リスト（x1, y1, x2, y2, …, xn, yn）                                             |
| &nbsp;&nbsp;&nbsp;&nbsp;└─`property`  | `string`         | 属性（何か意味を持つ場所のみ適用）                                                            |

# エリア／ウォールデータ削除API

## エンドポイント

`DELETE /api/areas/{area}`

### リクエスト

### ヘッダー

```http
Accept: application/json, text/plain, */*
Authorization: Bearer <token>
```

### レスポンス

Status: `204 No Content`

レスポンスボディは空です。

# エリア詳細API

## エンドポイント

`GET /api/areas/{area}`

### リクエスト

### ヘッダー

```http
Accept: application/json, text/plain, */*
Authorization: Bearer <token>
```

### レスポンス

```json
{
  "area_name": "対象エリア",
  "forbidden_areas": [
    {
      "area_type": "special",
      "points": [
        105,
        842,
        105,
        1213,
        936,
        1213,
        936,
        842
      ],
      "property": null
    }
  ]
}
```

| フィールド名            | データ型             | 説明                                                                           |
|-------------------|------------------|------------------------------------------------------------------------------|
| `area_name`       | `string`         | エリア名                                                                         |
| `forbidden_areas` | `array`          | エリア一覧                                                                        |
| ├─`area_type`     | `string`         | エリア種別<br/>**special**：何か意味を持つ場所<br/>**forbidden**：不可侵領域<br/>**target**：対象エリア |
| ├─`points`        | `array<integer>` | 座標リスト（x1, y1, x2, y2, …, xn, yn）                                             |
| └─`property`      | `string`         | 属性（何か意味を持つ場所のみ適用）                                                            |

# グリッド一覧API

アプリケーションクラスターに紐づくグリッド一覧を取得します。

## エンドポイント

`GET /api/applications/{application_cluster}/grids`

### リクエスト

### ヘッダー

```http
Accept: application/json, text/plain, */*
Authorization: Bearer <token>
```

### クエリ

```http request
page=1&grid_name=グリッド
```

| フィールド名      | データ型      | 説明         |
|-------------|-----------|------------|
| `page`      | `integer` | 現在のページ     |
| `grid_name` | `string`  | グリッド名で絞り込み |

### レスポンス

```json
{
  "total": 1,
  "last_page": 1,
  "data": [
    {
      "id": 1,
      "grid_name": "グリッド",
      "created_at": "2025-10-16 11:12:07",
      "updated_at": "2025-10-20 13:25:05",
      "grid_size_preview": "60 cm",
      "position_preview": "(67, 102)"
    }
  ]
}
```

| フィールド名                | データ型      | 説明              |
|-----------------------|-----------|-----------------|
| `total`               | `integer` | グリッド総件数         |
| `last_page`           | `integer` | 総ページ数           |
| `data`                | `array`   | グリッド一覧          |
| ├─`id`                | `integer` | グリッドID          |
| ├─`grid_name`         | `string`  | グリッド名           |
| ├─`created_at`        | `string`  | グリッド作成日時        |
| ├─`updated_at`        | `string`  | グリッド更新日時        |
| ├─`grid_size_preview` | `string`  | グリッドサイズ（単位含む）   |
| └─`position_preview`  | `string`  | グリッドの基準座標（x, y） |

# グリッドデータ削除API

## エンドポイント

`DELETE /api/grids/{grid}`

### リクエスト

### ヘッダー

```http
Accept: application/json, text/plain, */*
Authorization: Bearer <token>
```

### レスポンス

Status: `204 No Content`

レスポンスボディは空です。

# グリッド詳細API

## エンドポイント

`GET /api/grids/{grid}`

### リクエスト

### ヘッダー

```http
Accept: application/json, text/plain, */*
Authorization: Bearer <token>
```

### レスポンス

```json
{
  "grid_name": "グリッド",
  "grid_size": 30,
  "start_x": 84.47999999999999,
  "start_y": 55.67999999999999,
  "end_x": 1794.48,
  "end_y": 1735.68
}
```

| フィールド名      | データ型      | 説明             |
|-------------|-----------|----------------|
| `grid_name` | `string`  | グリッド名          |
| `grid_size` | `integer` | グリッド1マスあたりのサイズ |
| `start_x`   | `float`   | グリッド左上のX座標     |
| `start_y`   | `float`   | グリッド左上のY座標     |
| `end_x`     | `float`   | グリッド右下のX座標     |
| `end_y`     | `float`   | グリッド右下のY座標     |

# ウォール一覧API

アプリケーションクラスターに紐づくウォール一覧を取得します。

## エンドポイント

`GET /api/applications/{application_cluster}/walls`

### リクエスト

### ヘッダー

```http
Accept: application/json, text/plain, */*
Authorization: Bearer <token>
```

### クエリ

```http request
page=1&area_name=ウォール
```

| フィールド名      | データ型      | 説明        |
|-------------|-----------|-----------|
| `page`      | `integer` | 現在のページ    |
| `area_name` | `string`  | エリア名で絞り込み |

### レスポンス

```json
{
  "total": 1,
  "last_page": 1,
  "data": [
    {
      "id": 1,
      "area_name": "ウォール",
      "wall_count": 1,
      "created_at": "2026-01-05 13:08:08",
      "updated_at": "2026-01-05 13:08:56"
    }
  ]
}
```

| フィールド名         | データ型      | 説明      |
|----------------|-----------|---------|
| `total`        | `integer` | エリア総件数  |
| `last_page`    | `integer` | 総ページ数   |
| `data`         | `array`   | エリア一覧   |
| ├─`id`         | `integer` | エリアID   |
| ├─`area_name`  | `string`  | エリア名    |
| ├─`wall_count` | `integer` | ウォール数   |
| ├─`created_at` | `string`  | エリア作成日時 |
| └─`updated_at` | `string`  | エリア更新日時 |

# ウォール詳細API

## エンドポイント

`GET /api/walls/{wall}`

### リクエスト

### ヘッダー

```http
Accept: application/json, text/plain, */*
Authorization: Bearer <token>
```

### レスポンス

```json
{
  "area_name": "ウォール",
  "walls": [
    {
      "points": [
        1649,
        343,
        1655,
        454,
        1727,
        451,
        1716,
        347,
        1653,
        341
      ]
    }
  ]
}
```

| フィールド名      | データ型             | 説明                               |
|-------------|------------------|----------------------------------|
| `area_name` | `string`         | エリア名                             |
| `walls`     | `array`          | ウォール一覧                           |
| └─`points`  | `array<integer>` | 座標リスト（x1, y1, x2, y2, …, xn, yn） |

# 接続ポイント一覧API

アプリケーションクラスタに属する経路一覧を取得します。
（アプリケーションクラスタに属する経路データ一覧および、経路データ作成に使用するアプリケーションクラスタ一覧を含む）

## エンドポイント

`GET /api/applications/{application_cluster}/cluster-joints`

### リクエスト

### ヘッダー

```http
Accept: application/json, text/plain, */*
Authorization: Bearer <token>
```

### レスポンス

```json
[
  {
    "id": 1,
    "joint_point_type": "stair",
    "title": "階段",
    "direction": "up",
    "x": 140.16,
    "y": 78.72,
    "app_clusters": [
      63,
      63
    ],
    "routes": [
      1,
      2
    ]
  }
]
```

| フィールド名             | データ型             | 説明                                                                                          |
|--------------------|------------------|---------------------------------------------------------------------------------------------|
| `id`               | `integer`        | ルートID                                                                                       |
| `joint_point_type` | `string`         | ルート種別<br/>**stair**：階段<br/>**escalator**：エスカレーター<br/>**elevator**：エレベーター<br/>**point**：ポイント |
| `title`            | `string`         | ルート名                                                                                        |
| `direction`        | `string`         | ルート方向<br/>**up**：上り<br/>**down**：下り<br/>**up_down**：上下                                      |
| `x`                | `float`          | ルートのX座標                                                                                     |
| `y`                | `float`          | ルートのY座標                                                                                     |
| `app_clusters`     | `array<integer>` | アプリケーションクラスタID一覧                                                                            |
| `routes`           | `array<integer>` | ルートデータID一覧                                                                                  |

# 接続ポイント作成・更新・削除API

## エンドポイント

`POST /api/applications/{application_cluster}/cluster-joints`

### リクエスト

### ヘッダー

```http
Accept: application/json, text/plain, */*
Authorization: Bearer <token>
Content-Type: application/json
```

### リクエストボディー

```json
{
  "cluster_joints": [
    {
      "id": 1,
      "x": 504.96,
      "y": 84.48,
      "joint_point_type": "stair",
      "title": "階段",
      "direction": "up",
      "app_clusters": [
        63,
        63
      ],
      "routes": [
        1,
        2
      ]
    }
  ]
}
```

| フィールド名               | データ型             | 必須                          | 説明                                                                                             |
|----------------------|------------------|-----------------------------|------------------------------------------------------------------------------------------------|
| `cluster_joints`     | `array`          | 必須                          | 接続ポイント一覧                                                                                       |
| ├─`id`               | `integer`        | 任意（更新対象の場合は必須）              | 接続ポイントID                                                                                       |
| ├─`x`                | `float`          | 必須                          | 接続ポイントのX座標                                                                                     |
| ├─`y`                | `float`          | 必須                          | 接続ポイントのY座標                                                                                     |
| ├─`joint_point_type` | `string`         | 必須                          | 接続ポイント種別<br/>**stair**：階段<br/>**escalator**：エスカレーター<br/>**elevator**：エレベーター<br/>**point**：ポイント |
| ├─`title`            | `string`         | 必須                          | 接続ポイント名                                                                                        |
| ├─`direction`        | `string`         | 任意（階段・エスカレーター・エレベーターの場合は必須） | 進行方向<br/>**up**：上り<br/>**down**：下り<br/>**up_down**：上下                                          |
| ├─`app_clusters`     | `array<integer>` | 必須                          | アプリケーションクラスターID一覧                                                                              |
| └─`routes`           | `array<integer>` | 必須                          | ルートデータID一覧                                                                                     |

### レスポンス

Status: `201 Created`

レスポンスボディは空です。

# 経路データ一覧API

## エンドポイント

`GET /api/routes`

### リクエスト

### ヘッダー

```http
Accept: application/json, text/plain, */*
Authorization: Bearer <token>
```

### クエリ

```http request
page=1&application_cluster=63&route_name=経路データ&is_bookmark=true
```

| フィールド名                 | データ型      | 説明                                |
|------------------------|-----------|-----------------------------------|
| `page`                 | `integer` | 現在のページ                            |
| `application_cluster`  | `integer` | アプリケーションクラスターIDでフィルタ              |
| `route_name`           | `string`  | 経路データ名でフィルタ                       |
| `is_bookmark`          | `boolean` | ブックマークでフィルタ<br/>**true**：ブックマーク済み |

### レスポンス

```json
{
  "total": 1,
  "last_page": 1,
  "data": [
    {
      "id": 1,
      "area_id": 1,
      "grid_id": 1,
      "name": "経路データ",
      "start_time": "2025-12-29 00:00",
      "end_time": "2025-12-29 23:59",
      "wall_id": 1,
      "descriptions": "",
      "algorithm_id": 1,
      "process_status": 3,
      "created_at": "2026-01-05 13:24:57",
      "updated_at": "2026-01-09 18:43:00",
      "is_bookmark": true,
      "is_update": false,
      "algorithm_preview": "前後測位点を基に時間差比率で補正",
      "process_status_preview": "作成済",
      "area": {
        "id": 1,
        "area_name": "対象エリア"
      },
      "grid_parameter_set": {
        "id": 1,
        "grid_name": "グリッド"
      },
      "wall": {
        "id": 1,
        "area_name": "ウォール"
      }
    }
  ]
}
```

| フィールド名                                | データ型      | 説明                                                                                       |
|---------------------------------------|-----------|------------------------------------------------------------------------------------------|
| `total`                               | `integer` | 経路データ数                                                                                   |
| `last_page`                           | `integer` | ページ数                                                                                     |
| `data`                                | `array`   | 経路データ一覧                                                                                  |
| ├─`id`                                | `integer` | 経路データID                                                                                  |
| ├─`area_id`                           | `integer` | エリアID                                                                                    |
| ├─`grid_id`                           | `integer` | グリッドID                                                                                   |
| ├─`name`                              | `string`  | 経路データ名                                                                                   |
| ├─`start_time`                        | `string`  | 分析に使用するデータ開始日時                                                                           |
| ├─`end_time`                          | `string`  | 分析に使用するデータ終了日時                                                                           |
| ├─`wall_id`                           | `integer` | ウォールID                                                                                   |
| ├─`descriptions`                      | `string`  | 経路データの説明                                                                                 |
| ├─`algorithm_id`                      | `integer` | アルゴリズムID                                                                                 |
| ├─`process_status`                    | `integer` | 処理ステータスID                                                                                |
| ├─`created_at`                        | `string`  | 経路データ作成日時                                                                                |
| ├─`updated_at`                        | `string`  | 経路データ更新日時                                                                                |
| ├─`is_bookmark`                       | `boolean` | ブックマーク<br/>**false**：未ブックマーク<br/>**true**：ブックマーク済み                                       |
| ├─`is_update`                         | `boolean` | 経路データ作成後にエリア／グリッド／ウォールデータが変更されたかの判定<br/>**false**：経路データは通常利用可能<br/>**true**：経路データの再作成が必要 |
| ├─`algorithm_preview`                 | `string`  | アルゴリズム名                                                                                  |
| ├─`process_status_preview`            | `string`  | 処理ステータス                                                                                  |
| ├─`area`                              | `object`  | エリア情報                                                                                    |
| &nbsp;&nbsp;&nbsp;&nbsp;├─`id`        | `integer` | エリアID                                                                                    |
| &nbsp;&nbsp;&nbsp;&nbsp;└─`area_name` | `string`  | エリア名                                                                                     |
| ├─`grid_parameter_set`                | `object`  | グリッド情報                                                                                   |
| &nbsp;&nbsp;&nbsp;&nbsp;├─`id`        | `integer` | グリッドID                                                                                   |
| &nbsp;&nbsp;&nbsp;&nbsp;└─`grid_name` | `string`  | グリッド名                                                                                    |
| └─`wall`                              | `object`  | ウォール情報                                                                                   |
| &nbsp;&nbsp;&nbsp;&nbsp;├─`id`        | `integer` | ウォールID                                                                                   |
| &nbsp;&nbsp;&nbsp;&nbsp;└─`area_name` | `string`  | ウォール名                                                                                    |

# 経路データブックマーク更新API

## エンドポイント

`POST /api/routes/{route}/bookmark`

### リクエスト

### ヘッダー

```http
Accept: application/json, text/plain, */*
Authorization: Bearer <token>
```

### レスポンス

Status: `202 Accepted`

レスポンスボディは空です。

# 経路データ更新API

## エンドポイント

`PUT /api/routes/{route}`

### リクエスト

### ヘッダー

```http
Accept: application/json, text/plain, */*
Authorization: Bearer <token>
Content-Type: application/json
```

### リクエストボディー

```json
{
  "area_id": 1,
  "grid_id": 1,
  "wall_id": 1,
  "start_time": "2026-01-03 00:00",
  "end_time": "2026-01-03 23:59",
  "algorithm_id": 1,
  "name": "経路データ",
  "descriptions": ""
}
```

| フィールド名         | データ型      | 必須 | 説明          |
|----------------|-----------|----|-------------|
| `area_id`      | `integer` | 必須 | エリアID       |
| `grid_id`      | `integer` | 必須 | グリッドID      |
| `wall_id`      | `integer` | 必須 | ウォールID      |
| `start_time`   | `string`  | 必須 | 開始時間        |
| `end_time`     | `string`  | 必須 | 終了時間        |
| `algorithm_id` | `integer` | 必須 | アルゴリズムID    |
| `name`         | `string`  | 必須 | 経路データ名      |
| `descriptions` | `string`  | 任意 | 経路データの説明    |

### レスポンス

Status: `202 Accepted`

レスポンスボディは空です。

# 経路データ削除API

## エンドポイント

`DELETE /api/routes/{route}`

### リクエスト

### ヘッダー

```http
Accept: application/json, text/plain, */*
Authorization: Bearer <token>
```

### レスポンス

Status: `204 No Content`

レスポンスボディは空です。

# 経路データ詳細API

## エンドポイント

`GET /api/routes/{route}`

### リクエスト

### ヘッダー

```http
Accept: application/json, text/plain, */*
Authorization: Bearer <token>
```

### レスポンス

```json
{
  "area_id": 1,
  "grid_id": 1,
  "name": "経路データ",
  "start_time": "2026-01-03 00:00",
  "end_time": "2026-01-03 23:59",
  "wall_id": 1,
  "descriptions": "",
  "algorithm_id": 1,
  "is_bookmark": true,
  "area": {
    "id": 1,
    "area_name": "対象エリア"
  },
  "grid_parameter_set": {
    "id": 1,
    "grid_name": "グリッド"
  },
  "wall": {
    "id": 1,
    "area_name": "ウォール"
  }
}
```

| フィールド名               | データ型      | 説明                                              |
|----------------------|-----------|-------------------------------------------------|
| `area_id`            | `integer` | エリアID                                           |
| `grid_id`            | `integer` | グリッドID                                          |
| `name`               | `string`  | ルートデータ名                                         |
| `start_time`         | `string`  | 分析に使用する開始時刻                                     |
| `end_time`           | `string`  | 分析に使用する終了時刻                                     |
| `wall_id`            | `integer` | ウォールID                                          |
| `descriptions`       | `string`  | ルートデータの説明                                       |
| `algorithm_id`       | `integer` | アルゴリズムID                                        |
| `is_bookmark`        | `boolean` | ブックマークフラグ<br/>false：ブックマークしない<br/>true：ブックマークする |
| `area`               | `object`  | エリア情報                                           |
| ├─ `id`              | `integer` | エリアID                                           |
| └─ `area_name`       | `string`  | エリア名                                            |
| `grid_parameter_set` | `object`  | グリッド情報                                          |
| ├─ `id`              | `integer` | グリッドID                                          |
| └─ `grid_name`       | `string`  | グリッド名                                           |
| `wall`               | `object`  | ウォール情報                                          |
| ├─ `id`              | `integer` | ウォールID                                          |
| └─ `wall_name`       | `string`  | ウォール名                                           |

# 経路データ描画API

## エンドポイント

`GET /api/route-data/{route}/draw`

### リクエスト

### ヘッダー

```http
Accept: application/json, text/plain, */*
Authorization: Bearer <token>
```

### レスポンス

```json
{
  "data": {
    "name": "経路データ",
    "start_time": "2025-12-31 00:00",
    "end_time": "2025-12-31 23:59",
    "algorithm_id": 1,
    "is_bookmark": true
  },
  "forbidden_areas": [
    {
      "area_type": "special",
      "points": [
        47,
        1377,
        47,
        1771,
        1128,
        1771,
        1128,
        1377
      ],
      "property": null
    }
  ],
  "grid": {
    "grid_size": 40,
    "start_x": 59.519999999999996,
    "start_y": 266.88,
    "end_x": 1619.5200000000007,
    "end_y": 1386.8799999999999
  },
  "walls": [
    {
      "points": [
        105,
        320,
        92,
        541,
        305,
        560,
        433,
        314
      ]
    }
  ],
  "cluster_joints": [
    {
      "id": 1,
      "joint_point_type": "stair",
      "title": "階段",
      "direction": "up",
      "x": 140.16,
      "y": 78.72,
      "app_clusters": [
        63,
        63
      ],
      "routes": [
        1,
        2
      ]
    }
  ]
}
```

| 項目                   | 型                | 説明                                                                                          |
|----------------------|------------------|---------------------------------------------------------------------------------------------|
| `data`               | `object`         | 経路データ                                                                                       |
| ├─`name`             | `string`         | 経路データ名                                                                                      |
| ├─`start_time`       | `string`         | 分析に使用するデータの開始時間                                                                             |
| ├─`end_time`         | `string`         | 分析に使用するデータの終了時間                                                                             |
| ├─`algorithm_id`     | `integer`        | アルゴリズムID                                                                                    |
| └─`is_bookmark`      | `boolean`        | ブックマーク false:未ブックマーク true:ブックマーク済み                                                          |
| `forbidden_areas`    | `array`          | エリア一覧                                                                                       |
| ├─`area_type`        | `string`         | エリア種別 special:特殊エリア forbidden:立入禁止エリア target:対象エリア                                          |
| ├─`points`           | `array<integer>` | 座標リスト(x1,y1,x2,y2,…,xn,yn)                                                                  |
| └─`property`         | `string`         | 属性(※特殊エリアのみ適用)                                                                              |
| `grid`               | `object`         | グリッド情報                                                                                      |
| ├─`grid_size`        | `integer`        | グリッド1マスのサイズ                                                                                 |
| ├─`start_x`          | `float`          | グリッド左上角のX座標                                                                                 |
| ├─`start_y`          | `float`          | グリッド左上角のY座標                                                                                 |
| ├─`end_x`            | `float`          | グリッド右下角のX座標                                                                                 |
| └─`end_y`            | `float`          | グリッド右下角のY座標                                                                                 |
| `walls`              | `array`          | ウォール一覧                                                                                      |
| └─`points`           | `array<integer>` | 座標リスト(x1,y1,x2,y2,…,xn,yn)                                                                  |
| `cluster_joints`     | `array`          | 接続ポイント一覧                                                                                    |
| ├─`id`               | `integer`        | ルートID                                                                                       |
| ├─`joint_point_type` | `string`         | ルート種別<br/>**stair**：階段<br/>**escalator**：エスカレーター<br/>**elevator**：エレベーター<br/>**point**：ポイント |
| ├─`title`            | `string`         | ルート名                                                                                        |
| ├─`direction`        | `string`         | ルート方向<br/>**up**：上り<br/>**down**：下り<br/>**up_down**：上下                                      |
| ├─`x`                | `float`          | ルートのX座標                                                                                     |
| ├─`y`                | `float`          | ルートのY座標                                                                                     |
| ├─`app_clusters`     | `array<integer>` | アプリケーションクラスタID一覧                                                                            |
| └─`routes`           | `array<integer>` | ルートデータID一覧                                                                                  |

# リアルタイムデバイス一覧API

## エンドポイント

`GET /api/applications/{application_cluster}/realtime/device`

### リクエスト

### ヘッダー

```http
Accept: application/json, text/plain, */*
Authorization: Bearer <token>
```

### レスポンス

```json
[
  {
    "label": "全て",
    "value": "all"
  },
  {
    "label": "Device 001",
    "value": "6946b9f4-61c8-4f28-8057-296f2836df0d"
  }
]
```

| フィールド   | データ型     | 説明     |
|---------|----------|--------|
| `label` | `string` | デバイス名  |
| `value` | `string` | デバイスID |

# リアルタイムマップAPI

## エンドポイント

`POST /api/applications/{application_cluster}/realtime/data`

### リクエスト

### ヘッダー

```http
Accept: application/json, text/plain, */*
Authorization: Bearer <token>
Content-Type: application/json
```

### リクエストボディー

```json
{
  "device_ids": [
    "6946b9f4-61c8-4f28-8057-296f2836df0d"
  ]
}
```

| 項目           | 型               | 必須 | 説明           |
|--------------|-----------------|----|--------------|
| `device_ids` | `array<string>` | 任意 | デバイスIDでの絞り込み |

### レスポンス

```json
[
  {
    "label": "6946b9f4-61c8-4f28-8057-296f2836df0d",
    "value": "6946b9f4-61c8-4f28-8057-296f2836df0d",
    "x": 1577.9999999999998,
    "y": 719.9999999999999,
    "detected": "2026-01-14 13:15:09"
  }
]
```

| 項目         | 型        | 説明         |
|------------|----------|------------|
| `label`    | `string` | デバイス名      |
| `value`    | `object` | デバイスID     |
| `x`        | `float`  | デバイスのX座標   |
| `y`        | `float`  | デバイスのY座標   |
| `detected` | `string` | 位置が記録された時刻 |

# リアルタイムアラート一覧API

## エンドポイント

`GET /api/realtime-data/{route}/alert`

### リクエスト

### ヘッダー

```http
Accept: application/json, text/plain, */*
Authorization: Bearer <token>
```

### レスポンス

```json
[
  {
    "id": 1,
    "time": "2026-02-02 13:15:09",
    "message": "Device 001 entered restricted area."
  }
]
```

| フィールド    | データ型      | 説明       |
|----------|-----------|----------|
| `id`      | `integer` | アラートID   |
| `time`    | `string`  | 発生時間     |
| `message` | `string`  | アラート内容   |

# 経路データ内デバイス一覧API

## エンドポイント

`GET /api/route-data/{route}/device`

### リクエスト

### ヘッダー

```http
Accept: application/json, text/plain, */*
Authorization: Bearer <token>
```

### レスポンス

```json
[
  {
    "label": "全て",
    "value": "all"
  },
  {
    "label": "0a3b40dc-910e-4b9e-9364-fd6079063516",
    "value": "0a3b40dc-910e-4b9e-9364-fd6079063516"
  }
]
```

| フィールド   | データ型     | 説明     |
|---------|----------|--------|
| `label` | `string` | デバイス名  |
| `value` | `string` | デバイスID |

# 経路データマップAPI

## エンドポイント

`POST /api/route-data/{route}/data`

### リクエスト

### ヘッダー

```http
Accept: application/json, text/plain, */*
Authorization: Bearer <token>
Content-Type: application/json
```

### リクエストボディー

```json
{
  "device_ids": [
    "6946b9f4-61c8-4f28-8057-296f2836df0d"
  ]
}
```

| フィールド        | データ型            | 必須 | 説明           |
|--------------|-----------------|----|--------------|
| `device_ids` | `array<string>` | 任意 | デバイスIDでの絞り込み |

### レスポンス

```json
{
  "0a3b40dc-910e-4b9e-9364-fd6079063516": [
    {
      "x": 182.14953190323342,
      "y": 780.7276669654293,
      "device_id": "0a3b40dc-910e-4b9e-9364-fd6079063516"
    }
  ]
}
```

| フィールド                                  | データ型     | 説明       |
|----------------------------------------|----------|----------|
| `0a3b40dc-910e-4b9e-9364-fd6079063516` | `array`  | デバイスID   |
| `x`                                    | `float`  | デバイスのX座標 |
| `y`                                    | `float`  | デバイスのY座標 |
| `device_id`                            | `string` | デバイスID   |

# 経路データ分析後のデバイス一覧API

## エンドポイント

`GET /api/analysis-data/{route}/device`

### リクエスト

### ヘッダー

```http
Accept: application/json, text/plain, */*
Authorization: Bearer <token>
```

### レスポンス

```json
[
  {
    "label": "0a3b40dc-910e-4b9e-9364-fd6079063516",
    "value": "0a3b40dc-910e-4b9e-9364-fd6079063516"
  }
]
```

| フィールド   | データ型     | 説明     |
|---------|----------|--------|
| `label` | `string` | デバイス名  |
| `value` | `string` | デバイスID |

# アカウント一覧API

## エンドポイント

`GET /api/users`

### リクエスト

### ヘッダー

```http
Accept: application/json, text/plain, */*
Authorization: Bearer <token>
```

### クエリ

```http request
page=1&filter=user@rooking.co.jp
```

| 項目       | データ型      | 説明                    |
|----------|-----------|-----------------------|
| `page`   | `integer` | 現在のページ                |
| `filter` | `string`  | カナ名・メールアドレス・会社名での絞り込み |

### レスポンス

```json
{
  "total": 1,
  "last_page": 1,
  "data": [
    {
      "id": 1,
      "email": "user@rooking.co.jp",
      "company_name": "ROOKING, Inc.",
      "user_type": 3,
      "created_at": "2026-01-09 13:50:34",
      "updated_at": "2026-01-12 23:11:13",
      "name_preview": "林 彩花",
      "name_kana_preview": "はやし あやか",
      "user_type_preview": "会員",
      "has_update_permission": true,
      "has_delete_permission": true,
      "has_login_user_permission": false,
      "applications": [
        {
          "app_name": "駅すぱあと本番用",
          "pivot": {
            "user_id": 1,
            "app_id": 83
          }
        }
      ],
      "app_clusters": [
        {
          "cluster_id": "6ec48ca4-90d5-4609-a9c7-a4aa28b9c80a",
          "pivot": {
            "user_id": 1,
            "app_cluster_id": 63
          },
          "cluster": {
            "cluster_id": "6ec48ca4-90d5-4609-a9c7-a4aa28b9c80a",
            "cluster_name": "大阪駅1F"
          }
        }
      ]
    }
  ]
}
```

| 項目                                                                                       | データ型      | 説明                                                                       |
|------------------------------------------------------------------------------------------|-----------|--------------------------------------------------------------------------|
| `total`                                                                                  | `integer` | アカウント総数                                                                  |
| `last_page`                                                                              | `integer` | 総ページ数                                                                    |
| `data`                                                                                   | `array`   | アカウント一覧                                                                  |
| &nbsp;&nbsp;&nbsp;&nbsp;├─`id`                                                           | `integer` | アカウントID                                                                  |
| &nbsp;&nbsp;&nbsp;&nbsp;├─`email`                                                        | `string`  | メールアドレス                                                                  |
| &nbsp;&nbsp;&nbsp;&nbsp;├─`company_name`                                                 | `string`  | 会社名                                                                      |
| &nbsp;&nbsp;&nbsp;&nbsp;├─`user_type`                                                    | `integer` | アカウント種別<br/>**1**：Beacrewアカウント<br/>**2**：Tenant管理者アカウント<br/>**3**：一般ユーザー |
| &nbsp;&nbsp;&nbsp;&nbsp;├─`created_at`                                                   | `string`  | アカウント作成日時                                                                |
| &nbsp;&nbsp;&nbsp;&nbsp;├─`updated_at`                                                   | `string`  | アカウント更新日時                                                                |
| &nbsp;&nbsp;&nbsp;&nbsp;├─`name_preview`                                                 | `string`  | 氏名（漢字）                                                                   |
| &nbsp;&nbsp;&nbsp;&nbsp;├─`name_kana_preview`                                            | `string`  | 氏名（カナ）                                                                   |
| &nbsp;&nbsp;&nbsp;&nbsp;├─`user_type_preview`                                            | `string`  | アカウント種別名（表示用）                                                            |
| &nbsp;&nbsp;&nbsp;&nbsp;├─`has_update_permission`                                        | `boolean` | 当該アカウント情報の更新権限                                                           |
| &nbsp;&nbsp;&nbsp;&nbsp;├─`has_delete_permission`                                        | `boolean` | 当該アカウントの削除権限                                                             |
| &nbsp;&nbsp;&nbsp;&nbsp;├─`has_login_user_permission`                                    | `boolean` | 当該アカウントとしてログインする権限                                                       |
| &nbsp;&nbsp;&nbsp;&nbsp;├─`applications`                                                 | `array`   | アカウントに紐づくアプリケーション一覧                                                      |
| &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;├─`app_name`                             | `string`  | アプリケーション名                                                                |
| &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;└─`pivot`                                | `object`  | アカウントとアプリケーションの紐付け情報                                                     |
| &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;├─`user_id`      | `integer` | アカウントID                                                                  |
| &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;└─`app_id`       | `integer` | アプリケーションID                                                               |
| &nbsp;&nbsp;&nbsp;&nbsp;└─`app_clusters`                                                 | `array`   | アカウントに紐づくアプリケーションクラスター一覧                                                 |
| &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;├─`cluster_id`                           | `string`  | クラスターID                                                                  |
| &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;├─`pivot`                                | `object`  | アカウントとアプリケーションクラスターの紐付け情報                                                |
| &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;├─`user_id`            | `integer` | アカウントID                                                                  |
| &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;└─`app_cluster_id`     | `integer` | アプリケーションクラスターID                                                          |
| &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;└─`cluster`                              | `object`  | クラスター情報                                                                  |
| &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;├─`cluster_id`   | `string`  | クラスターID                                                                  |
| &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;└─`cluster_name` | `string`  | クラスター名                                                                   |

# アカウント情報削除API

## エンドポイント

`DELETE /api/users/{user}`

### リクエスト

### ヘッダー

```http
Accept: application/json, text/plain, */*
Authorization: Bearer <token>
```

### レスポンス

Status: `204 No Content`

レスポンスボディは空です。

# 管理者権限によるログインAPI

サーバーは、新しいCookieをブラウザに設定し、別のアカウントとしてログインできるようにします。

## エンドポイント

`GET /api/switch-user/{user}`

### リクエスト

### ヘッダー

```http
Accept: application/json, text/plain, */*
Authorization: Bearer <token>
```

### レスポンス

Status: `204 No Content`

レスポンスボディは空です。サーバーは `Set-Cookie` ヘッダーで新しいログインCookieを返します。

# アカウント詳細API

## エンドポイント

`GET /api/users/{user}`

### リクエスト

### ヘッダー

```http
Accept: application/json, text/plain, */*
Authorization: Bearer <token>
```

### レスポンス

```json
{
  "id": 2,
  "email": "user@rooking.co.jp",
  "user_type": 3,
  "last_name": "林",
  "first_name": "彩花",
  "last_name_kana": "はやし",
  "first_name_kana": "あやか",
  "company_name": "ROOKING, Inc.",
  "memo": null,
  "has_delete_permission": true,
  "applications": [
    {
      "id": 83,
      "app_name": "駅すぱあと本番用",
      "pivot": {
        "user_id": 1,
        "app_id": 83
      }
    }
  ],
  "app_clusters": [
    {
      "cluster_id": "6ec48ca4-90d5-4609-a9c7-a4aa28b9c80a",
      "pivot": {
        "user_id": 21,
        "app_cluster_id": 63
      },
      "cluster": {
        "cluster_id": "6ec48ca4-90d5-4609-a9c7-a4aa28b9c80a",
        "cluster_name": "大阪駅1F"
      }
    }
  ]
}
```

| 項目                                                               | データ型      | 説明                                                                       |
|------------------------------------------------------------------|-----------|--------------------------------------------------------------------------|
| `id`                                                             | `integer` | アカウントID                                                                  |
| `email`                                                          | `string`  | メールアドレス                                                                  |
| `user_type`                                                      | `integer` | アカウント種別<br/>**1**：Beacrewアカウント<br/>**2**：Tenant管理者アカウント<br/>**3**：一般ユーザー |
| `last_name`                                                      | `string`  | 姓（漢字）                                                                    |
| `first_name`                                                     | `string`  | 名（漢字）                                                                    |
| `last_name_kana`                                                 | `string`  | 姓（カナ）                                                                    |
| `first_name_kana`                                                | `string`  | 名（カナ）                                                                    |
| `company_name`                                                   | `string`  | 会社名                                                                      |
| `memo`                                                           | `string`  | メモ                                                                       |
| `has_delete_permission`                                          | `boolean` | 当該アカウントの削除権限                                                             |
| ├─`applications`                                                 | `array`   | アカウントに紐づくアプリケーション一覧                                                      |
| &nbsp;&nbsp;&nbsp;&nbsp;├─`id`                                   | `string`  | アプリケーションID                                                               |
| &nbsp;&nbsp;&nbsp;&nbsp;├─`app_name`                             | `string`  | アプリケーション名                                                                |
| &nbsp;&nbsp;&nbsp;&nbsp;└─`pivot`                                | `object`  | アカウントとアプリケーションの紐付け情報                                                     |
| &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;├─`user_id`      | `integer` | アカウントID                                                                  |
| &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;└─`app_id`       | `integer` | アプリケーションID                                                               |
| └─`app_clusters`                                                 | `array`   | アカウントに紐づくアプリケーションクラスター一覧                                                 |
| &nbsp;&nbsp;&nbsp;&nbsp;├─`cluster_id`                           | `string`  | クラスターID                                                                  |
| &nbsp;&nbsp;&nbsp;&nbsp;├─`pivot`                                | `object`  | アカウントとアプリケーションクラスターの紐付け情報                                                |
| &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;├─`user_id`            | `integer` | アカウントID                                                                  |
| &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;└─`app_cluster_id`     | `integer` | アプリケーションクラスターID                                                          |
| &nbsp;&nbsp;&nbsp;&nbsp;└─`cluster`                              | `object`  | クラスター情報                                                                  |
| &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;├─`cluster_id`   | `string`  | クラスターID                                                                  |
| &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;└─`cluster_name` | `string`  | クラスター名                                                                   |

# アプリケーション選択一覧API

## エンドポイント

`GET /api/application-option`

### リクエスト

### ヘッダー

```http
Accept: application/json, text/plain, */*
Authorization: Bearer <token>
```

### レスポンス

```json
[
  {
    "label": "全て",
    "value": "all"
  },
  {
    "label": "駅すぱあと本番用",
    "value": 83
  }
]
```

| 項目      | データ型              | 説明         |
|---------|-------------------|------------|
| `label` | `string`          | アプリケーション名  |
| `value` | `string\|integer` | アプリケーションID |

# アプリケーションクラスタ選択一覧API

## エンドポイント

`GET /api/application-cluster-option`

### リクエスト

### ヘッダー

```http
Accept: application/json, text/plain, */*
Authorization: Bearer <token>
```

### レスポンス

```json
[
  {
    "label": "大阪駅1F",
    "value": 63
  }
]
```

| 項目      | データ型      | 説明              |
|---------|-----------|-----------------|
| `label` | `string`  | アプリケーションクラスター名  |
| `value` | `integer` | アプリケーションクラスターID |

# Beacrewアカウント更新API

## エンドポイント

`PUT /api/system-admin/{system_admin}`

### リクエスト

### ヘッダー

```http
Accept: application/json, text/plain, */*
Authorization: Bearer <token>
Content-Type: application/json
```

### リクエストボディー

```json
{
  "last_name": "林",
  "first_name": "彩花",
  "last_name_kana": "はやし",
  "first_name_kana": "あやか",
  "email": "user@rooking.co.jp",
  "company_name": "ROOKING, Inc.",
  "memo": null
}
```

| 項目                | データ型     | 必須 | 説明      |
|-------------------|----------|----|---------|
| `last_name`       | `string` | はい | 姓（漢字）   |
| `first_name`      | `string` | はい | 名（漢字）   |
| `last_name_kana`  | `string` | はい | 姓（カナ）   |
| `first_name_kana` | `string` | はい | 名（カナ）   |
| `email`           | `string` | はい | メールアドレス |
| `company_name`    | `string` | はい | 会社名     |
| `memo`            | `string` | はい | メモ      |

### レスポンス

Status: `202 Accepted`

レスポンスボディは空です。

# テナント管理者アカウント作成API

## エンドポイント

`POST /api/tenant-admin`

### リクエスト

### ヘッダー

```http
Accept: application/json, text/plain, */*
Authorization: Bearer <token>
Content-Type: application/json
```

### リクエストボディー

```json
{
  "last_name": "林",
  "first_name": "彩花",
  "last_name_kana": "はやし",
  "first_name_kana": "あやか",
  "email": "user@rooking.co.jp",
  "company_name": "ROOKING, Inc.",
  "memo": null,
  "applications": [
    83
  ]
}
```

| 項目                | データ型             | 必須 | 説明           |
|-------------------|------------------|----|--------------|
| `last_name`       | `string`         | はい | 姓（漢字）        |
| `first_name`      | `string`         | はい | 名（漢字）        |
| `last_name_kana`  | `string`         | はい | 姓（カナ）        |
| `first_name_kana` | `string`         | はい | 名（カナ）        |
| `email`           | `string`         | はい | メールアドレス      |
| `company_name`    | `string`         | はい | 会社名          |
| `memo`            | `string`         | はい | メモ           |
| `applications`    | `array<integer>` | はい | アプリケーションID一覧 |

### レスポンス

Status: `201 Created`

レスポンスボディは空です。

# テナント管理者アカウント更新API

## エンドポイント

`PUT /api/tenant-admin/{tenant_admin}`

### リクエスト

### ヘッダー

```http
Accept: application/json, text/plain, */*
Authorization: Bearer <token>
Content-Type: application/json
```

### リクエストボディー

```json
{
  "last_name": "林",
  "first_name": "彩花",
  "last_name_kana": "はやし",
  "first_name_kana": "あやか",
  "email": "user@rooking.co.jp",
  "company_name": "ROOKING, Inc.",
  "memo": null,
  "applications": [
    83
  ]
}
```

| 項目                | データ型             | 必須 | 説明           |
|-------------------|------------------|----|--------------|
| `last_name`       | `string`         | 必須 | 姓（漢字）        |
| `first_name`      | `string`         | 必須 | 名（漢字）        |
| `last_name_kana`  | `string`         | 必須 | 姓（カナ）        |
| `first_name_kana` | `string`         | 必須 | 名（カナ）        |
| `email`           | `string`         | 必須 | メールアドレス      |
| `company_name`    | `string`         | 必須 | 会社名          |
| `memo`            | `string`         | 必須 | メモ           |
| `applications`    | `array<integer>` | 必須 | アプリケーションID一覧 |

### レスポンス

Status: `202 Accepted`

レスポンスボディは空です。

# ユーザーアカウント作成API

## エンドポイント

`POST /api/member`

### リクエスト

### ヘッダー

```http
Accept: application/json, text/plain, */*
Authorization: Bearer <token>
Content-Type: application/json
```

### リクエストボディー

```json
{
  "last_name": "林",
  "first_name": "彩花",
  "last_name_kana": "はやし",
  "first_name_kana": "あやか",
  "email": "user@rooking.co.jp",
  "memo": null,
  "application_clusters": [
    83
  ]
}
```

| 項目                     | データ型             | 必須 | 説明                |
|------------------------|------------------|----|-------------------|
| `last_name`            | `string`         | 必須 | 姓（漢字）             |
| `first_name`           | `string`         | 必須 | 名（漢字）             |
| `last_name_kana`       | `string`         | 必須 | 姓（カナ）             |
| `first_name_kana`      | `string`         | 必須 | 名（カナ）             |
| `email`                | `string`         | 必須 | メールアドレス           |
| `memo`                 | `string`         | 必須 | メモ                |
| `application_clusters` | `array<integer>` | 必須 | アプリケーションクラスターID一覧 |

### レスポンス

Status: `201 Created`

レスポンスボディは空です。

# ユーザーアカウント更新API

## エンドポイント

`PUT /api/member/{member}`

### リクエスト

### ヘッダー

```http
Accept: application/json, text/plain, */*
Authorization: Bearer <token>
Content-Type: application/json
```

レスポンスボディは空です。
### リクエストボディー

```json
{
  "last_name": "林",
  "first_name": "彩花",
  "last_name_kana": "はやし",
  "first_name_kana": "あやか",
  "email": "user@rooking.co.jp",
  "memo": null,
  "application_clusters": [
    63
  ]
}
```

| 項目                     | データ型             | 必須 | 説明                |
|------------------------|------------------|----|-------------------|
| `last_name`            | `string`         | 必須 | 姓（漢字）             |
| `first_name`           | `string`         | 必須 | 名（漢字）             |
| `last_name_kana`       | `string`         | 必須 | 姓（カナ）             |
| `first_name_kana`      | `string`         | 必須 | 名（カナ）             |
| `email`                | `string`         | 必須 | メールアドレス           |
| `memo`                 | `string`         | 必須 | メモ                |
| `application_clusters` | `array<integer>` | 必須 | アプリケーションクラスターID一覧 |

### レスポンス

Status: `202 Accepted`

