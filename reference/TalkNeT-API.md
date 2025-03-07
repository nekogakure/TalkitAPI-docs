# TalkNeT common API 
## OpenAPI仕様
[TalkNeT-API.yaml](https://github.com/nekogakure/TalkitAPI-docs/blob/main/talkNeT-API.yaml)
## バージョン
- **API バージョン**: 1.0.0

## エンドポイント
`https://nandeyanen.ie-t.net/talkit/api/v1/TalkNeT`
### 1. 投稿の作成
**POST /posts**
- 認証済みのユーザーが新しい投稿を作成できます。
- **リクエストヘッダー:**
  ```
  X-Session-Id: {sessionId}
  ```
- **リクエストボディ:**
  ```json
  {
    "title": "string",
    "content": "string"
  }
  ```
- **レスポンス:**
  - `201 Created`: 投稿成功 `{ "postId": "string" }`
  - `401 Unauthorized`: 認証失敗

### 2. 投稿の取得 (一覧)
**GET /posts?type={latest|random}&count={1-100}**
- 最新またはランダムな投稿のID一覧を取得できます。
- **レスポンス:**
  - `200 OK`: 投稿一覧取得成功 `[{ "postId": "string", "content": "string", "author": "string", "createdAt": "date-time", "likes": "integer" }, ...]`

### 3. 特定の投稿の取得
**GET /posts/{postId}**
- 指定した投稿の詳細を取得します。
- **レスポンス:**
  - `200 OK`: 投稿取得成功 `{ "postId": "string", "content": "string", "author": "string", "createdAt": "date-time" }`
  - `404 Not Found`: 投稿が存在しない

### 4. 投稿の編集
**PATCH /posts/{postId}**
- 認証済みのユーザーが自身の投稿を編集できます。
- **リクエストヘッダー:**
  ```
  X-Session-Id: {sessionId}
  ```
- **リクエストボディ:**
  ```json
  {
    "content": "string"
  }
  ```
- **レスポンス:**
  - `200 OK`: 編集成功
  - `401 Unauthorized`: 認証失敗
  - `403 Forbidden`: 権限なし
  - `404 Not Found`: 投稿が存在しない

### 5. 投稿の削除
**DELETE /posts/{postId}**
- 認証済みのユーザーが自身の投稿を削除できます。
- **リクエストヘッダー:**
  ```
  X-Session-Id: {sessionId}
  ```
- **レスポンス:**
  - `200 OK`: 削除成功
  - `401 Unauthorized`: 認証失敗
  - `403 Forbidden`: 権限なし

### 6. コメントの投稿
**POST /posts/{postId}/comments**
- 認証済みのユーザーが投稿にコメントできます。
- **リクエストヘッダー:**
  ```
  X-Session-Id: {sessionId}
  ```
- **リクエストボディ:**
  ```json
  {
    "comment": "string"
  }
  ```
- **レスポンス:**
  - `201 Created`: コメント成功 `{ "commentId": "string" }`
  - `401 Unauthorized`: 認証失敗
  - `404 Not Found`: 投稿が存在しない

### 7. コメントの取得
**GET /posts/{postId}/comments**
- 指定した投稿のコメント一覧を取得します。
- **レスポンス:**
  - `200 OK`: コメント取得成功 `[{ "commentId": "string", "comment": "string", "author": "string", "createdAt": "date-time" }, ...]`
  - `404 Not Found`: 投稿が存在しない

### 8. コメントの編集
**PATCH /posts/{postId}/comments/{commentId}**
- 認証済みのユーザーが自身のコメントを編集できます。
- **リクエストヘッダー:**
  ```
  X-Session-Id: {sessionId}
  ```
- **リクエストボディ:**
  ```json
  {
    "comment": "string"
  }
  ```
- **レスポンス:**
  - `200 OK`: 編集成功
  - `401 Unauthorized`: 認証失敗
  - `403 Forbidden`: 権限なし
  - `404 Not Found`: コメントが存在しない

### 9. 投稿に「いいね」
**POST /posts/{postId}/love**
- 認証済みのユーザーが投稿に「いいね」を付けることができます。
- **リクエストヘッダー:**
  ```
  X-Session-Id: {sessionId}
  ```
- **リクエストボディ:**
  ```json
  {
    "favorite": true
  }
  ```
- **レスポンス:**
  - `200 OK`: いいね成功
  - `401 Unauthorized`: 認証失敗
  - `404 Not Found`: 投稿が存在しない


