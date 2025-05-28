### Instalação K8s com KIND

Use esse tutorial para ter um cluster KIND: [KIND + MetalLB + Nginx + NFS
](https://github.com/silvemerson/kind-infra-lab)


## Instalção ollama

https://ollama.com/download/linux

```bash
curl -fsSL https://ollama.com/install.sh | bash
```
## Validando versão:


```bash

ollama --version

```

## Ajusta para a aplicação ser acessível publicamente:

```bash

# /etc/systemd/system/ollama.service

[Unit]
Description=Ollama Service
After=network-online.target

[Service]
ExecStart=/usr/local/bin/ollama serve
User=ollama
Group=ollama
Restart=always
RestartSec=3
Environment="PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games:/snap/bin"
Environment="OLLAMA_HOST=0.0.0.0"

[Install]
WantedBy=default.target

```

## Baixando e executando llama2

```
ollama run llama2
```
## Definindo variáveis de ambiente:

```bash
export OPENAI_ENDPOINT="http://localhost:11434/v1"  # URL do Ollama
export OPENAI_DEPLOYMENT_NAME="llama2"  # Modelo que você está usando
export OPENAI_API_KEY="dummytoken"  # Token fictício (não é validado no Ollama)

```

## Inicializando UI

```bash
docker run -d -p 3000:8080 -v open-webui:/app/backend/data -e OLLAMA_BASE_URL=http://192.168.1.100:11434 -e OPENAI_ENDPOINT="http://localhost:11434/v1" -e OPENAI_DEPLOYMENT_NAME="codellama" -e OPENAI_API_KEY="dummytoken" --name open-webui --restart always ghcr.io/open-webui/open-webui:main
```


## Instalação e Configuração do k8sgpt

```bash
curl -LO https://github.com/k8sgpt-ai/k8sgpt/releases/download/v0.4.13/k8sgpt_amd64.deb
sudo dpkg -i k8sgpt_amd64.deb
```

```bash

k8sgpt auth add \                                            
  -n ollama \
  -b ollama \
  -u http://192.168.1.100:11434 \
  -m llama2


```
Edite `~/.config/k8sgpt/k8sgpt.yaml`

E troca isso:

```bash
defaultprovider: ""

```
Por isso:

```bash
defaultprovider: ollama
```

## kubectl ai

## Instalação

```bash
git clone https://github.com/sozercan/kubectl-ai.git
cd kubectl-ai
go build -o kubectl-ai
sudo mv kubectl-ai /usr/local/bin/

kubectl ai help
```


## Definindo variáveis de ambiente:

```bash
export OPENAI_ENDPOINT="http://192.168.1.100:11434"  # URL do Ollama
export OPENAI_DEPLOYMENT_NAME="llama2"  # Modelo que você está usando
export OPENAI_API_KEY="dummytoken"  # Token fictício (não é validado no Ollama)
