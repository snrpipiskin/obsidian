---
noteId: 1772782720412
related:
  - "[[Obsidian Sync/30 Interests 1/31 Programming/Go/База для собесов/Темы к собесам/Строки|Строки]]"
---
Как преобразовать строку в число в Go?

---

В Go для этого используется пакет `strconv`.

### 1. В целое число (int)
Самый простой способ:
```go
i, err := strconv.Atoi("123")
```

Или через `ParseInt` (для указания битности):
```go
i, err := strconv.ParseInt("123", 10, 64)
```

### 2. В число с плавающей точкой (float64)
```go
f, err := strconv.ParseFloat("123.45", 64)
```

