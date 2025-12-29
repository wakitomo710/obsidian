
| クラス名                            | 説明                                        | 親クラス                       |
| ------------------------------- | ----------------------------------------- | -------------------------- |
| `Throwable`                     | すべての例外 (`Exception`) とエラー (`Error`) の親クラス | -                          |
| **[1] Exception 系 (一般的なエラー処理)** | -                                         | `Throwable`                |
| `Exception`                     | 一般的な例外クラス (`try...catch` でよく使う)           | `Throwable`                |
| `ErrorException`                | 通常のエラー (`E_WARNING` など) を例外に変換するために使う     | `Exception`                |
| `LogicException`                | ロジックの誤りによる例外（予期しないメソッド呼び出しなど）             | `Exception`                |
| `BadFunctionCallException`      | 存在しない関数を呼び出した                             | `LogicException`           |
| `BadMethodCallException`        | 存在しないメソッドを呼び出した                           | `BadFunctionCallException` |
| `InvalidArgumentException`      | 間違った引数を渡した                                | `LogicException`           |
| `DomainException`               | 値が妥当な範囲にない                                | `LogicException`           |
| `LengthException`               | 長さが許容範囲外                                  | `LogicException`           |
| `OutOfRangeException`           | 許容範囲外の値を取得                                | `LogicException`           |
| `RuntimeException`              | 実行時のエラー                                   | `Exception`                |
| `OutOfBoundsException`          | 許容範囲外のキーを取得                               | `RuntimeException`         |
| `OverflowException`             | 値が上限を超えた                                  | `RuntimeException`         |
| `UnderflowException`            | 取り出す要素がないのに取り出そうとした                       | `RuntimeException`         |
| `RangeException`                | 許容範囲外の値を設定                                | `RuntimeException`         |
| `UnexpectedValueException`      | 予期しない値が渡された                               | `RuntimeException`         |
| **[2] Error 系 (致命的エラーの処理)**     | -                                         | `Throwable`                |
| `Error`                         | 致命的エラーを例外として処理するための基底クラス                  | `Throwable`                |
| `ArithmeticError`               | 数学的な計算エラー (0 で割るなど)                       | `Error`                    |
| `DivisionByZeroError`           | 0 での除算エラー                                 | `ArithmeticError`          |
| `AssertionError`                | `assert()` での失敗                           | `Error`                    |
| `TypeError`                     | 間違った型の引数や戻り値を使用                           | `Error`                    |
| `ParseError`                    | `eval()` などの構文解析エラー                       | `Error`                    |
