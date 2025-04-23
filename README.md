# Moonshot AI Java Client

This project provides a Java client for the Moonshot AI API. It is based on the Spring AI project's Moonshot integration and has been extracted to be used as a standalone library.

## Overview

The Moonshot AI Java Client is organized as a multi-module Maven project:

- `moonshot-parent`: The parent POM with dependency management
- `moonshot-core`: The core implementation of the Moonshot AI client

## Features

- Complete implementation of the Moonshot API
- Support for chat completions
- Support for streaming responses
- Function calling capability
- Retry mechanism for API calls
- Observation and metrics support via Micrometer

## Requirements

- Java 17 or higher
- Maven 3.6.3 or higher

## Building from Source

To build the project from source, run:

```bash
./mvnw clean install
```

## Usage

Add the following dependency to your project:

```xml
<dependency>
    <groupId>org.springframework.ai.moonshot</groupId>
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