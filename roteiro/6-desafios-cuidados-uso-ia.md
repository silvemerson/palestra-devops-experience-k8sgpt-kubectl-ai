# 5 Desafios e Cuidados no Uso de IA

- Custo Computacional Local
Rodar LLMs com o Ollama exige máquinas potentes, com CPU e GPU compatíveis.
Apesar de evitar custos de API externos (como OpenAI ou Anthropic), há aumento no uso de energia local e consumo de recursos físicos — o que pode ser um gargalo em ambientes compartilhados ou de baixo orçamento.

- Latência em Tempo Real
Modelos LLM locais, especialmente os maiores, podem ter tempo de resposta mais lento dependendo do hardware.
Isso impacta aplicações que precisam de respostas rápidas, como alertas em pipelines CI/CD ou análise de falhas em produção. Testes de performance são fundamentais antes da integração.

- Privacidade ≠ Segurança Absoluta
Apesar do Ollama rodar offline e proteger melhor a privacidade, ele não elimina riscos como vazamento de dados sensíveis por meio de logs, prompts mal formatados ou más práticas no manuseio de informações.
É essencial seguir boas práticas de prompt engineering e gestão segura de contexto.

- Alucinações com Confiança
Mesmo offline, modelos LLMs podem “alucinar”: dar respostas incorretas com alta confiança.
No contexto DevOps, isso pode significar um diagnóstico errado de um incidente, ou um YAML malformado. Por isso, é importante ter curadoria humana e mecanismos de verificação por trás da IA.