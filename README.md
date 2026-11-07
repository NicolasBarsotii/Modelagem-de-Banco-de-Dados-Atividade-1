# Entrega 2 — Modelo Lógico, Implementação SQL e Apresentação Final

### Modelagem de um sistema de gestão de informações para a MAXfood

## Integrantes

| Nome completo do aluno | RGM | Usuário do GitHub |
| :--- | :--- | :--- |
| Anderson Josué Quispe Salcedo | 50132075 | *(andersonjosue1528)* |
| João Victor Cipriano Bezerra | 48071277 | *(john099gg)* |
| Luis Angel Yana Poma | 50132229 | *(luisangelyp2019-oss)* |
| Nicolas de Oliveira Batista Barsoti | 48030058 | *(NicolasBarsotii)* |
| Paulo Henrique Oliveira dos Santos | 47848430 | *(PauloSantss)* |

&nbsp;

## 1. Relatório Técnico Final

### 1.1 Revisão do Modelo Conceitual

**Caracterização da organização**

A MAXfood é uma lanchonete de pequeno porte, com fins lucrativos, localizada estrategicamente dentro do campus Tatuapé da Universidade Cidade de São Paulo (UNICID). Seu horário de funcionamento vai das 10h às 22h, atendendo majoritariamente o público acadêmico (alunos, professores e funcionários). A operação é enxuta, contando atualmente com apenas dois funcionários (um dedicado ao atendimento e outro à cozinha), sendo gerida pelo responsável Rafael Novais.

O volume de operação é significativo para o seu porte: estima-se uma média de 45 a 50 clientes por dia, podendo chegar a 60 em dias de pico (como períodos de provas), o que resulta em um fluxo aproximado de 1.200 a 1.500 pedidos mensais. Toda essa movimentação é gerenciada atualmente de forma manual, utilizando planilhas soltas em Excel e anotações em cadernos de papel.

**Problemas e necessidades identificados (Crise Operacional)**

A falta de um sistema informatizado integrado gera quatro problemas principais, que impactam diretamente a rentabilidade e a rotina da lanchonete:
*   **P1 (Ruptura de Estoque):** O controle visual é falho. A lanchonete frequentemente sofre com a falta de insumos essenciais, principalmente bebidas (refrigerantes). O estoque "de amostra" (nas geladeiras) acaba, e o funcionário só percebe quando o cliente pede, gerando perda de venda.
*   **P2 (Desorganização de Pedidos):** Os pedidos feitos por WhatsApp ou telefone são anotados em um caderno. Essa prática gera erros de comunicação com a cozinha, perda de comandas e impossibilidade de consultar o histórico de pedidos de forma rápida.
*   **P3 (Perdas de Perecíveis):** Sem um controle rigoroso de validade e quantidade, ocorrem prejuízos financeiros com alimentos que vencem e precisam ser descartados.
*   **P4 (Fechamento de Caixa Manual):** Ao final do dia, o gerente precisa somar manualmente todas as formas de pagamento (Pix, dinheiro, cartão), o que consome tempo e está sujeito a erros de contagem.

**Escopo do sistema**

O banco de dados foi projetado para ser o núcleo de gestão da MAXfood, centralizando todas as informações da organização. O escopo engloba desde o cadastro de fornecedores e entrada de mercadorias, até o controle de estoque interno/amostra, gestão de funcionários, registro de pedidos (com regras de descontos e cancelamentos), gestão de combos e acompanhamentos, controle de pagamentos, emissão de notas fiscais e fechamento de caixa.

**Justificativa da escolha e Evidências**

A escolha da MAXfood justifica-se por ser uma organização real, acessível ao grupo, com processos muito claros e que sofre claramente com a falta de tecnologia. O porte é ideal para a modelagem, permitindo criar um sistema robusto, mas sem complexidades desnecessárias de grandes redes. As evidências (fotos do local, cardápio, perfil no Google Maps e Instagram) e o contato com o responsável (Rafael Novais - 11913433270) estão documentados no repositório.

**Relato da entrevista e Observação Presencial**

A entrevista foi realizada presencialmente no ambiente da lanchonete com o proprietário, Rafael Novais. Durante a visita, o grupo pôde contrastar o relato do dono com a realidade observada:
*   **Relato vs. Observação:** O proprietário afirmou que "controla o estoque olhando as geladeiras". No entanto, a observação presencial revelou que não há nenhum tipo de planilha de contagem diária, e o estoque do depósito (interno) não é conferido antes de abrir o caixa.
*   **O Levantamento Completo:** O documento detalhado com todas as perguntas, respostas e observações da visita está disponível no arquivo [levantamento/levantamento.md](./levantamento/levantamento.md).

**Processos de negócio**

O sistema foi modelado para abranger 100% dos processos da lanchonete:
1.  **Fluxo de Vendas:** O cliente faz o pedido (presencial ou remoto). O atendente registra o pedido, aplica descontos (se houver), e o sistema envia os itens para a cozinha. Após a entrega, o pagamento é registrado e a Nota Fiscal é emitida.
2.  **Fluxo de Compras:** Quando o estoque atinge o nível mínimo (monitorado pelo sistema), o gerente gera um Pedido de Compra para o Fornecedor. Ao receber a mercadoria, ele registra a entrada no estoque.
3.  **Fluxo de Apoio (Estoque e Caixa):** Diariamente, a cozinha verifica a validade dos itens (registrando perdas, se houver) e o caixa consolida os pagamentos do dia (Fechamento de Caixa).

**Requisitos do Sistema**

*   **Requisitos Funcionais (RF):** O sistema deve permitir o cadastro completo de fornecedores, produtos (com controle de categoria, preço e unidade), funcionários e acompanhamentos. Deve registrar pedidos, calculando o total automaticamente, gerenciar a fila de preparo (status), registrar as múltiplas formas de pagamento, gerar o fechamento de caixa diário, emitir o registro de Nota Fiscal para fins legais, controlar a entrada e saída de estoque e emitir alertas de nível mínimo.
*   **Requisitos Não Funcionais (RNF):** A interface deve ser de alta usabilidade (simples, para ser usada no balcão). O sistema deve ter disponibilidade total durante o horário de funcionamento (10h-22h), desempenho rápido para não gerar filas, e segurança por meio de perfis de acesso (Atendente, Cozinha, Gerente). Os dados devem passar por rotinas de backup diário.

**Regras de Negócio**

As regras foram mapeadas para garantir a integridade da operação:
*   **RN01:** Desconto fixo de R$ 2,00 para funcionários da UNICID, exigindo comprovação de vínculo.
*   **RN02:** O prato do dia deve ser um produto já cadastrado no sistema, com preço promocional que muda diariamente.
*   **RN03:** Formas de pagamento aceitas: Débito, Crédito, Pix e Dinheiro.
*   **RN04:** A venda fiada (pagamento pendente) só pode ser registrada mediante autorização explícita do gerente.
*   **RN05:** O sistema deve sugerir a reposição (Pedido de Compra) quando o `QT_ESTOQUE` for menor ou igual ao `QT_ESTOQUE_MIN`.
*   **RN06:** Refeições permitem no máximo 3 acompanhamentos. Coberturas são restritas a batatas e sanduíches.
*   **RN07:** O estoque é dividido em "Amostra" (vitrine/geladeira) e "Interno" (depósito).
*   **RN08:** Produtos perecíveis vencidos devem ser baixados do estoque como "Perda".
*   **RN09:** Um pedido cancelado só pode ser alterado se o status não for "Entregue".
*   **RN10:** Todo pedido finalizado gera um registro de Nota Fiscal (NFe) para conformidade legal, mesmo que o cliente não solicite a via impressa.

**Notação do DER conceitual**

O DER foi criado no software **brModelo Web**. [Link para o DER](./DER.png).
*Correções aplicadas em relação à Entrega 1:* Inclusão das entidades de Compras (`PEDIDO_COMPRA`), Fechamento de Caixa (`FECHAMENTO_CAIXA`) e Nota Fiscal (`NOTA_FISCAL`). Correção das cardinalidades (ex: Fornecedor para `(0,1)` em movimentações) e marcação de todas as chaves primárias (identificadores).

### 1.2 Conversão do Modelo Conceitual para o Modelo Lógico

A conversão seguiu as regras formais da modelagem relacional:
*   **Entidades → Tabelas:** Cada entidade do DER tornou-se uma tabela no modelo lógico.
*   **Relacionamentos 1:N:** Foram resolvidos pela migração da Chave Primária (PK) da tabela "Pai" (lado 1) para a tabela "Filha" (lado N) na forma de Chave Estrangeira (FK). Exemplo: A PK `CD_FORNECEDOR` foi para a tabela `PEDIDO_COMPRA`.
*   **Relacionamentos N:N:** Foram convertidos em tabelas associativas. Exemplo: O relacionamento entre `PEDIDO` e `PRODUTO` deu origem à tabela `ITEM_PEDIDO`, que contém as FKs de ambos e os atributos próprios da relação (quantidade, preço).
*   **Atributos Multivalorados:** Foram isolados em tabelas próprias.

### 1.3 Definição de Chaves Primárias e Estrangeiras

*   **Chaves Primárias (PK):** Todas as tabelas utilizam chaves artificiais (surrogadas) no padrão `CD_` (Código), configuradas como `INT AUTO_INCREMENT`. Isso garante que o identificador nunca mude, mesmo que o nome de um produto ou o CNPJ de um fornecedor seja atualizado.
*   **Chaves Estrangeiras (FK):** Garantem a integridade referencial. Por exemplo, não é possível registrar um pagamento (`PAGAMENTO`) para um pedido (`CD_PEDIDO`) que não existe. A tabela `NOTA_FISCAL` também possui uma FK apontando para `PEDIDO`, garantindo que uma nota não fique órfã.

### 1.4 Processo de Normalização (1FN, 2FN e 3FN)

O banco foi estruturado para evitar redundâncias e anomalias de atualização:
*   **1ª Forma Normal (1FN):** Todos os atributos são atômicos. Não existem campos que guardam listas (ex: em vez de ter uma coluna "Produtos" no Pedido, cada produto é uma linha na tabela `ITEM_PEDIDO`).
*   **2ª Forma Normal (2FN):** Na tabela `ITEM_PEDIDO`, os atributos `VL_UNITARIO` e `QT_ITEM` dependem da chave primária completa da linha (`CD_ITEM`), e não apenas de uma parte dela.
*   **3ª Forma Normal (3FN):** Não há dependências transitivas. Por exemplo, o nome do fornecedor não é guardado na tabela de estoque, apenas a sua FK (`CD_FORNECEDOR`). Se o nome mudar, altera-se apenas na tabela `FORNECEDOR`, mantendo o banco consistente.

### 1.5 Justificativas Técnicas das Decisões

*   **Ausência da tabela CLIENTE:** Conforme o levantamento, a MAXfood não realiza cadastro de clientes. Criar essa tabela forçaria o atendente a fazer um cadastro a cada venda, o que quebraria a agilidade do balcão. Os dados do cliente (nome e telefone) para entregas são tratados como atributos opcionais em `PEDIDO`.
*   **Inclusão da tabela NOTA_FISCAL:** Apesar da lanchonete não emitir nota fiscal no dia a dia, a estrutura foi preparada para a conformidade legal. A tabela permite registrar a chave de acesso (NFe) e o status do documento.
*   **Separação de PAGAMENTO e PEDIDO:** Um pedido pode ser pago de formas mistas (ex: R$ 10 em dinheiro e R$ 15 no Pix). A tabela separada permite registrar múltiplos pagamentos vinculados ao mesmo pedido.
*   **Uso de ENUM:** Para campos de domínio fixo (ex: `TP_CANAL` com 'Balcão', 'WhatsApp', 'Telefone'), o uso de ENUM garante a integridade dos dados e impede erros de digitação que quebrariam as consultas.

### 1.6 Proposta de Arquitetura Analítica para BI e IA

*   **Indicadores (KPIs):**
    *   **Ticket Médio (KPI01):** Ajuda a entender o poder de compra do cliente da UNICID.
    *   **Ruptura de Estoque (KPI02):** Alerta sobre produtos que estão zerando.
    *   **Taxa de Perdas (KPI04):** Percentual do faturamento perdido com validade vencida.
*   **Aplicações de IA:** Com o histórico de `PEDIDO` e `ITEM_PEDIDO`, um modelo de machine learning pode prever a demanda de lanches em dias de semana (considerando o calendário acadêmico da UNICID), otimizando a compra de insumos e evitando o P3 (perdas).

**Rastreabilidade:**

| Problema ou KPI | Tabelas envolvidas | Consulta no script |
| :--- | :--- | :--- |
| P1 - Ruptura de bebidas (KPI02) | PRODUTO | G01 |
| P2 - Desorganização de pedidos | PEDIDO, ITEM_PEDIDO | G05 |
| P3 - Perdas de perecíveis (KPI04) | ESTOQUE_MOVIMENTACAO | G03 |
| P4 - Fechamento de caixa (KPI05) | PAGAMENTO, FECHAMENTO_CAIXA | G02 |
| KPI01 - Ticket Médio | PEDIDO | G04 |

---

## 2. Modelo Lógico Relacional

O modelo lógico foi criado no **MySQL Workbench** e pode ser visualizado na imagem abaixo:
[Clique aqui para abrir o Modelo Lógico](./Modelo_Logico.png)

Ele representa as tabelas, colunas com seus respectivos tipos de dados, Chaves Primárias (PK) e Chaves Estrangeiras (FK), demonstrando a correta conversão das regras de negócio para a estrutura relacional.

## 3. Script SQL Completo

O script SQL foi implementado em **MySQL** e está disponível no repositório no arquivo: [docs/Script.sql](./docs/Script.sql).
Ele contém desde a criação do banco de dados (DDL), tabelas com constraints (PK, FK, CHECK, UNIQUE), carga de dados (massa fictícia variada), comandos DML (Update/Delete), consultas gerenciais (G01 a G06) e consultas de auditoria (A01 a A04).

## 4. Massa de Dados

A massa de dados fictícia está incluída diretamente no script SQL (`docs/Script.sql`). O volume e a variedade foram baseados nos números reais da organização (estimativa de 1.500 pedidos/mês). Foram gerados dados que simulam cenários reais e críticos: pedidos cancelados, clientes com pagamentos pendentes (fiado), produtos perecíveis vencidos, produtos abaixo do estoque mínimo e emissão de notas fiscais (emitidas e canceladas), garantindo que as consultas gerenciais retornem dados reais.

## 5. Repositório GitHub

O repositório está organizado da seguinte forma:
- `README.md` (Relatório Técnico)
- [Dicionario.html](./Dicionario.html) (Dicionário de Dados atualizado com LGPD e Relacionamentos)
- [DER.png](./DER.png) (Modelo Conceitual revisado)
- [Modelo_Logico.png](./Modelo_Logico.png) (Modelo Lógico)
- `levantamento/` (Pasta com o arquivo de levantamento e fotos)
- `docs/` (Pasta contendo o [Script.sql](./docs/Script.sql))

---

## 6. Uso de Inteligência Artificial

O grupo utilizou ferramentas de IA como apoio técnico para garantir a qualidade, padronização e o nível de detalhamento exigido nesta etapa. Abaixo, o registro transparente de como a ferramenta foi empregada:

| Item | O que registrar |
| :--- | :--- |
| **Ferramenta e etapa** | **DeepSeek**. Utilizada nas etapas de estruturação e revisão textual do README, modelagem de dados e escrita/validação de scripts SQL. |
| **Motivação** | A IA foi utilizada para agilizar a redação técnica do relatório (garantindo a clareza e o detalhamento solicitados) e como "segunda opinião" para validar a sintaxe das consultas SQL e a integridade do modelo lógico. |
| **Prompt(s) utilizados** | Foram solicitados à IA: a revisão estrutural do README com base nas exigências da Entrega 2; a expansão dos textos explicativos sobre processos e regras de negócio; a inclusão da estrutura de Nota Fiscal (exigida na correção); e a geração do script SQL e do dicionário HTML. |
| **Resposta recebida** | A IA retornou os textos do README expandidos e devidamente justificados, o script SQL (incluindo `CREATE TABLE`, `INSERT` e consultas de auditoria/gerenciais) e o código HTML do dicionário. |
| **Fontes consultadas e verificadas** | Todas as sugestões foram confrontadas com as anotações da entrevista de campo e com o teste prático no MySQL Workbench. |
| **Trechos rejeitados ou corrigidos** | A IA sugeriu a criação da entidade `CLIENTE`, que foi rejeitada (a lanchonete não realiza cadastro). Houve também um erro de sintaxe gerado na consulta `G03` (falha no `GROUP BY`), que foi corrigido após testes no banco real. Por fim, a estrutura de emissão de Nota Fiscal foi inserida após apontamento do professor. |
| **Justificativa da escolha final** | A IA foi mantida como ferramenta de apoio pois ajudou a elevar o nível de detalhamento da documentação, mas todas as decisões de negócio e o código final foram validados e testados pela equipe. |
| **Reflexão crítica** | O uso da IA demonstrou que, embora ela seja excelente para gerar estruturas iniciais e organizar textos, ela tende a generalizar regras de negócio (como presumir que todo comércio emite nota fiscal ou cadastra clientes). O grupo percebeu que a pesquisa de campo e a validação humana são insubstituíveis. |

---

## 7. Apresentação Corporativa Final

A apresentação (pitch de 8 minutos) será realizada presencialmente, seguindo a ordem exigida:
1. Contextualização da crise operacional da MAXfood (P1 a P4).
2. Apresentação da solução e do Modelo Lógico.
3. Demonstração do banco de dados rodando no MySQL Workbench (Consultas G01, G02 e Auditoria A01).
4. Potencial de BI e IA para prever demanda e evitar perdas.
5. Benefícios diretos para a tomada de decisão do proprietário.
