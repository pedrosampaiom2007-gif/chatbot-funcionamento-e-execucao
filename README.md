#  Charge Grid Intelligence — CGI Assistant

> Assistente conversacional com IA para gestão de eletropostos em postos comerciais e frotas  
> EV Challenge 2026 — GoodWe / FIAP

---

##  Equipe

| Nome | RM |
|------|----|
| Luan de Araujo Carneiro | RM 573691 |
| Pedro Sampaio Mochnacs Arruda | RM 573522 |
| Raul Sampaio Mochnacs Arruda | RM 573523 |
| Lucas Garcia de Britto | RM 571768 |
| Kevin Rodrigues de Melo | RM 571777 |

---

##  Problema Abordado

A expansão dos veículos elétricos em operações comerciais expõe dois problemas centrais:

- **Ausência de orquestração de potência:** sem controle inteligente, o uso simultâneo de múltiplos carregadores sobrecarrega a infraestrutura elétrica do posto, gerando custos elevados e risco de interrupção do serviço.
- **Falta de visibilidade operacional:** sem monitoramento em tempo real, operadores não conseguem otimizar a disponibilidade dos carregadores, prever picos de demanda ou identificar falhas com agilidade.

---

##  Diferencial Competitivo

Diferente de dashboards tradicionais, o Charge Grid Intelligence permite acesso direto aos dados via linguagem natural. Gestores e operadores obtêm respostas precisas sem precisar interpretar gráficos ou relatórios complexos.

---

##  Estrutura do Repositório
charge-grid-intelligence/
├── ChargeGrid_Intelligence_Sprint2.ipynb   # Notebook principal (Sprint 2)
├── README.md                               # Este arquivo
└── resultados_testes_sprint2.json          # Gerado automaticamente ao rodar a Célula 4

---

##  Tecnologias Utilizadas

| Tecnologia | Função | Justificativa |
|------------|--------|---------------|
| **Ollama** (`llama3.2:3b`) | Modelo de linguagem | Gratuito, open source, sem API Key ou custo por token |
| **RAG** (busca por palavras-chave) | Injeção de dados contextuais | Garante respostas baseadas em dados reais do sistema |
| **ipywidgets** | Interface interativa | Interface demonstrável no Colab sem dependências externas |
| **Python** | Linguagem principal | Compatibilidade com Ollama e ecossistema de IA |

---

##  Como Executar

### Google Colab (recomendado)

1. Abra o arquivo `ChargeGrid_Intelligence_Sprint2.ipynb` no Google Colab
2. Execute as células **em ordem**: Célula 1 → 2 → 3 → 4
3. A Célula 1 instala o Ollama e baixa o modelo automaticamente (~2 GB, aguarde)
4. A Célula 3 abre a interface de chat
5. A Célula 4 executa os casos de teste e pede sua avaliação qualitativa

### Execução Local

```bash
# 1. Instalar o Ollama: https://ollama.com
# 2. Baixar o modelo
ollama pull llama3.2:3b

# 3. Instalar dependência Python
pip install ollama

# 4. Abrir o notebook na IDE de preferência
jupyter notebook ChargeGrid_Intelligence_Sprint2.ipynb
```

---

##  Dependências
ollama
ipywidgets

> Nenhuma API Key necessária. O Ollama roda o modelo localmente.

---

## 🏗️ Arquitetura do Chatbot
Pergunta do usuário
↓
buscar_contexto()  ← RAG: busca documentos relevantes por palavras-chave
↓
Contexto + Pergunta + Histórico
↓
ollama.chat(llama3.2:3b)
↓
Resposta em português, dentro do escopo

**Técnicas implementadas:**
- ✅ System prompt estruturado em 5 blocos
- ✅ RAG com base de conhecimento local (12 documentos)
- ✅ Histórico de mensagens persistente por sessão
- ✅ Interface interativa via ipywidgets

---

## 💬 Exemplos de Uso
👤 Você: Qual carregador gerou mais receita este mês?
🤖 Bot:  O carregador CP-03 foi o destaque do mês, com 312 kWh fornecidos
e um faturamento de R$ 280,80.
👤 Você: Qual o melhor carro elétrico para comprar?
🤖 Bot:  Só consigo ajudar com questões relacionadas ao Charge Grid Intelligence
e à operação dos eletropostos. Posso te ajudar com algo nessa área?

---

##  Casos de Teste — Sprint 1

| # | Pergunta | Escopo | Resposta Esperada | Avaliação |
|---|----------|--------|-------------------|-----------|
| 1 | Qual carregador gerou mais receita este mês? | Dentro | Identifica CP-03 com R$ 280,80 e 312 kWh | [Adequada] |
| 2 | Quantas sessões de recarga foram realizadas hoje? | Dentro | Retorna 47 sessões das 06h às 22h30 | [Adequada] |
| 3 | Como é feita a cobrança dos usuários no posto? | Dentro | Explica cobrança por kWh ou por tempo de sessão | [Adequadar] |
| 4 | Qual o prazo de retorno do investimento na instalação dos eletropostos? | Dentro | Explica ticket médio, volume de sessões e tarifa | [Adequada] |
| 5 | Quantos carregadores eu precisaria instalar para um posto com alto fluxo? | Dentro | 3 carregadores de 22 kW para cada 50 veículos/dia | [Adequada ] |
| 6 | Qual o melhor carro elétrico para comprar? | Fora | Redireciona para o escopo do sistema | [Adequada] |
| 7 | Tem algum restaurante perto do posto? | Fora | Redireciona educadamente | [Adequada] |

> Resultados completos com respostas obtidas disponíveis em `resultados_testes_sprint2.json`

---

##  Vídeo de Demonstração

[preencher com link do YouTube]

---

> Projeto desenvolvido para o EV Challenge 2026 — FIAP  
> Matéria: Prompt and Artificial Intelligence
