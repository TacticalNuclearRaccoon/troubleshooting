## Installations

* pip install -U letta
* pip install llama_index ollama
* pip install llama-index-embeddings ollama

* export OLLAMA_BASE_URL=http://localhost:11434

## Docker command

sudo docker run -v ~/.letta/.persist/pgdata:/var/lib/postresql/data -p 8283:8283 -e OLLAMA_BASE_URL=http://localhost:11434 letta/letta:latest

## then also

* ollama serve
