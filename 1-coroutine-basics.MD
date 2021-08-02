# Coroutines basics

- A _coroutine_ is an instance of suspendable computation.
- A coroutine is not bound to any particular thread. It may suspend its execution in one thread and resume in another one.

```kotlin
fun main() = runBlocking { // this: CoroutineScope
    launch { // launch a new coroutine and continue
        delay(1000L) // non-blocking delay for 1 second (default time unit is ms)
        println("World!") // print after delay
    }
    println("Hello") // main coroutine continues while a previous one is delayed
}
```

The following result will be:
```
Hello
World!
```

- `launch` is a _coroutine builder_. It launches a new coroutine concurrently with the rest of the code, which continues to work independently. That's why Hello has been printed first.
