# 🧠 Engenharia de Prompts Avançada e Ancoragem de Contexto no NotebookLM

## 📝 Contexto e Objetivos

Este projeto prático, desenvolvido para a plataforma DIO, simula a atuação de um **Engenheiro de IA/Especialista em Prompting**. O objetivo é transformar o Google NotebookLM em um motor de aprendizagem ativa de alta fidelidade, mitigando alucinações por meio de técnicas avançadas de ancoragem (*grounding*) e injeção de contexto estruturado.

### Objetivos Estratégicos:
* **Sistematizar o Conhecimento:** Criar um ambiente de estudo controlado utilizando LLMs baseados em recuperação de contexto (RAG - *Retrieval-Augmented Generation*).
* **Otimizar a Relação Sinal-Ruído:** Desenvolver prompts de alta densidade de informação para extrair análises sintéticas e precisas das fontes primárias.
* **Mapeamento de Falhas (Cicatrizes):** Documentar o comportamento do modelo diante de instruções ambíguas e registrar o refinamento técnico dos prompts.

---

## 📚 Curadoria de Fontes de Alta Autoridade

Para garantir a qualidade técnica das respostas, o NotebookLM foi alimentado com a base teórica e prática que define o estado da arte em Engenharia de Prompts:

1. **Guia de Engenharia de Prompts da DAIR.AI (Elvis Saravia):** Repositório de referência global que mapeia técnicas desde o *Zero-Shot* até o *Directional Stimulus Prompting*. [Acessar Fonte](https://github.com)
2. **Práticas Recomendadas de Engenharia de Prompts (OpenAI):** Documentação oficial detalhando estratégias de decomposição de tarefas complexas e uso de delimitadores. [Acessar Fonte](https://openai.com)
3. **Artigo Base: "Chain-of-Thought Prompting Elicits Reasoning in Large Language Models" (Wei et al., Google Research):** O paper científico pioneiro que introduziu a técnica de cadeias de pensamento para o despertar do raciocínio lógico em LLMs. [Acessar arXiv](https://arxiv.org)

---

## 🛠️ Engenharia de Prompts e "Cicatrizes" (Troubleshooting Avançado)

Abaixo está o registro técnico do processo de iteração e refinamento das instruções fornecidas à IA.

### ❌ Iteração 1: Abordagem Ingênua (*Naive Prompting*)
* **Prompt Executado:** *"Explique a diferença entre poucas amostras (Few-Shot) e pensamento em cadeia (Chain of Thought) de acordo com os textos."*
* **Comportamento do Modelo (Falha):** A IA gerou uma resposta puramente conceitual e abstrata. Embora correta, ela falhou em extrair a sintaxe exata e os exemplos matemáticos contidos no PDF de Wei et al. O modelo utilizou seu conhecimento prévio geral em vez de se ancorar estritamente nas fontes.
* **Diagnóstico Técnico:** Falta de atribuição de papel (*Role-Play*), ausência de delimitadores e falta de restrição de escopo.

### 🎯 Iteração 2: Prompt Avançado com Ancoragem Estrita (*Grounding & System Persona*)
* **Prompt Executado:**
  > `[PERSONA]` Atue como um Principal AI Engineer e Professor Adjunto de Ciência da Computação.
  > `[CONTEXTO]` Analise rigorosamente os documentos carregados no seu contexto atual, priorizando o paper de Wei et al.
  > `[TAREFA]` Contraste a mecânica operacional de 'Few-Shot Prompting' versus 'Chain-of-Thought (CoT) Prompting'.
  > `[RESTRICÕES]` 
  > 1. Sua resposta deve ser dividida estritamente em três seções: Mecânica de Atuação, Impacto na Taxa de Erro e Exemplo Sintático Computacional.
  > 2. Proíba o uso de conhecimento externo ao notebook. Se a informação não estiver nas fontes, responda "Dados insuficientes no contexto fornecido".
  > 3. Use citações diretas em formato Markdown para embasar as afirmações.
* **Resultado Obtido (Sucesso):** O NotebookLM isolou o conhecimento externo. Ele gerou uma tabela comparativa exata, extraiu os exemplos de problemas matemáticos do paper (ex: o problema das maçãs) e citou as seções específicas do PDF. As alucinações foram reduzidas a zero.

---

## 📖 Miniguia de Estudo (Consolidação de Conhecimento)

### 1. Resumo Estruturado: Arquitetura de Instruções
A Engenharia de Prompts em ambientes baseados em RAG (como o NotebookLM) exige o entendimento de que a IA não está criando conhecimento, mas **filtrando e sintetizando** vetores de contexto. O sucesso da extração depende de três variáveis fundamentais:
* **Delimitação de Escopo:** Instruir explicitamente o modelo a ignorar o conhecimento geral da internet.
* **Estruturação de Saída:** Forçar formatos rígidos (JSON, Markdown, tabelas) para evitar prolixidade.
* **Metacognição Induzida:** Exigir que a IA explique o porquê chegou àquela conclusão antes de entregar o resultado.

### 2. Glossário Técnico Base
* **In-Context Learning (Aprendizado em Contexto):** A capacidade do modelo de aprender uma nova tarefa temporariamente, apenas processando os exemplos fornecidos no prompt, sem alterar seus pesos neurais.
* **Chain-of-Thought (CoT):** Técnica de decomposição onde o modelo gera uma sequência de passos intermediários de raciocínio antes de emitir o token de resposta final.
* **Grounding (Ancoragem):** O processo de vincular as respostas da IA a uma base de dados real, verificável e estática (as fontes do seu NotebookLM).
* **Token Budget (Orçamento de Tokens):** A gestão do limite de leitura/escrita do modelo. Prompts prolixos gastam contexto útil desnecessariamente.

### 3. Framework de Prompts Reutilizáveis (Templates de Elite)

#### Engenharia Reversa de Conceitos Complexos
```text
[CONTEXTO] Baseando-se estritamente nas fontes fornecidas.
[TAREFA] Decomponha o conceito de [INSERIR CONCEITO] utilizando a técnica Feynman.
[FORMATO] 1. Explicação para uma criança de 10 anos; 2. Análise técnica de nível sênior; 3. Analogia com o mundo físico; 4. Mapeamento de possíveis equívocos comuns sobre o tema.
```

#### Simulador de Exames com Feedback Iterativo
```text
Atue como um examinador de certificação técnica. Com base nos PDFs anexados, gere uma única pergunta complexa de múltipla escolha (A a D) sobre [TÓPICO SPECÍFICO]. Não forneça a resposta ainda. Aguarde a minha resposta para avaliar e, em seguida, forneça uma justificativa detalhada baseada nas páginas do documento.
```

---
*Este repositório foi estruturado seguindo as melhores práticas de documentação técnica para engenharia de software e IA. Desenvolvido para a comunidade [DIO](https://dio.me).*
