# Talker common API 
## OpenAPI仕様
[Talker-API.yaml](https://github.com/nekogakure/TalkitAPI-docs/blob/main/Talker-API.yaml)
## バージョン
- **API バージョン**: 1.0.0

## エンドポイント
`https://nandeyanen.ie-t.net/talkit/api/v1/Talker`
### 1. メッセージ一覧取得
**GET /messages?count={0, 100}**
- 最新のメッセージをcount分取得します。
- **リクエストボディ:**
  ```json
  {}
  ```
- **レスポンス:**
  - `200 OK`: ログイン成功 `{ "sessionId": "string" }`
  - `401 Unauthorized`: 認証失敗

### 2. ユーザーログアウト
**POST /logout**
- セッションIDを無効化し、ログアウトします。
- **リクエストボディ:**
  ```json
  {
    "sessionId": "string"
  }
  ```
- **レスポンス:**
  - `200 OK`: ログアウト成功
  - `401 Unauthorized`: 無効なセッションID

### 3. 通知取得
**GET /notifications**
- 通知を取得します。
- **レスポンス:**
  - `200 OK`: 通知取得成功
  - `401 Unauthorized`: 認証失敗
  - **レスポンスボディ:**
  ```json
  {
    "notices": [
      {
        "type": "string",
        "postUrl": "string",
        "user": "string",
        "timestamp": "date-time"
      }
    ]
  }
  ```
