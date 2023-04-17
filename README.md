# combine-kitchen-sink

https://theswiftdev.com/the-ultimate-combine-framework-tutorial-in-swift/

## By using operators you can chain a bunch of publishers together, this gives us that nice declarative syntax

```swift
private var cancellable: AnyCancellable?
//...
self.cancellable = URLSession.shared.dataTaskPublisher(for: url)
.map { $0.data }
.decode(type: [Post].self, decoder: JSONDecoder())
.replaceError(with: [])
.eraseToAnyPublisher()
.sink(receiveValue: { posts in
    print(posts.count)
})
//...
self.cancellable?.cancel()
```

Anyway, there are a bunch of goodies that Combine will bring you:

* Simplified asynchronous code - no more callback hells
* Declarative syntax - easier to read and maintain code
* Composable components - composition over inheritance & reusability
* Multi-platform - except on linux, we're good with SwiftNIO's approach
* Cancellation support - it was always an issue with Promises
* Multithreading - you don't have to worry about it (that much)
* Built-in memory management - no more bags to carry on
