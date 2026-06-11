JapanRefund-project/
├── pnpm-workspace.yaml    # pnpm workspacesを定義
├── package.json
├── pnpm-lock.yaml
├── docker-compose.yml.     # 開発環境用のDocker compose
│
├── docs/
│   ├── OpenAPI
│   ├── specs/                      # ドキュメント
│   └── ...
│
├── infra/                                  # CDKによるインフラ管理
│
├── backend/                           # Backend API (Laravel 12+)
│   ├── composer.json
│   ├── docker                        # Multi-stage Docker
│   ├── app/                            # APIロジックのソースコード
│   └── ...
│
└── apps/                                # Javascriptアプリケーションを格納するディレクトリ (Frontend)
├── traveler/                      # 旅行者向けWeb App（React + Vite + Tailwind）
│   ├── package.json
│   ├── docker/                # Multi-stage Docker
│   ├── src/                       # 旅行者向け画面のソースコード
│   ├── OpenAPI/                 # OpenAPI
│   └── ...
│
└── admin/                        # 管理者向け管理画面（React + Vite + Tailwind + Shadcn UI）
├── package.json
├── docker                    # Multi-stage Docker
├── src/                         # 管理画面のソースコード
├── OpenAPI/               # OpenAPI
└── ...
└── generator/                   # Frontend向け型生成（Type Generation）およびBackend向けリクエスト定義を担当
├── package.json
├── src/                         # 管理画面のソースコード
└── ...
