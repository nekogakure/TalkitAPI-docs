# Talkit common API 
## OpenAPI仕様
[Talkit-API.yaml](https://github.com/nekogakure/TalkitAPI-docs/blob/main/Talkit-API.yaml)
## バージョン
- **API バージョン**: 1.0.0

## エンドポイント
`https://nandeyanen.ie-t.net/talkit/api/v1/Talker`
### 1. メッセージ取得
**GET /messages?count={1, 100}**
- 最新のメッセージを取得します。countで取得するメッセージ数を指定できます。
- **リクエストヘッダー:**
  ```
  X-Session-Id: {sessionId}
  ```
- **リクエストボディ:**
  ```json
  なし
  ```
- **レスポンス:**
  - `200 OK`: 取得成功
  ```json
    {
    "messages": [
      {
        "sender": "string",
        "recipient": "string",
        "content": "string",
        "title": "string",
        "timestamp": "date-time"
      }
    ]
  }
  ```
  - `401 Unauthorized`: 認証失敗

### 2. メッセージ送信
**POST /send**
- メッセージを送信します
- **リクエストヘッダー:**
  ```
  X-Session-Id: {sessionId}
  ```
- **リクエストボディ:**
  ```json
  {
    "recipient": "string",
    "title": "string",
    "content": "string"
  }
  ```
- **レスポンス:**
  - `200 OK`: 送信完了
  - `401 Unauthorized`: 認証失敗
  - `404 NotFound`: ユーザーが存在しない

### 3. 通知取得
**GET /user_messages?username={username}**
- 特定ユーザーとのメッセージをすべて取得します。
- **リクエストヘッダー:**
  ```
  X-Session-Id: {sessionId}
  ```
- **レスポンス:**
  - `200 OK`: 取得成功
  ```json
    {
    "messages": [
      {
        "sender": "string",
        "recipient": "string",
        "content": "string",
        "title": "string",
        "timestamp": "date-time"
      }
    ]
  }
  ```
  - `401 Unauthorized`: 認証失敗
  - `404 NotFound`: ユーザーが存在しない

