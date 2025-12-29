```php
// Post モデル
public function user()
{
    return $this->belongsTo(User::class, 'user_id', 'id');
}
```
- 第1引数：関連するモデル名（必須）
- 第2引数：自分（子）テーブルの「外部キー」
- 第3引数：親テーブルの「ローカルキー」