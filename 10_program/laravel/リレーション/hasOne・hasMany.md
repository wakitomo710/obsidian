```php
// User モデル
public function posts()
{
    return $this->hasMany(Post::class, 'user_id', 'id');
}
```
- 第1引数：関連するモデル名（必須）
- 第2引数：相手（子）テーブルの「外部キー」
- 第3引数：自分（親）テーブルの「ローカルキー」