---
tags:
  - note
---
> [!IMPORTANT]
> このテンプレート[[02_note]]の内容（見出しNote）はサンプルです。
> ご自分にとって使いやすいように編集してください。

## note
serviceでgetCondition
newインスタンス作成(引数を渡す)
```
return new Hohoge(argument1: $argument1, argument2 $argument2)
```
```
public function __construct(
	praivte readonly $argument1,
	praivte readonly $argument2,
) {
	$this->argument1 = argument1;
	$this->argument1 = argument2;
}
```