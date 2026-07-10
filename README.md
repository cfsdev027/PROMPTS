# PROMPTS
Guias, boas práticas e documentações essenciais para engenharia de prompts e configuração de Agentes de IA. Um repositório centralizado para estruturar instruções eficientes, otimizar fluxos de trabalho autônomos e maximizar o potencial de LLMs em diferentes ecossistemas. Ideal para desenvolvedores e entusiastas de automação inteligente.

# Guia de Referência para Criação de PROMPTS e Agentes de IA em Linhas de Produção


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
