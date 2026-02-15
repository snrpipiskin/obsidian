---
noteId: 1770362663695
related:
  - "[[30 Interests/31 Programming/Go/База для собесов/Темы к собесам/Каналы]]"
  - "[[30 Interests/31 Programming/Go/База для собесов/Темы к собесам/Горутина]]"
---
Напиши merge каналов

---

```go
func merge[T any](channels ...<-chan T) <-chan T {
    out := make(chan T)
    var wg sync.WaitGroup

    for _, ch := range channels {
        wg.Add(1)
        go func(c <-chan T) {
            defer wg.Done()
            for v := range c {
                out <- v
            }
        }(ch)
    }

    go func() {
        wg.Wait()
        close(out)
    }()

    return out
}
```
