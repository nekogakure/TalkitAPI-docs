# TalkNeT API
## バージョン
- **API バージョン**: 1.0.0

## エンドポイント

### 1. 投稿の作成
**POST /posts**
- 認証済みのユーザーが新しい投稿を作成できます。
- **リクエストボディ:**
  ```json
  {
    "sessionId": "string",
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
  - `200 OK`: 投稿一覧取得成功 `[{ "postId": "string" }, ...]`

### 3. 特定の投稿の取得
**GET /posts/{postId}**
- 指定した投稿の詳細を取得します。
- **レスポンス:**
  - `200 OK`: 投稿取得成功 `{ "postId": "string", "content": "string", "author": "string", "createdAt": "date-time" }`
  - `404 Not Found`: 投稿が存在しない

### 4. 投稿の削除

**POST /posts/{postId}/delete**
- 認証済みのユーザーが自身の投稿を削除できます。
- **リクエストボディ**:
  ```json
    {
      "sessionId": "string"
    }
  ```
- **レスポンス**:
  - 200 OK: 削除成功
  - 401 Unauthorized: 認証失敗
  - 403 Forbidden: 権限なし

### 5. コメントの投稿
**POST /posts/{postId}/comments**
- 認証済みのユーザーが投稿にコメントできます。
- **リクエストボディ:**
  ```json
  {
    "sessionId": "string",
    "comment": "string"
  }
  ```
- **レスポンス:**
  - `201 Created`: コメント成功 `{ "commentId": "string" }`
  - `401 Unauthorized`: 認証失敗
  - `404 Not Found`: 投稿が存在しない

### 6. 投稿に「いいね」
**POST /posts/{postId}/love**
- 認証済みのユーザーが投稿に「いいね」を付けることができます。
- **リクエストボディ:**
  ```json
  {
    "sessionId": "string"
  }
  ```
- **レスポンス:**
  - `200 OK`: いいね成功
  - `401 Unauthorized`: 認証失敗
  - `404 Not Found`: 投稿が存在しない


