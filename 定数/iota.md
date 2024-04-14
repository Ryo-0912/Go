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
