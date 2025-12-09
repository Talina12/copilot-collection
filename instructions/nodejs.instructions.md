## Best Practices

- Use proper TypeScript types for all parameters and return values
- Implement comprehensive error handling with try-catch blocks
- Use async/await for all asynchronous operations
- Close database connections and clean up resources properly
- Validate input parameters before processing
- Use structured logging for debugging without polluting stdout/stderr
- Consider security implications when exposing file system or network access
- Implement proper resource cleanup on transport close events
- Use environment variables for configuration (ports, API keys, etc.)
- Document tool capabilities and limitations clearly
- Test with multiple clients to ensure compatibility

### Event Loop Best Practices

- **Don't block the event loop**: Avoid CPU-intensive synchronous operations
- **Use asynchronous APIs**: Prefer async methods (e.g., `fs.readFile` over `fs.readFileSync`)
- **Offload heavy computations**: Use Worker Threads or child processes for CPU-intensive tasks
- **Be careful with RegEx**: Avoid complex regular expressions that can cause catastrophic backtracking (use tools like safe-regex to check)
- **Stream large data**: Use streaming APIs instead of loading large files/data into memory
- **Partition large tasks**: Break up large arrays/loops and process in chunks using `setImmediate()` to yield control back to the event loop
- **Avoid large JSON operations**: Use streaming JSON parsers for large payloads; be cautious with `JSON.parse()` and `JSON.stringify()` on large objects
- **Consider algorithm complexity**: Be mindful of O(n²) or worse algorithms, especially with user-controlled input sizes
- **Validate user input**: Sanitize and limit user-provided data that affects processing time (regex patterns, array sizes, etc.)
- **Monitor event loop lag**: Use tools like `perf_hooks` to detect when the event loop is blocked
- **Use async crypto methods**: Prefer `crypto.pbkdf2()` over `crypto.pbkdf2Sync()` and similar async alternatives
