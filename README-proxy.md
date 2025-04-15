# Watson AI OpenAI Proxy

This is a simple proxy server that allows you to use IBM Watson Code Assistant as an OpenAI-compatible API. It can be used with any tool that supports the OpenAI API, such as LangChain, OpenAI Python library, OpenWebUI or any other tool that supports the OpenAI API.

## Prerequisites

- Python 3.6 or higher
- An IBM Watson Code Assistant API key

## Installation

1. Clone this repository: `git clone https://github.com/sshnaidm/watson-ai-openai-proxy.git`
2. Install the required Python packages: `pip install -r proxy-requirements.txt`
3. Set your IBM Watson Code Assistant API key as an environment variable: `export IAM_APIKEY=your_api_key`

Default model name is `watson-ai`.

## Usage

1. Export your IBM Watson Code Assistant API key as an environment variable: `export IAM_APIKEY=your_api_key`
2. Run the proxy server: `python watson_openai_proxy.py`
   a. If you want to change host or port, use `flask` command:  `flask --app watson_openai_proxy run --host=0.0.0.0 --port=5555`
3. Use the proxy server as an OpenAI API endpoint. For example, in LangChain: `llm = ChatOpenAI(base_url="http://localhost:5000/v1", model="watson-ai", api_key="111")`
4. Use API of this proxy server in OpenWebUI as `http://localhost:5000/v1`
