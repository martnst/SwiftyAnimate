# SwiftyAnimate
Swift animation

## Installation

### Cocoapods
```ruby
pod 'SwiftyAnimate'
```

## Escape the Pyramid of Doom!

```swift
// This!
Animate(duration: time) {
    // animation
}.do { [unowned self] in
    // non-animation function
    self.function {}
}.then(duration: time) {
    // animation
}.wait { [unowned self] resume in
    // function that takes time
    self.function {
        resume()
    }
}.then(duration: time) {
    // animation
}.then(duration: time) {
    // animation
}.perform()


// Not this!
UIView.animate(withDuration: time, animations: { 
    // animation
}) { success in
    // non-animation function
    self.function {}
    UIView.animate(withDuration: time, animations: {
        // animation
    }) { [unowned self]  success in
        // function that takes time
        self.function {
            UIView.animate(withDuration: time, animations: {
                // animation
            }) { success in
                UIView.animate(withDuration: time, animations: {
                    // animation
                })
            }
        }
    }
}
```