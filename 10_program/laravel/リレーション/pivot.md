**pivot = 多対多（belongsToMany / morphToMany）の中間テーブル1行を表す特別オブジェクト。**  
`withPivot()` や `withTimestamps()` で **pivot に含めるカラム**を宣言する。

# 1. 基本定義

## belongsToMany
```php
// Post.php
public function tags()
{
    // デフォルト: post_tag, post_id, tag_id
    return $this->belongsToMany(Tag::class) 
                ->withTimestamps() // pivotのcreated_at,updated_at
                ->withPivot('priority'); // 追加カラム
}
```

## 取得（読む）
```php
$post = Post::with('tags')->find($id);

foreach ($post->tags as $tag) {
    $tag->name;
    $tag->pivot->priority; // withPivot('priority')
    $tag->pivot->created_at; // withTimestamps()
}
```

## pivot 条件付き Eager Load
```php
Post::with(['tags' => fn($q) => $q->wherePivot('priority', '>=', 10)])
    ->get();
```

## 並び替え（pivot カラム）
```php
Post::with(['tags' => fn($q) => $q->orderByPivot('priority', 'desc')])->get();
```

## 登録・更新・削除（書く）
```php
// 追加（中間テーブルに行を追加）
$post->tags()->attach($tagId, ['priority' => 10]);

// 複数一括
$post->tags()->attach([
  3 => ['priority' => 5],
  5 => ['priority' => 20],
]);

// 更新（既存pivot行の更新）
$post->tags()->updateExistingPivot($tagId, ['priority' => 15]);

// 削除（pivot行を削除）
$post->tags()->detach($tagId);

// 置き換え（存在しないものは追加、余分は削除）
$post->tags()->sync([1 => ['priority' => 2], 5 => ['priority' => 9]]);

// 追加のみ（既存は残す）
$post->tags()->syncWithoutDetaching([7 => ['priority' => 1]]);
```

## クエリ（絞り込み）
```php
// pivot 条件
Post::whereHas('tags', fn($q) => $q->wherePivot('priority', '>=', 10))->get();

// in / not in
Post::whereHas('tags', fn($q) => $q->wherePivotIn('priority', [1,2,3]))->get();
Post::whereHas('tags', fn($q) => $q->wherePivotNotIn('priority', [0]))->get();

// null 判定
Post::whereHas('tags', fn($q) => $q->wherePivotNull('deleted_at'))->get();
```
