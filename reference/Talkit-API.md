# Talkit common API 
## OpenAPI仕様
[Talkit-API.yaml](https://github.com/nekogakure/TalkitAPI-docs/blob/main/Talkit-API.yaml)
## バージョン
- **API バージョン**: 1.0.0

## エンドポイント
`https://nandeyanen.ie-t.net/talkit/api/v1`
### 1. ユーザーログイン
**POST /login**
- メールアドレスとパスワードでログインし、成功するとセッションIDを発行します。
- **リクエストヘッダー:**
  ```
  X-Password: {password}
  ```
- **リクエストボディ:**
  ```json
  {
    "email": "string"
  }
  ```
- **レスポンス:**
  - `200 OK`: ログイン成功 `{ "sessionId": "string" }`
  - `401 Unauthorized`: 認証失敗

### 2. ユーザーログアウト
**POST /logout**
- セッションIDを無効化し、ログアウトします。
- **リクエストヘッダー:**
  ```
  X-Session-Id: {sessionId}
  ```
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
- **リクエストヘッダー:**
  ```
  X-Session-Id: {sessionId}
  ```
- **レスポンス:**
  - `200 OK`: 通知取得成功
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
  - `401 Unauthorized`: 認証失敗

### 4. ユーザー情報取得
**GET /users**
ユーザー名、プロフィール、アイコンを返します
**リクエストボディ**

    ```json
    {
      "username": "string"
    }
    ```
**レスポンス**
  - `200 OK`: ユーザー情報取得成功
    ```json
    {
      "users": [
        {
          "username": "string",
          "iconUrl": "string",
          "profile": "string"
        }
      ]
    }
    ```
  - `404 NotFound`: ユーザーが存在しない 


