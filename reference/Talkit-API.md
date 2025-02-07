# Talkit API 
## OpenAPI仕様
[Talkit-API.yaml](https://github.com/nekogakure/TalkitAPI-docs/blob/main/Talkit-API.yaml)
## バージョン
- **API バージョン**: 1.0.0

## エンドポイント

### 1. ユーザーログイン
**POST /login**
- ユーザー名とパスワードでログインし、成功するとセッションIDを発行します。
- **リクエストボディ:**
  ```json
  {
    "username": "string",
    "password": "string"
  }
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
