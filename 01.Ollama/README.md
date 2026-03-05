## Ollama:
Ollama is a tool that allows you to run Large Language Models (LLMs) locally on your own computer or server. This means you can use AI models without relying on cloud APIs or an internet connection after installation.

Ollama হলো একটি টুল যা আপনার নিজের কম্পিউটার (লোকাল মেশিন)-এ Large Language Model (LLM) চালাতে সাহায্য করে। অর্থাৎ, আপনি ইন্টারনেট বা ক্লাউড API ছাড়াই লোকালভাবে AI মডেল রান করতে পারেন।


### Key Features

- Run LLMs locally – No cloud dependency.
- Simple installation and usage – Run models with a single command.
- Supports multiple open-source models, such as:
    - gpt-oss 
    - Gemma 3
    - DeepSeek-R1
    - Qwen3 and more
- Built-in REST API – Easily integrate with applications.
- Model customization (Modelfile) – Create custom system prompts and configurations.






## Ollama Installation:

_Install Required Packages:_
```
dnf install -y curl tar zstd git 
```


_To install Ollama, run the following command:_
```
curl -fsSL https://ollama.com/install.sh | sh
```


```
### Output: 

>>> Cleaning up old version at /usr/local/lib/ollama
>>> Installing ollama to /usr/local
>>> Downloading ollama-linux-amd64.tar.zst
######################################################################## 100.0%
>>> Creating ollama user...
>>> Adding ollama user to render group...
>>> Adding ollama user to video group...
>>> Adding current user to ollama group...
>>> Creating ollama systemd service...
>>> Enabling and starting ollama service...
Created symlink /etc/systemd/system/default.target.wants/ollama.service → /etc/systemd/system/ollama.service.
>>> The Ollama API is now available at 127.0.0.1:11434.
>>> Install complete. Run "ollama" from the command line.
WARNING: No NVIDIA/AMD GPU detected. Ollama will run in CPU-only mode.
```



### Verify: 

_Check Ollama version:_
```
ollama --version

ollama version is 0.17.4
```


_List available models:_
```
ollama list

NAME    ID    SIZE    MODIFIED
```



### Pull Models: 

If no models are installed yet, it will be empty. You can download models like `gpt-oss:20b`:

```
ollama pull gpt-oss:20b
```


```
ollama ls

NAME           ID              SIZE     MODIFIED
gpt-oss:20b    17052f91a42e    13 GB    18 seconds ago
```



> [!NOTE]
> If your system has only **8GB RAM**, large models like `gpt-oss:20b` may fail to load due to memory limits.



## Claude Code Installation:

Claude Code is Anthropic’s agentic coding tool that can read, modify, and execute code in your working directory.

Open models can be used with Claude Code through Ollama’s Anthropic-compatible API, enabling you to use models such as `glm-4.7`, `qwen3-coder`, `gpt-oss`.


_Install Claude Code:_
```
curl -fsSL https://claude.ai/install.sh | bash
```


_Verify:_
```
ll ~/.local/bin/claude
```


_Add to PATH:_
```
echo 'export PATH="$HOME/.local/bin:$PATH"' >> ~/.bashrc && source ~/.bashrc
```



### Using Claude Code with Ollama:

```
ollama launch claude

ollama launch claude --model gpt-oss:20b
```



### Example Prompt:

```
create an engineering portfolio with nodejs
```


_If you want better results, try:_
```
Create a full-stack engineering portfolio project using Node.js, Express, and MongoDB.
Include:
- REST API
- Authentication
- Project showcase section
- Dockerfile
- Deployment instructions
```



### Test the REST API: 

By default, Ollama runs on: `http://localhost:11434` 


_Example API request:_
```
curl http://127.0.0.1:11434/api/generate -d '{
  "model": "llama3",
  "prompt": "Explain Docker in simple terms"
}'
```




### License:
This project is licensed under the MIT License.






### Ref: 
- [Ollama Doc](https://docs.ollama.com/linux)
- [Ollama Models](https://ollama.com/search)
- [gpt-oss](https://ollama.com/library/gpt-oss)
- [Claude Code](https://docs.ollama.com/integrations/claude-code)
- [Open WebUI](https://docs.openwebui.com/)



