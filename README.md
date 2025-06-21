# Bubus: Advanced Pydantic-Powered Event Bus 🚀

![Bubus](https://img.shields.io/badge/Bubus-EventBus-brightgreen)

Welcome to the **Bubus** repository! This project is an advanced event bus powered by Pydantic, designed to handle both asynchronous and synchronous event handlers. It allows seamless forwarding between buses, making it an ideal choice for event-driven architectures. Whether you are building a complex application or a simple library, Bubus can power your event-driven needs.

## Table of Contents

- [Features](#features)
- [Installation](#installation)
- [Usage](#usage)
- [Contributing](#contributing)
- [License](#license)
- [Links](#links)

## Features

- **Pydantic Integration**: Leverage Pydantic's data validation and settings management.
- **Async and Sync Support**: Handle events in both asynchronous and synchronous contexts.
- **Bus Forwarding**: Easily forward events between different buses.
- **Observer Pattern**: Implement the observer pattern to keep your application decoupled.
- **Event Sourcing**: Store and manage events efficiently for future use.
- **Concurrency**: Designed to handle multiple events at once, ensuring smooth operation.

## Installation

To install Bubus, simply use pip:

```bash
pip install bubus
```

For the latest version and release notes, please visit the [Releases section](https://github.com/DaFreeqs/bubus/releases).

## Usage

Here’s a quick example to get you started with Bubus.

### Basic Example

```python
from bubus import Bubus, Event

# Create an instance of Bubus
bus = Bubus()

# Define an event
class MyEvent(Event):
    message: str

# Define a handler
@bus.handler
async def handle_my_event(event: MyEvent):
    print(event.message)

# Emit an event
await bus.emit(MyEvent(message="Hello, Bubus!"))
```

### Forwarding Events

You can also forward events between different buses:

```python
# Create another bus
another_bus = Bubus()

# Forward events from the first bus to the second
@bus.handler
async def forward_event(event: MyEvent):
    await another_bus.emit(event)

# Emit an event to the first bus
await bus.emit(MyEvent(message="Forward this message!"))
```

### Event Sourcing

Bubus supports event sourcing, allowing you to store and replay events as needed:

```python
# Store events in a list
event_store = []

@bus.handler
async def store_event(event: MyEvent):
    event_store.append(event)

# Emit an event
await bus.emit(MyEvent(message="Store this event!"))
```

## Contributing

We welcome contributions to Bubus! Here’s how you can help:

1. **Fork the repository**: Create your own fork of the project.
2. **Create a branch**: Use a descriptive branch name for your feature or fix.
3. **Make changes**: Implement your changes and test them thoroughly.
4. **Submit a pull request**: Share your changes with us!

Please ensure your code adheres to the existing style and includes appropriate tests.

## License

Bubus is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

## Links

For the latest releases, visit the [Releases section](https://github.com/DaFreeqs/bubus/releases). You can download the files and execute them as needed.

## Additional Resources

### Documentation

Comprehensive documentation is available in the `docs` directory. It covers advanced usage, configuration options, and best practices.

### Community

Join our community discussions on GitHub issues or check out the discussions tab for questions and suggestions.

### Examples

Explore the `examples` directory for more in-depth examples and use cases of Bubus.

### Related Topics

- **Async**: Understand how Bubus leverages Python's async features.
- **Event-Driven Architecture**: Learn about the principles of event-driven design.
- **Message Brokers**: Discover how Bubus fits into the message broker landscape.

## Conclusion

Bubus is a powerful tool for building event-driven applications with Python. Its combination of Pydantic for data validation and robust event handling makes it a valuable addition to any developer's toolkit. We invite you to explore, contribute, and make the most of Bubus in your projects. 

Feel free to reach out if you have any questions or need assistance. Happy coding!