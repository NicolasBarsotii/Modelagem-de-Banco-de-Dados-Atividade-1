# Entrega 2 — Modelo Lógico, Implementação SQL e Apresentação Final
### Modelagem de um sistema de gestão de informações para a MAXfood

## Integrantes

| Nome completo do aluno | RGM | Usuário do GitHub |
| :--- | :--- | :--- |
| Anderson Josué Quispe Salcedo | 50132075 | ⚠️ (andersonjosue1528) |
| João Victor Cipriano Bezerra | 48071277 | ⚠️ (john099gg) |
| Luis Angel Yana Poma | 50132229 | ⚠️ (luisangelyp2019-oss) |
| Nicolas de Oliveira Batista Barsoti | 48030058 | ⚠️ (nicolasbarsotii) |
| Paulo Henrique Oliveira dos Santos | 47848430 | ⚠️ (PauloSantss) |

---

## 1. Relatório Técnico Final

### 1.1 Revisão do Modelo Conceitual

#### Caracterização da organização

- **Nome e natureza da organização:** Lanchonete **MAXfood**, estabelecimento comercial de alimentação com fins lucrativos, localizado dentro da UNICID — Universidade Cidade de São Paulo, Campus Tatuapé.
- **Contexto e porte:** Organização de pequeno porte. Funciona das **10h às 22h**. Possui **2 funcionários**: um no atendimento e outro na cozinha. A média é de **45 a 50 clientes por dia**, podendo chegar a **60** em dias de maior movimento. O volume estimado é de aproximadamente **1.200 a 1.500 pedidos por mês**.
- **Problemas e necessidades identificados (Crise Operacional):**
  - **P1 (Ruptura de Estoque):** Falta de controle sistemático gera falta de insumos, principalmente refrigerantes e bebidas.
  - **P2 (Desorganização de Pedidos):** Pedidos por WhatsApp/telefone são anotados manualmente em cadernos ou planilhas soltas, gerando risco de perda de informações.
  - **P3 (Perdas de Perecíveis):** Prejuízos eventuais com alimentos que não foram salvos e venceram, pois não há controle de validade.
  - **P4 (Fechamento de Caixa Manual):** Dificuldade em consolidar as diferentes formas de pagamento ao final do dia.
- **Escopo do sistema:** O banco de dados reunirá todos os dados da organização: fornecedores, compras/reposição, produtos, controle de estoque (entradas, saídas, perdas), funcionários, pedidos, itens, combos, acompanhamentos, pagamentos e fechamento de caixa.
- **Justificativa da escolha:** A MAXfood é uma organização real, acessível ao grupo, com processos claros e porte adequado para modelagem. A ausência de um sistema informatizado a torna um caso ideal para a aplicação dos conceitos de modelagem.
- **Evidências da organização:** Fotos do local e do cardápio em `fotos/`; perfil no Google Maps e Instagram; endereço: UNICID — Campus Tatuapé.
- **Responsável pela organização:** Rafael Novais — Telefone: (11) 91343-3270.

#### Relato da entrevista

- **Quem:** Entrevista realizada com o responsável Rafael Novais. Participação dos integrantes do grupo.
- **Quando e onde:** Realizada presencialmente no ambiente da organização (UNICID — Tatuapé), com comprovação via foto em `fotos/foto_no_dia_da_entrevista.jpeg`.
- **O que foi levantado (e observação presencial):** Durante a observação, notou-se que o estoque de bebidas é mantido em geladeiras separadas (estoque de amostra) e em um depósito nos fundos (estoque interno). Foi confirmado que não há cadastro de clientes e que a venda fiada é rara. O levantamento completo está em `Levantamento/levantamento.md`.

#### Processos de negócio

1. **Vendas e Atendimento:** Pedidos no balcão, WhatsApp ou telefone; montagem de combos; escolha de acompanhamentos (até 3) e coberturas; aplicação de desconto UNICID; pagamento (débito, crédito, Pix, dinheiro); cancelamento de pedidos (antes da entrega).
2. **Compras e Recebimento:** Identificação de estoque mínimo; pedido de reposição ao fornecedor; recebimento de mercadoria com conferência e entrada no estoque.
3. **Apoio e Gestão de Estoque:** Contagem diária; registro de perdas de perecíveis; controle de validade; fechamento de caixa diário.

- *Processos não incluídos:* Emissão de nota fiscal (a lanchonete não emite e não repassa ao cliente) e cadastro de clientes (não é prática da organização).

#### Requisitos do Sistema

**Requisitos Funcionais (RF):**
- RF01 a RF16: cadastro de fornecedores, produtos, movimentações, pedidos, prato do dia, combos, acompanhamentos, descontos.
- RF17: O sistema deve permitir registrar pedidos de compra/reposição de fornecedores.
- RF18: O sistema deve permitir registrar o recebimento de mercadorias e a entrada no estoque.
- RF19: O sistema deve permitir registrar perdas de perecíveis (descarte).
- RF20: O sistema deve permitir o cancelamento de pedidos com registro de justificativa.
- RF21: O sistema deve permitir gerar o relatório de fechamento de caixa diário agrupado por forma de pagamento.

**Requisitos Não Funcionais (RNF):**
- RNF01 a RNF08: usabilidade, disponibilidade, desempenho, segurança, integridade, backup, compatibilidade, privacidade.

#### Regras de Negócio

- **RN01:** Desconto de R$ 2,00 para funcionários da UNICID, mediante comprovação.
- **RN02:** O prato do dia é sempre um item do cardápio e muda diariamente.
- **RN03:** Formas de pagamento: Débito, Crédito, Pix e Dinheiro.
- **RN04:** Fiado só com autorização do dono (status pendente).
- **RN05:** Reposição antecipada quando o estoque atingir o mínimo.
- **RN06:** Contagem diária de estoque.
- **RN07:** Estoque de amostra (geladeira/vitrine) × estoque interno (depósito).
- **RN08:** Até 3 acompanhamentos por refeição; coberturas apenas para batatas e sanduíches.
- **RN09:** Produtos perecíveis vencidos devem ser descartados e registrados como perda.
- **RN10:** Pedidos só podem ser cancelados se o status for "Aberto" ou "Em preparo".
- **RN11:** A lanchonete não emite nota fiscal; o comprovante é o cupom não fiscal.

#### Notação do DER conceitual

- **Software utilizado:** ⚠️ **PENDENTE — informar em qual software o DER foi criado (ex.: brModelo, draw.io, etc.)** e confirmar que a notação segue o padrão brModelo (retângulos, losangos, cardinalidades `(mín, máx)`, chave com círculo preenchido, etc.).
- O DER está no arquivo `DER.png`.

#### Caso A — Apontamentos da correção da E1

| Apontamento da correção da E1 | O que mudou no trabalho | Por quê |
| :--- | :--- | :--- |
| Identificadores não marcados (círculos vazios) | Todos os identificadores (chaves) foram preenchidos com círculo preto. | Para diferenciar atributos comuns de chaves primárias no modelo conceitual. |
| Fornecedor `(1,1)` do lado de FORNECEDOR | Alterado para `(0,1)` do lado de FORNECEDOR. | Nem toda movimentação de estoque tem fornecedor associado. |
| Registra `(1,n)` do lado de PEDIDO | Alterado para `(0,n)` do lado de PEDIDO. | Permite cadastrar funcionário que ainda não registrou pedido. |
| Atributo `id_funcionario` com `(0, n)` | Cardinalidade removida do atributo. | Atributos simples não possuem cardinalidade no brModelo. |
| Divergências (Pagamento, Pedido, Fornecedor) | Atributos faltantes adicionados no DER. | Para refletir exatamente o Dicionário de Dados. |
| Ausência de processo de Compras | Criadas `PEDIDO_COMPRA` e `ITEM_COMPRA`. | Para cobrir reposição de estoque e resolver P1. |
| Ausência de fechamento e perdas | Criadas `FECHAMENTO_CAIXA` e tipo "Perda" em `ESTOQUE_MOVIMENTACAO`. | Para cobrir RN09 e P4. |

> ⚠️ **PENDENTE:** Se a correção da E1 tiver outros apontamentos, acrescente-os nesta tabela. O esqueleto trata apontamento não listado como **não corrigido**.

#### 1.2 Conversão do Modelo Conceitual para o Modelo Lógico

- **Entidades → Tabelas:** Cada retângulo tornou-se uma tabela.
- **Atributos → Colunas:** Atributos simples viraram colunas; atributo multivalorado foi convertido em tabela filha.
- **Relacionamentos → Chaves:** 1:N por migração da PK do lado 1 para o lado N como FK; N:N por tabelas associativas (`ITEM_PEDIDO`, `COMBO_ITEM`).
- **Cardinalidades:** `(0,1)` → FK permite `NULL`; `(1,1)` e `(1,n)` → `NOT NULL`.
- **Generalização/Especialização:** O modelo não possui herança; todas as entidades são tabelas independentes.

#### 1.3 Definição de Chaves Primárias e Estrangeiras

| Tabela | PK | FKs |
| :--- | :--- | :--- |
| FUNCIONARIO | CD_FUNCIONARIO | — |
| FORNECEDOR | CD_FORNECEDOR | — |
| PRODUTO | CD_PRODUTO | — |
| ESTOQUE_MOVIMENTACAO | CD_MOVIMENTACAO | CD_PRODUTO; CD_FORNECEDOR (opcional) |
| PEDIDO_COMPRA | CD_PEDIDO_COMPRA | CD_FORNECEDOR |
| ITEM_COMPRA | CD_ITEM_COMPRA | CD_PEDIDO_COMPRA; CD_PRODUTO |
| PEDIDO | CD_PEDIDO | CD_FUNCIONARIO |
| ITEM_PEDIDO | CD_ITEM | CD_PEDIDO; CD_PRODUTO |
| PAGAMENTO | CD_PAGAMENTO | CD_PEDIDO |
| PRATO_DO_DIA | CD_PRATO_DIA | CD_PRODUTO |
| COMBO_ITEM | CD_COMBO_ITEM | CD_COMBO; CD_PRODUTO |
| FECHAMENTO_CAIXA | CD_FECHAMENTO | — |

#### 1.4 Processo de Normalização (1FN, 2FN e 3FN)

- **1FN:** Eliminação de grupos repetitivos. Os itens do pedido foram separados em `ITEM_PEDIDO` e `ITEM_COMPRA`; um pedido não armazena produtos em uma única coluna de texto, mas em linhas na tabela filha.
- **2FN:** Na tabela `ITEM_PEDIDO`, `QT_ITEM` e `VL_UNITARIO` dependem da PK `CD_ITEM` (surrogada). Se a PK fosse composta (`CD_PEDIDO` + `CD_PRODUTO`), o preço dependeria do produto, gerando dependência parcial.
- **3FN:** Não há atributos não-chave dependendo de outros atributos não-chave. O nome do fornecedor não é guardado em `ESTOQUE_MOVIMENTACAO`; a tabela `PAGAMENTO` foi separada de `PEDIDO` para evitar dependência transitiva.

> ⚠️ **PENDENTE:** O esqueleto pede uma **justificativa do processo** (por que cada FN foi necessária no seu caso). O texto acima já cobre parte, mas convém reforçar a justificativa de negócio para cada FN.

#### 1.5 Justificativas Técnicas das Decisões

- **Chaves Primárias:** Chaves artificiais (surrogadas) no padrão `CD_` (`INT AUTO_INCREMENT`) para garantir estabilidade. Dados naturais (CNPJ, telefone) podem mudar ou conter erros.
- **Chaves Estrangeiras:** Garantem integridade referencial. A FK de `ESTOQUE_MOVIMENTACAO` para `FORNECEDOR` é `NULL` porque saídas, ajustes e perdas (RN09) não têm fornecedor.
- **Restrições:**
  - `UNIQUE` em `NR_CNPJ` (FORNECEDOR).
  - `CHECK (QT_ESTOQUE >= 0)` em `PRODUTO`.
  - `CHECK (TP_MOVIMENTACAO IN ('Entrada','Saída','Ajuste','Perda'))` — RN09.
  - `DEFAULT CURRENT_TIMESTAMP` em `DT_PEDIDO`.
- **Decisões Arquiteturais:** `CLIENTE` omitida conforme levantamento; nome e telefone do cliente são atributos opcionais de `PEDIDO`. `PEDIDO_COMPRA` criada para cobrir reposição (P1).

#### 1.6 Proposta de Arquitetura Analítica para BI e IA

**Indicadores e KPIs propostos:**

| KPI | Fórmula | Período | Meta sugerida |
| :--- | :--- | :--- | :--- |
| KPI01 — Ticket Médio | `SUM(VL_TOTAL) / COUNT(CD_PEDIDO)` | Mensal | ⚠️ (definir com o responsável) |
| KPI02 — Ruptura de Estoque | `COUNT(CD_PRODUTO) WHERE QT_ESTOQUE < QT_ESTOQUE_MIN` | Diário | Zero produtos abaixo do mínimo |
| KPI03 — Faturamento por Canal | `SUM(VL_TOTAL) GROUP BY TP_CANAL` | Mensal | ⚠️ (definir) |
| KPI04 — Taxa de Perdas | `SUM(valor de perdas) / SUM(compras)` | Mensal | Redução contínua |
| KPI05 — Mix de Pagamento | `SUM(VL_PAGO) GROUP BY TP_PAGAMENTO` | Diário/Mensal | ⚠️ (definir) |

**Potencial para BI:** dashboards de vendas por período, produtos mais vendidos, formas de pagamento, perdas e estoque crítico.

**Aplicações analíticas e de IA:**
- **Previsão de demanda:** usar histórico de `ITEM_PEDIDO` e `DT_PEDIDO` para prever vendas por dia da semana (mitigar P3).
- **Alerta preditivo de estoque:** avisar com antecedência sobre necessidade de reposição (mitigar P1).

**Rastreabilidade:**

| Problema ou KPI | Tabelas envolvidas | Consulta no script |
| :--- | :--- | :--- |
| P1 — Ruptura de estoque (KPI02) | PRODUTO, ESTOQUE_MOVIMENTACAO | G02 |
| P2 — Desorganização de pedidos | PEDIDO, ITEM_PEDIDO | ⚠️ (definir consulta) |
| P3 — Perdas de perecíveis (KPI04) | ESTOQUE_MOVIMENTACAO | G03 |
| P4 — Fechamento de caixa (KPI05) | PAGAMENTO, FECHAMENTO_CAIXA | G04 |
| KPI01 — Ticket Médio | PEDIDO | G05 |

> ⚠️ **PENDENTE:** O esqueleto exige **pelo menos uma consulta por problema declarado e por KPI**. P2 está sem consulta associada; P3 e P4 precisam ser confirmados no Script.sql. Além disso, as consultas G01–G05 precisam estar **efetivamente implementadas no `Script.sql`** com os cabeçalhos padronizados.

---

## 2. Modelo Lógico Relacional

- O modelo lógico está documentado em `Modelo Lógico.md` e representado visualmente em ⚠️ **(informar o arquivo de imagem do modelo lógico, ex.: `Modelo_Logico.png`)**.
- **Software utilizado:** ⚠️ **PENDENTE — informar em qual software o modelo lógico foi criado** (ex.: brModelo, draw.io, MySQL Workbench).

---

## 3. Script SQL Completo

- Arquivo: `docs/Script.sql`.
- ⚠️ **PENDENTE:** confirmar que o script contém, nesta ordem: `CREATE DATABASE`, `CREATE TABLE` com constraints, `INSERT INTO` (massa de dados), `SELECT` com `JOIN`, `UPDATE`, `DELETE`, consultas gerenciais (`G01`…) e consultas de auditoria (`A01`…).
- ⚠️ **PENDENTE:** se a massa de dados **não** estiver dentro do `Script.sql`, criar `docs/massa_dados.sql` separado e linkar aqui.

---

## 4. Massa de Dados

- ⚠️ **PENDENTE:** O README atual afirma que existe `docs/massa_dados.sql`, mas **esse arquivo não está no repositório**. Se a massa estiver dentro do `Script.sql`, substitua a afirmação por “a massa de dados está incluída no `docs/Script.sql`”. Se não estiver, crie o arquivo.
- A massa deve ser **fictícia**, mas coerente com os volumes reais (1.200–1.500 pedidos/mês; 2 funcionários; estoque de bebidas e perecíveis; diferentes formas de pagamento; pedidos cancelados; produtos abaixo do mínimo; perdas registradas).

---

## 5. Repositório GitHub

Arquivos e pastas existentes:
- `README.md` (este arquivo)
- `DER.png`
- `Dicionario.html`
- `Modelo Lógico.md`
- `Levantamento/levantamento.md`
- `docs/Script.sql`
- `fotos/` (cardápios e fotos da entrevista)

> ⚠️ **PENDENTE:** o esqueleto valoriza **histórico de commits equilibrado** e **commits com a conta de cada integrante**. O repositório atual tem poucos commits, quase todos “Add files via upload”. Vale a pena distribuir commits ao longo do tempo e garantir que cada membro tenha commits identificáveis.

---

## 6. Uso de Inteligência Artificial

| Item | O que registrar |
| :--- | :--- |
| **Ferramenta e etapa** | DeepSeek — reestruturação do README para a Entrega 2 e revisão dos processos/regras conforme apontamentos da E1. |
| **Motivação** | Adequar o modelo aos feedbacks do professor (compras, cardinalidades, perdas/cancelamento) de forma ágil. |
| **Prompt(s) utilizados** | “Deepseek, preciso fazer a segunda entrega de uma atividade… Me ajude a fazer com essa explicação.” |
| **Resposta recebida** | Sugestão de `PEDIDO_COMPRA`, `FECHAMENTO_CAIXA`, tipo “Perda”, correção de cardinalidade e estrutura do README. |
| **Fontes consultadas e verificadas** | Confronto com DER original, Dicionário de Dados HTML e anotações de campo. |
| **Trechos rejeitados ou corrigidos** | Sugestão de entidade `CLIENTE` rejeitada (contraria a entrevista); data de validade movida para `ESTOQUE_MOVIMENTACAO`. |
| **Justificativa da escolha final** | Mantido o texto ajustado por cobrir os processos, problemas e consultas gerenciais. |
| **Reflexão crítica** | IA útil para organizar, mas propõe soluções genéricas (“empresariais”) que não se aplicam ao porte da MAXfood; o grupo filtrou. |

> ⚠️ **PENDENTE:** Se houve outros usos de IA (ex.: geração da massa de dados, escrita de queries), acrescente linhas ou parágrafos nesta seção. O esqueleto diz que **uso de IA não declarado será penalizado**.

---

## 7. Apresentação Corporativa Final

> ⚠️ **PENDENTE:** esta seção do esqueleto é sobre a **apresentação oral** (8 minutos, slides minimalistas, demonstração SQL, defesa do modelo). O README deve **mencionar** que a apresentação será realizada, mas os slides não precisam estar no README — podem ficar em arquivo separado (ex.: `docs/apresentacao.pdf`). Verifique com o professor se é necessário anexar os slides ao repositório.

---

## Critérios Atitudinais (20%)

> Avaliados por Avaliação 360º e pelo histórico de commits. Não é necessário preencher seção no README, mas o **equilíbrio de commits** e a **participação de todos** na apresentação são critérios.
