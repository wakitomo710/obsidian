```php
class Country extends Model
{
    public function posts()
    {
        return $this->hasManyThrough(
            Post::class,   // 目的のモデル
            User::class,   // 中間モデル
            'country_id',  // 中間モデル(users)の外部キー
            'user_id',     // 目的モデル(posts)の外部キー
            'id',          // 自分(countries)のローカルキー
            'id'           // 中間モデル(users)のローカルキー
        );
    }
}
```
- 第1引数：最終的に欲しいモデル
- 第2引数：経由する中間モデル
- 第3引数：中間モデル上の外部キー（Countryに対する）
- 第4引数：目的モデル上の外部キー（Userに対する）
- 第5引数：Countryのローカルキー
- 第6引数：Userのローカルキー