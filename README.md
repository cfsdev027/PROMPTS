# Guia de Referência para Criação de PROMPTS e Agentes de IA em Linhas de Produção

# Organização e fluxo de informação
Esta seção descreve a estrutura organizacional, os papéis essenciais e o fluxo end-to-end de valor e informação dentro da Software House. O modelo adota práticas ágeis modernas, com forte inspiração no framework Scrum e nos princípios do *Lean Software Development* (Poppendieck), visando a alta performance, previsibilidade de entrega e otimização de custos operacionais.
## 1. Agentes e Colaboradores Essenciais
Para que o fluxo produtivo seja enxuto e livre de gargalos, os papéis são divididos em quatro pilares macro. Cada agente possui responsabilidades bem delimitadas, evitando sobreposições e retrabalho.
### A. Pilar de Negócios e Captação
 * **Business Development Representative (BDR) / Sales:** Atua na prospecção ativa e qualificação de leads. É o primeiro contato do cliente com a Software House.
 * **Product Owner (PO) / Analista de Negócios:** Transforma a visão de negócio do cliente em um *Product Backlog* priorizado. É o guardião do valor do produto e a ponte principal entre o cliente e o time técnico.
### B. Pilar de Arquitetura e Engenharia de Requisitos
 * **Arquiteto de Software:** Define a stack tecnológica, padrões de projeto (Design Patterns), estrutura de dados e diretrizes de escalabilidade/segurança. Garante que o sistema suporte o crescimento do negócio sem gerar débito técnico impagável.
 * **Analista de Sistemas:** Traduz os requisitos de negócio (do PO) em especificações técnicas utilizáveis pelos desenvolvedores (diagramas de sequência, modelagem de dados física/lógica e contratos de API).
### C. Pilar de Desenvolvimento e Execução
 * **Software Engineer (Backend / Frontend / Fullstack):** Implementa o código fonte seguindo as diretrizes do Arquiteto e do Analista de Sistemas. Utiliza práticas como TDD (*Test-Driven Development*) e revisões de código (*Code Review*) para garantir a manutenibilidade.
 * **DevOps Engineer:** Responsável pela infraestrutura como código (IaC), automação de pipelines de CI/CD, monitoramento (*observability*) e garantia de alta disponibilidade dos ambientes (Staging e Production).
### D. Pilar de Qualidade e Governança
 * **QA Engineer (Analista de Testes):** Atua desde o início do ciclo de desenvolvimento (*Shift-Left Testing*). Desenha planos de teste, automatiza testes funcionais/regressão e garante que nenhum incremento seja liberado com bugs críticos.
 * **Scrum Master / Agile Coach:** Remove impedimentos do time, otimiza as métricas de fluxo (como *Lead Time* e *Cycle Time*) e garante a aderência aos ritos ágeis.
## 2. Fluxo de Informação End-to-End (Ponta a Ponta)
O fluxo abaixo descreve a jornada da informação, desde a captação do cliente até a sustentação do software em produção, garantindo rastreabilidade total.
```
[ Cliente ] ──(Dores/Demandas)──> [ Sales / BDR ]
                                        │
                                (Lead Qualificado)
                                        ▼
                                 [ Product Owner ] ──(Regras de Negócio)
                                        │                           │
                                (User Stories)                      ▼
                                        │                   [ Arquiteto / Analista ]
                                        ▼                           │
                                [ Product Backlog ] <──(Specs Técnicas / APIs)
                                        │
                                (Sprint Planning)
                                        ▼
   ┌────────────────────────────> [ Dev Team ]
   │                                    │
   │                             (Pull Request)
   │                                    ▼
   │                            [ Code Review ]
   │                                    │
(Retrabalho se quebrar)           (Build OK)
   │                                    ▼
   │                            [ QA / Automated ]
   │                                    │
   └─────── (Bugs Encontrados) ───     (Aprovado)
                                        ▼
                                 [ DevOps pipeline ] ──(Deploy)──> [ Produção ]

```
### Detalhamento das Etapas do Fluxo
 1. **Fase de Descoberta (Discovery):** O time de **Sales** qualifica a oportunidade e a repassa ao **PO**. O PO realiza sessões de *Product Discovery* para entender o problema real do cliente.
 2. **Refinamento Técnico (Refinement):** O PO escreve as Histórias de Usuário. O **Arquiteto** e o **Analista de Sistemas** entram em cena para desenhar a arquitetura técnica, mapear dependências e definir os contratos de integração.
 3. **Planejamento e Execução (Sprint):** O time de desenvolvimento consome as tarefas prontas para desenvolvimento (*Ready*). O desenvolvimento é iterativo.
 4. **Garantia de Qualidade (Quality Gate):** Nenhum código vai para produção sem passar por **Code Review** (mínimo de 2 desenvolvedores revisores) e pela esteira automatizada de **QA**, mitigando falhas em ambientes produtivos.
 5. **Entrega Contínua (Deployment):** O **DevOps** garante que, uma vez aprovado, o código seja empacotado e implantado automaticamente via CI/CD, reduzindo a zero a necessidade de deploys manuais suscetíveis a erros humanos.
## 3. Melhores Práticas para Excelência e Redução de Custos
Para mitigar custos operacionais e elevar o padrão de entrega, a organização fundamenta-se nas seguintes disciplinas de engenharia de software:
| Prática Adotada | Objetivo Principal | Impacto Financeiro / Operacional |
|---|---|---|
| **Shift-Left Testing** | Trazer os testes para o início do ciclo. | Reduz o custo de correção de bugs. Um bug encontrado em produção custa até 100x mais caro do que se descoberto na fase de requisitos (Boehm). |
| **CI/CD Automatizado** | Automatizar testes de integração, linters e deploys. | Elimina o tempo ocioso de desenvolvedores gerando pacotes manuais e reduz o *Time-to-Market*. |
| **Arquiteturas Baseadas em Contrato (API-First)** | Definir mocks de APIs antes do desenvolvimento. | Permite que o time de Frontend e Backend trabalhem em paralelo, reduzindo o tempo total de entrega da feature. |
| **Cultura de Reaproveitamento (InnerSource)** | Criar bibliotecas internas para componentes comuns. | Reduz o tempo de desenvolvimento de novos projetos ao reutilizar códigos já validados de autenticação, logs e segurança. |
| **Métricas de Fluxo (DORA Metrics)** | Monitorar *Deployment Frequency* e *Lead Time for Changes*. | Identifica gargalos processuais com base em dados, evitando contratações desnecessárias ou alocações erradas de pessoal. |

# Arquitetura e Engenharia de Agentes de IA: Automação do Ciclo de Software
Este documento especifica o escopo, os modelos de dados, as regras de negócio e a pipeline de implantação para a conversão dos papéis tradicionais de uma Software House em um ecossistema de **Sistemas Multiagentes (MAS)** autônomos e colaborativos.
## 1. Engenharia de Requisitos e Escopo dos Agentes
Para garantir a substituição ou o aumento de performance (*augmentation*) das funções humanas, cada agente é definido por seu identificador único, escopo de atuação, triggers de iteração e barramento de comunicação.
### Tabela de Especificação dos Agentes de IA
| ID do Agente | Nome do Agente | Escopo de Atuação / Responsabilidade | Gatilho de Entrada (Input Trigger) | Produto Gerado (Output / Iteração) |
|---|---|---|---|---|
| **AGE-BDR-01** | *Sales Discovery Agent* | Prospecção, qualificação de leads e extração inicial de dores do cliente via transcrições/e-mails. | Novo contato no CRM ou e-mail recebido. | Proposta comercial preliminar e Termo de Abertura do Projeto (TAP). |
| **AGE-PO-02** | *Product Owner Agent* | Engenharia de requisitos, decomposição do TAP em *User Stories* com Critérios de Aceite (Gherkin). | TAP aprovado pelo cliente. | Histórias de Usuário injetadas no backlog (ex: Jira/GitHub Issues). |
| **AGE-SYS-03** | *Systems Analyst Agent* | Modelagem de dados, arquitetura lógica, mapeamento de tabelas e definição de contratos OpenAPI/Swagger. | *User Story* em estado *Ready for Analysis*. | Diagramas técnicos (Mermaid) e especificações JSON/YAML de contratos de API. |
| **AGE-ENG-04** | *Software Engineer Agent* | Geração de código (Backend/Frontend), aplicação de Design Patterns, refatoração e escrita de testes unitários. | Contrato de API e *User Story* técnica aprovados. | Pull Request (PR) com código-fonte e suite de testes unitários. |
| **AGE-QA-05** | *Quality Assurance Agent* | Execução de testes funcionais, de integração e regressão. Revisão estática de segurança do PR (SAST/Linters). | Abertura de Pull Request pelo AGE-ENG-04. | Relatório de cobertura de testes, aprovação do PR ou abertura de *Bug Issues*. |
| **AGE-OPS-06** | *DevOps & Observability Agent* | Gerenciamento de infraestrutura (IaC), orquestração de deploy e monitoramento de logs/erros em produção. | Aprovação do PR pelo AGE-QA-05 e merge na branch principal. | Deploy automatizado em ambiente de *Staging/Production* e alertas de saúde do sistema. |
## 2. Modelos de Dados e Regras de Negócio
Para evitar o acoplamento rígido e garantir que os agentes possam ser testados e mantidos individualmente, a arquitetura utiliza o padrão **Event-Driven Architecture (EDA)** sobre um barramento de mensageria centralizado.
### A. Modelo de Dados de Intercâmbio (Payload Padrão)
Cada transição de estado entre os agentes trafega no formato JSON seguindo a estrutura abaixo:
```json
{
  "eventId": "evt_987654321_abc",
  "timestamp": "2026-07-10T17:15:00Z",
  "correlationId": "corr_project_marmitaria_001",
  "sourceAgent": "AGE-SYS-03",
  "targetAgent": "AGE-ENG-04",
  "payload": {
    "featureContext": "Módulo de Autenticação e Registro de Ponto",
    "technicalSpecifications": {
      "databaseSchemaChanges": "ALTER TABLE usuarios ADD COLUMN ultimo_ponto TIMESTAMP;",
      "apiContractUrl": "https://api.internal/docs/v1/ponto.yaml"
    },
    "acceptanceCriteria": [
      "Dado que um usuário autenticado envie o token JWT válido, quando acionar o endpoint /ponto, então o sistema deve registrar o timestamp atual com precisão de milissegundos."
    ]
  },
  "securityContext": {
    "allowedScopes": ["repo:write", "artifacts:read"]
  }
}

```
### B. Arquitetura de Software e Regras de Manutenibilidade
Para que o sistema multiagentes não se torne obsoleto ou de difícil manutenção, adota-se o padrão de **Camadas Isoladas para Agentes de IA**:
 1. **Camada de Percepção (Ingestion Layer):** Traduz os gatilhos externos (webhooks do GitHub, e-mails, mensagens do Slack) no JSON padrão do ecossistema.
 2. **Camada de Raciocínio (Cognitive Layer):** Onde residem as técnicas de Engenharia de Prompt:
   * **Few-Shot Prompting:** Exemplos estáticos de código perfeitamente estruturados e documentados fornecidos no contexto do agente.
   * **RAG (Retrieval-Augmented Generation):** Busca vetorial em bancos de dados (ex: pgvector ou MongoDB Atlas) para injetar as regras de negócio atualizadas do cliente e padrões de arquitetura da empresa antes de acionar o LLM.
 3. **Camada de Ação (Execution Layer):** Ferramentas executáveis (*Function Calling*) que permitem aos agentes interagir com o mundo real (fazer commits, disparar builds, criar issues).
#### Estratégia de Testabilidade e Guardrails (Garantia de Qualidade)
 * **LLM-as-a-Judge:** Um agente validador isolado analisa semanticamente se o código gerado pelo *AGE-ENG-04* quebra as diretrizes arquiteturais definidas pelo *Arquiteto de Software*.
 * **Ambientes Isolados (Sandboxing):** O agente de engenharia de software executa a escrita e compilação do código dentro de containers Docker efêmeros e seguros, prevenindo a execução de códigos maliciosos ou loops infinitos no ambiente de desenvolvimento principal.
## 3. Pipeline de Publicação e Implantação (CI/CD)
A pipeline de publicação dos agentes visa garantir estabilidade através de ambientes de testes automatizados de prompts e versionamento rigoroso de modelos.
### Arquitetura da Pipeline de CI/CD
```
[ Git Commit (Prompt/Código) ]
               │
               ▼
┌────────────────────────────────────────┐
│  Fase 1: Linting & Validação Estática  │
│  - Checagem sintática de JSON/YAML     │
│  - Validação de Schemas de Mensagens   │
└──────────────┬─────────────────────────┘
               │
               ▼
┌────────────────────────────────────────┐
│  Fase 2: Prompt Evaluation (Testes)    │
│  - Execução de Assertivas Semânticas   │
│  - Validação de RAG (Retenção de Contexto)
└──────────────┬─────────────────────────┘
               │
               ▼
┌────────────────────────────────────────┐
│  Fase 3: Construção e Registro         │
│  - Build das imagens Docker dos Agentes│
│  - Push para o Container Registry      │
└──────────────┬─────────────────────────┘
               │
               ▼
┌────────────────────────────────────────┐
│  Fase 4: Deploy Progressivo (GitOps)   │
│  - Atualização do Cluster via ArgoCD   │
│  - Liberação Canary (10% -> 100%)      │
└────────────────────────────────────────┘

```
### Detalhes de Implementação da Pipeline
 1. **Versionamento de Prompts (PromptOps):** Todos os prompts de sistema, esquemas de *Few-Shot* e hyperparâmetros (como *temperature* e *top_p*) são tratados como código (infraestrutura declarativa) e versionados no Git.
 2. **Avaliação Automatizada (Fase 2):** Antes de ir para a produção, os agentes passam por testes de regressão de comportamento usando frameworks como *Promptflow* ou *LangSmith*. Se o agente alterar drasticamente a forma de responder a uma dor clássica do cliente, a pipeline é abortada.
 3. **Deploy em Arquitetura de Microserviços (Fase 3 e 4):** Cada agente é empacotado como um microserviço em um container Docker, exposto via endpoints assíncronos e orquestrado dentro de um cluster Kubernetes. O deploy utiliza a estratégia **Canary**, permitindo avaliar o comportamento dos agentes em 10% dos novos projetos antes da virada total da operação, minimizando riscos operacionais e custos com tokens desperdiçados.


## Modelo XML para configuração de agente de IA:

```xml
<agent>
   <configuration>
      <version>"1.0"</version>
      <identity>
         <name>NomeDoAgente</name>
         <role>Analista de Sistemas Especialista em [Domínio]</role>
         <description>Um assistente focado em resolver problemas complexos de [Área] de forma analítica e direta.</description>
         <tone_and_style>Profissional, conciso, focado em soluções e levemente técnico.</tone_and_style>
      </identity>
      <context>
         <environment>Produção / Desenvolvimento</environment>
         <core_knowledge>
            <topic>Arquitetura de Software e Integração de Dados</topic>
            <topic>Melhores práticas de codificação e documentação</topic>
         </core_knowledge>
      </context>
      <instructions>
         <rule id="1">Sempre valide as premissas antes de propor uma solução de código ou arquitetura.</rule>
         <rule id="2">Se a requisição for ambígua, peça esclarecimentos específicos em vez de assumir o pior cenário.</rule>
         <constraints>
            <never_do>Não invente APIs, bibliotecas ou parâmetros inexistentes (alucinação).</never_do>
            <never_do>Não exponha dados sensíveis, credenciais fictícias ou chaves de acesso nos exemplos.</never_do>
            <always_do>Utilize boas práticas de componentização e legibilidade no código gerado.</always_do>
         </constraints>
      </instructions>
      <response_format>
         <step order="1" name="Analysis">Pense silenciosamente sobre o problema, identificando gargalos e requisitos.</step>
         <step order="2" name="Explanation">Explique a abordagem adotada de forma clara e direta.</step>
         <step order="3" name="Implementation">Forneça o artefato (código, configuração ou texto) revisado e limpo.</step>
         <output_style>Markdown limpo, utilizando blocos de código com a sintaxe correta e sem rodeios introdutórios.</output_style>
      </response_format>
      <variables>
         <user_input>{{USER_PROMPT}}</user_input>
         <current_date>{{CURRENT_DATE}}</current_date>
      </variables>
   </configuration>
</agent>
```
