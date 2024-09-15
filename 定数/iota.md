# iota

Goにおける連番定数生成するもの。


例 iotaを使わない連番定数の宣言

```
type Status int

const (
  Draft Status = 0
  Applived Status = 1
  Approved Status = 2
)
```

例 iotaを使った連番定数の宣言

```
type Status int

const (
  Draft Status = iota
  Applived Status = iota
  Approved Status = iota
)
```

# 特徴
  
- 値に意味がなく、それぞれが違う値であれば良い
- 値に意味があったり、DBなどに保存する場合はiotaを使わない
- 順番が変わると値が変わってしまう
- 2つめ以降のConstSpecの右辺を省略できる

  例
  ```
  const (
      A = iota
      B
      C
  )
  ```
  
ここで、BやCの右辺に明示的な値は書かれていないが、これは**直前のA = iota**の式がそのまま継承されている。
iotaは行ごとに自動的に1ずつ増加するため、このコードは次のように解釈されます。

  ```
  const (
      A = iota // 0
      B = iota // 1
      C = iota // 2
  )
  ```
つまり、BやCの右辺を省略しても、それぞれに自動的にiotaの値が割り当てられ、iotaは行ごとに1ずつ増加する。
