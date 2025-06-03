# Moonshot AI Java Client

This project provides a Java client for the Moonshot AI API. It is based on the Spring AI project's Moonshot integration and has been extracted to be used as a standalone library.

## Overview

The Moonshot AI Java Client is organized as a multi-module Maven project:

- `moonshot-parent`: The parent POM with dependency management
- `moonshot-core`: The core implementation of the Moonshot AI client
- `docs`: Documentation module built with Antora

## Features

- **Chat Models**: Comprehensive implementation of the Moonshot Chat API supporting models like `moonshot-v1-8k`, `moonshot-v1-32k`, and `moonshot-v1-128k`
- **Flexible Configuration**: Extensive customization options including temperature, max tokens, top-p sampling, and more
- **Streaming Responses**: Support for token-by-token streaming responses for interactive applications
- **Function Calling**: Register custom Java functions that Moonshot models can intelligently invoke with appropriate arguments
- **Robust Error Handling**: Built-in retry mechanism with configurable exponential backoff for handling transient errors
- **Observability**: Integration with Micrometer for metrics collection and performance monitoring
- **Type Safety**: Fully typed API that provides compile-time safety and excellent IDE support

## Requirements

- Java 17 or higher
- Maven 3.6.3 or higher

## Building from Source

To build the project from source, run:

```bash
./mvnw clean install
```

### Building the Documentation

To build the documentation locally:

```bash
cd docs
../mvnw antora:antora
```

The generated documentation will be available at `docs/target/antora/site/`.

## Usage

Add the following dependency to your project:

```xml
<dependency>
    <groupId>org.springaicommunity</groupId>
    <artifactId>moonshot-core</artifactId>
    <version>0.1.0-SNAPSHOT</version>
</dependency>
```

## Example

```java
// Create the Moonshot API client
MoonshotApi moonshotApi = new MoonshotApi("your-api-key");

// Create the chat model
MoonshotChatModel chatModel = new MoonshotChatModel(moonshotApi);

// Create a prompt
UserMessage userMessage = new UserMessage("Tell me a joke about programming");
Prompt prompt = new Prompt(List.of(userMessage));

// Get the response
ChatResponse response = chatModel.call(prompt);
String content = response.getResult().getOutput().getContent();
System.out.println(content);
```

## License

This project is licensed under the [Apache License 2.0](LICENSE).