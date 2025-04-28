# Lilypad Qwen 2.5 Coder 7B

Run [Qwen 2.5 Coder 7B](https://ollama.com/library/qwen2.5-coder) on Lilypad Network.

## Getting Started

> Make sure that you Base64 encode your request.

```sh
export WEB3_PRIVATE_KEY=WEB3_PRIVATE_KEY

lilypad run github.com/Lilypad-Tech/lilypad-qwen2.5-coder-7b:<COMMIT> \
-i request="$(echo -n '{
  "model": "MODEL_NAME:MODEL_VERSION",
  "messages": [{
    "role": "system",
    "content": "you are a helpful AI assistant"
  },
  {
  "role": "user",
  "content": "what is the animal order of the frog?"
  }],
  "stream": false,
  "options": {
    "temperature": 1.0
  }
}' | base64 -w 0)"
```

### Valid Options Parameters and Default Values

- [Ollama Modelfile](https://github.com/ollama/ollama/blob/main/docs/modelfile.md#valid-parameters-and-values)

| Parameter      | Description                                                                                                                                                                                                                                                                                                                                                 | Default |
| -------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------- |
| mirostat       | Enable Mirostat sampling for controlling perplexity. (0 = disabled, 1 = Mirostat, 2 = Mirostat 2.0)                                                                                                                                                                                                                                                         | `0`     |
| mirostat_eta   | Influences how quickly the algorithm responds to feedback from the generated text. A lower learning rate will result in slower adjustments, while a higher learning rate will make the algorithm more responsive.                                                                                                                                           | `0.1`   |
| mirostat_tau   | Controls the balance between coherence and diversity of the output. A lower value will result in more focused and coherent text.                                                                                                                                                                                                                            | `5`     |
| num_ctx        | Sets the size of the context window used to generate the next token.                                                                                                                                                                                                                                                                                        | `2048`  |
| repeat_last_n  | Sets how far back for the model to look back to prevent repetition. (0 = disabled, -1 = num_ctx)                                                                                                                                                                                                                                                            | `64`    |
| repeat_penalty | Sets how strongly to penalize repetitions. A higher value (e.g., 1.5) will penalize repetitions more strongly, while a lower value (e.g., 0.9) will be more lenient.                                                                                                                                                                                        | `1.1`   |
| temperature    | The temperature of the model. Increasing the temperature will make the model answer more creatively.                                                                                                                                                                                                                                                        | `0.8`   |
| seed           | Sets the random number seed to use for generation. Setting this to a specific number will make the model generate the same text for the same prompt.                                                                                                                                                                                                        | `0`     |
| stop           | Sets the stop sequences to use. When this pattern is encountered the LLM will stop generating text and return. Multiple stop patterns may be set by specifying multiple separate stop parameters in a modelfile.                                                                                                                                            |         |
| num_predict    | Maximum number of tokens to predict when generating text. (-1 = infinite generation)                                                                                                                                                                                                                                                                        | `-1`    |
| top_k          | Reduces the probability of generating nonsense. A higher value (e.g. 100) will give more diverse answers, while a lower value (e.g. 10) will be more conservative.                                                                                                                                                                                          | `40`    |
| top_p          | Works together with top-k. A higher value (e.g., 0.95) will lead to more diverse text, while a lower value (e.g., 0.5) will generate more focused and conservative text.                                                                                                                                                                                    | `0.9`   |
| min_p          | Alternative to the top_p, and aims to ensure a balance of quality and variety. The parameter p represents the minimum probability for a token to be considered, relative to the probability of the most likely token. For example, with p=0.05 and the most likely token having a probability of 0.9, logits with a value less than 0.045 are filtered out. | `0.0`   |

## Available Scripts

In the project directory, you can run:

### [`scripts/configure`](scripts/configure)

Configures your module.
Sets the following values in the [`.env` file](.env)

```
MODEL_NAME
MODEL_VERSION
DOCKER_HUB_USERNAME
DOCKER_IMAGE
GITHUB_REPO
```

### [`scripts/build [--major] [--minor] [--patch] [--local]`](scripts/build)

Builds the Docker image and pushes it to Docker Hub.

### `--major`, `--minor`, and `--patch` Flags

Increments the specified version before building the Docker image.

#### `--local` Flag

Loads the built Docker image into the local Docker daemon.

### [`scripts/run`](scripts/run)

Runs your module.

## Learn More

To learn more about Lilypad, check out the [Lilypad documentation](https://docs.lilypad.tech/lilypad).
