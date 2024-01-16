# Microsoft AutoGen on Windows: A User's Journey

[Back to home](index.md)

Hello there! Recently, I stumbled upon [this fascinating video](https://www.youtube.com/watch?v=V2qZ_lgxTzg&t=14s) showcasing Microsoft AutoGen on Windows, and I must say, it piqued my interest instantly. It seemed almost too good to be true! Eager to explore, I embarked on my journey to set it up. Naturally, there were a few hiccups along the way, but nothing that couldn’t be resolved with a bit of patience and problem-solving.

## Getting Started

To begin, I focused on configuring my development environment on my PC. Here's a quick overview:

1. **Initiating a Git Repository**: The first step is setting up version control using Git. This involves initializing your local directory with the `git init` command and establishing a remote repository for code backup. I alternate between GitLab and GitHub, depending on the project. If you're new to Git, I recommend starting with this [installation guide](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git) and this [introductory section](https://git-scm.com/book/en/v2/Getting-Started-What-is-Git%3F) for a comprehensive understanding.
2. **Setting Up a Conda Environment**: For each new project, it's prudent to create a dedicated virtual environment. This can be done using `venv` included in your Python distribution, or through `conda`, which is my preferred tool. I use Miniconda for its simplicity and efficiency. Check out [this guide](https://docs.conda.io/projects/miniconda/en/latest/) for a quick setup.
3. **Using a Starter Example**: I began by tweaking [this example notebook](https://github.com/microsoft/autogen/blob/main/notebook/agentchat_auto_feedback_from_code_execution.ipynb) from Microsoft AutoGen. It's a tested and reliable starting point for newcomers to the platform.

Navigating new technologies always comes with a learning curve. Here's how I tackled some challenges along the way.

## Overcoming Challenges

### `config_list` Setup

The creation of the `config_list` configuration was not immediately obvious. This is done deliberately as the Autogen developers guide you to obviscate your API-key, and not check it into your repo directly. Detailed in the [config_list example notebook](https://github.com/microsoft/autogen/blob/main/notebook/oai_openai_utils.ipynb), it involves setting up an environment variable or a .json file which are referenced by the AutoGen package. This configuration is crucial for securely integrating your OpenAI API key, and credit is due to the thoughtful and security-conscious design by the AutoGen team.

### Code Execution Hurdles

An unexpected error occurred during code execution: `EXECUTING CODE BLOCK 0 (inferred language is sh)...`. Surprisingly, this was related to PowerShell incompatibility issue on Windows, a quirk I found rather amusing.

**The Solution**: Enable Docker for code execution. This involves configuring the UserProxyAgent (which is the agent which executes the produced code on your behalf) as follows:

```python
user_proxy = UserProxyAgent(
    ...
    code_execution_config={
        "use_docker": True,
    },
)
```

The essential step here is `"use_docker": True`.

> ***Note:*** keep an eye on the images that docker uses. It seems there is an tendancy to download, or create, an image everytime code is run

### Docker Permission Issues

A minor yet crucial step was updating Docker to the latest version (24.x.x at the time of writing) and enabling cross-platform compatibility between Windows and WSL (Windows Subsystem Linux), as discussed in [this helpful StackOverflow post](https://stackoverflow.com/questions/63497928/ubuntu-wsl-with-docker-could-not-be-found).

## Wrapping Up

After navigating through these setup steps and resolving the challenges, I successfully executed the program and achieved the desired results with GenAI.

I hope this guide assists you in your AutoGen journey. Whether your experience mirrors mine or diverges, I'd love to hear about it. Feel free to share your thoughts and feedback in the comments!

[Back to home](index.md)