
# Debouncing and Throttling in JavaScript

Debouncing and throttling are two techniques used in JavaScript (and in programming more broadly) to control the rate at which a function is executed. This is particularly useful for optimizing performance and improving user experience, especially in situations where some code should not run too often. This can include resizing windows, scrolling, keypress actions in search inputs, etc.

## Debouncing

Debouncing ensures that a function does not get called again until a certain amount of time has passed without it being called. Essentially, every time the debounced function is invoked, the timer gets reset. The function will only be called after the timer expires.

This is useful when you want to ensure that the function is not called too frequently. For instance, consider a search input that fetches results from an API as the user types. You wouldn't want to make an API call on every keystroke, so you debounce the function to make a call only when the user has stopped typing for a certain period.

### Example of Debouncing:

```javascript
function debounce(func, delay) {
  let timer;
  return function() {
    const context = this;
    const args = arguments;
    clearTimeout(timer);
    timer = setTimeout(() => func.apply(context, args), delay);
  };
} 

// Usage
const debouncedFunction = debounce(() => console.log('Debounced!'), 2000);



```
  
## Throttling

Throttling ensures that a function is called at most once in a specified time period. This means, once the function is called, it won’t be called again until the specified time has passed.

This is useful for functions that you want to allow to run, but not too often. For example, handling scroll events, you might want to check the scroll position, but doing so on every scroll event can be a performance issue. Throttling the function allows you to check the position, say, every 100 milliseconds, regardless of how many scroll events occur.

```function throttle(func, limit) {
  let inThrottle;
  return function() {
    const args = arguments;
    const context = this;
    if (!inThrottle) {
      func.apply(context, args);
      inThrottle = true;
      setTimeout(() => inThrottle = false, limit);
    }
  };
}

// Usage
const throttledFunction = throttle(() => console.log('Throttled!'), 2000);
```

Key Differences
Timing: Debouncing is based on the pause in the events, whereas throttling is based on a fixed amount of time.
Use Cases: Debouncing is ideal for tasks that should only happen after a delay in activity (like typing in a search bar), while throttling is ideal for controlling how often a function can be executed in a given period (like handling scroll or resize events).
