## GitHub Models extension

Use the GitHub Models service from the CLI!

## Using

### Prerequisites

The extension requires the [`gh` CLI](https://cli.github.com/) to be installed and in the `PATH`. The extension also requires the user have authenticated via `gh auth`.

### Installing

After installing the `gh` CLI, from a command-line run:
```shell
gh extension install https://github.com/github/gh-models
```

#### Upgrading

If you've previously installed the `gh models` extension and want to update to the latest version, you can run this command:

```sh
gh extension upgrade github/gh-models
```


### Examples

#### Listing models

```shell
gh models list
```

Example output:
```shell
ID                              DISPLAY NAME
ai21-labs/ai21-jamba-1.5-large  AI21 Jamba 1.5 Large
openai/gpt-4.1                  OpenAI GPT-4.1
openai/gpt-4o-mini              OpenAI GPT-4o mini
cohere/cohere-command-r         Cohere Command R
deepseek/deepseek-v3-0324       Deepseek-V3-0324
```

Use the value in the "ID" column when specifying the model on the command-line.

#### Running inference

##### REPL mode

Run the extension in REPL mode. This will prompt you for which model to use.
```shell
gh models run
```

In REPL mode, use `/help` to list available commands. Otherwise just type your prompt and hit ENTER to send to the model.

##### Single-shot mode

Run the extension in single-shot mode. This will print the model output and exit.
```shell
gh models run openai/gpt-4o-mini "why is the sky blue?"
```

Run the extension with output from a command. This uses single-shot mode.
```shell
cat README.md | gh models run openai/gpt-4o-mini "summarize this text"
```

#### Evaluating prompts

Run evaluation tests against a model using a `.prompt.yml` file:
```shell
gh models eval my_prompt.prompt.yml
```

The evaluation will run test cases defined in the prompt file and display results in a human-readable format. For programmatic use, you can output results in JSON format:
```shell
gh models eval my_prompt.prompt.yml --json
```

The JSON output includes detailed test results, evaluation scores, and summary statistics that can be processed by other tools or CI/CD pipelines.

Here's a sample GitHub Action that uses the `eval` command to automatically run the evals in any PR that updates a prompt file: [evals_action.yml](/examples/evals_action.yml).

Learn more about `.prompt.yml` files here: [Storing prompts in GitHub repositories](https://docs.github.com/github-models/use-github-models/storing-prompts-in-github-repositories).

## Notice

Remember when interacting with a model you are experimenting with AI, so content mistakes are possible. The feature is
subject to various limits (including requests per minute, requests per day, tokens per request, and concurrent requests)
and is not designed for production use cases. GitHub Models uses
[Azure AI Content Safety](https://azure.microsoft.com/products/ai-services/ai-content-safety). These filters
cannot be turned off as part of the GitHub Models experience. If you decide to employ models through a paid service,
please configure your content filters to meet your requirements. This service is under
[GitHub's Pre-release Terms](https://docs.github.com/site-policy/github-terms/github-pre-release-license-terms). Your
use of the GitHub Models is subject to the following
[Product Terms](https://www.microsoft.com/licensing/terms/productoffering/MicrosoftAzure/allprograms) and
[Privacy Statement](https://www.microsoft.com/licensing/terms/product/PrivacyandSecurityTerms/MCA). Content within this
Repository may be subject to additional license terms.

