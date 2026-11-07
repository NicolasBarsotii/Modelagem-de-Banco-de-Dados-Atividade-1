# Modelo Lógico Relacional — MAXfood

O modelo lógico da MAXfood representa a estrutura do banco de dados por meio de tabelas, atributos e relacionamentos. As chaves primárias (**PK**) identificam exclusivamente cada registro, enquanto as chaves estrangeiras (**FK**) estabelecem as relações de integridade entre as tabelas.

---

## 1. Estrutura das Tabelas

### 1.1 FUNCIONARIO
| Atributo | Chave |
| :--- | :--- |
| `CD_FUNCIONARIO` | **PK** |
| `NM_FUNCIONARIO` | - |
| `TP_CARGO` | - |
| `NR_TELEFONE` | - |
| `NM_EMAIL` | - |
| `IN_ATIVO` | - |

### 1.2 FORNECEDOR
| Atributo | Chave |
| :--- | :--- |
| `CD_FORNECEDOR` | **PK** |
| `NM_FORNECEDOR` | - |
| `NR_CNPJ` | **UNIQUE** |
| `NR_TELEFONE` | - |
| `NM_EMAIL` | - |
| `DS_ENDERECO` | - |
| `NM_CONTATO` | - |
| `IN_ATIVO` | - |

### 1.3 PRODUTO
| Atributo | Chave |
| :--- | :--- |
| `CD_PRODUTO` | **PK** |
| `NM_PRODUTO` | - |
| `DS_PRODUTO` | - |
| `TP_CATEGORIA` | - |
| `VL_VENDA` | - |
| `VL_COMBO` | - |
| `TP_UNIDADE` | - |
| `TP_ESTOQUE` | - |
| `QT_ESTOQUE` | - |
| `QT_ESTOQUE_MIN` | - |
| `IN_PERECIVEL` | - |
| `IN_PERMITE_ACOMP` | - |
| `IN_PERMITE_COB` | - |
| `IN_ATIVO` | - |

### 1.4 ACOMPANHAMENTO
| Atributo | Chave |
| :--- | :--- |
| `CD_ACOMPANHAMENTO` | **PK** |
| `NM_ACOMPANHAMENTO` | - |
| `TP_ACOMPANHAMENTO` | - |
| `VL_ADICIONAL` | - |

### 1.5 FECHAMENTO_CAIXA
| Atributo | Chave |
| :--- | :--- |
| `CD_FECHAMENTO` | **PK** |
| `DT_FECHAMENTO` | - |
| `VL_TOTAL_DINHEIRO` | - |
| `VL_TOTAL_CARTAO` | - |
| `VL_TOTAL_PIX` | - |
| `VL_TOTAL_GERAL` | - |

### 1.6 PEDIDO_COMPRA
| Atributo | Chave |
| :--- | :--- |
| `CD_PEDIDO_COMPRA` | **PK** |
| `CD_FORNECEDOR` | **FK** |
| `DT_COMPRA` | - |
| `TP_STATUS` | - |

### 1.7 ITEM_COMPRA
| Atributo | Chave |
| :--- | :--- |
| `CD_ITEM_COMPRA` | **PK** |
| `CD_PEDIDO_COMPRA` | **FK** |
| `CD_PRODUTO` | **FK** |
| `QT_COMPRA` | - |
| `VL_UNITARIO` | - |

### 1.8 ESTOQUE_MOVIMENTACAO
| Atributo | Chave |
| :--- | :--- |
| `CD_MOVIMENTACAO` | **PK** |
| `CD_PRODUTO` | **FK** |
| `CD_FORNECEDOR` | **FK** (Permite NULL) |
| `TP_MOVIMENTACAO` | - |
| `QT_MOVIMENTACAO` | - |
| `DT_MOVIMENTACAO` | - |
| `DS_OBSERVACAO` | - |

### 1.9 PEDIDO
| Atributo | Chave |
| :--- | :--- |
| `CD_PEDIDO` | **PK** |
| `CD_FUNCIONARIO` | **FK** |
| `DT_PEDIDO` | - |
| `TP_CANAL` | - |
| `TP_STATUS` | - |
| `NM_CLIENTE` | - |
| `NR_TELEFONE_CLI` | - |
| `VL_TOTAL` | - |
| `VL_DESCONTO` | - |
| `DS_MOTIVO_DESC` | - |
| `DS_OBSERVACAO` | - |

### 1.10 ITEM_PEDIDO
| Atributo | Chave |
| :--- | :--- |
| `CD_ITEM` | **PK** |
| `CD_PEDIDO` | **FK** |
| `CD_PRODUTO` | **FK** |
| `QT_ITEM` | - |
| `VL_UNITARIO` | - |
| `VL_SUBTOTAL` | - |
| `DS_OBSERVACAO` | - |

### 1.11 PAGAMENTO
| Atributo | Chave |
| :--- | :--- |
| `CD_PAGAMENTO` | **PK** |
| `CD_PEDIDO` | **FK** |
| `TP_FORMA_PAG` | - |
| `VL_PAGAMENTO` | - |
| `DT_PAGAMENTO` | - |
| `TP_STATUS_PAG` | - |

### 1.12 NOTA_FISCAL *(Nova Tabela)*
| Atributo | Chave |
| :--- | :--- |
| `CD_NOTA_FISCAL` | **PK** |
| `CD_PEDIDO` | **FK** |
| `NR_NOTA_FISCAL` | - |
| `DT_EMISSAO` | - |
| `VL_NOTA` | - |
| `DS_CHAVE_ACESSO` | **UNIQUE** |
| `TP_STATUS_NOTA` | - |

### 1.13 PRATO_DO_DIA
| Atributo | Chave |
| :--- | :--- |
| `CD_PRATO_DIA` | **PK** |
| `CD_PRODUTO` | **FK** |
| `DT_OFERTA` | - |
| `VL_PROMOCIONAL` | - |
| `DS_DESCRICAO` | - |
| `IN_ATIVO` | - |

### 1.14 COMBO_ITEM
| Atributo | Chave |
| :--- | :--- |
| `CD_COMBO_ITEM` | **PK** |
| `CD_PRODUTO_COMBO` | **FK** |
| `CD_PRODUTO_ITEM` | **FK** |
| `QT_ITEM` | - |

### 1.15 ITEM_PEDIDO_ACOMPANHAMENTO
| Atributo | Chave |
| :--- | :--- |
| `CD_ITEM` | **PK, FK** |
| `CD_ACOMPANHAMENTO` | **PK, FK** |
| `QT_ESCOLHA` | - |

---

## 2. Relacionamentos entre as Tabelas

A tabela abaixo demonstra a cardinalidade (1:N) entre as entidades do sistema.

| Tabela de Origem | Cardinalidade | Tabela Relacionada |
| :--- | :---: | :--- |
| FUNCIONARIO | 1:N | PEDIDO |
| FORNECEDOR | 1:N | PEDIDO_COMPRA |
| PEDIDO_COMPRA | 1:N | ITEM_COMPRA |
| PRODUTO | 1:N | ITEM_COMPRA |
| PRODUTO | 1:N | ESTOQUE_MOVIMENTACAO |
| FORNECEDOR | 1:N | ESTOQUE_MOVIMENTACAO |
| PEDIDO | 1:N | ITEM_PEDIDO |
| PRODUTO | 1:N | ITEM_PEDIDO |
| PEDIDO | 1:N | PAGAMENTO |
| PEDIDO | 1:N | NOTA_FISCAL |
| PRODUTO | 1:N | PRATO_DO_DIA |
| PRODUTO (combo) | 1:N | COMBO_ITEM |
| PRODUTO (componente) | 1:N | COMBO_ITEM |
| ITEM_PEDIDO | 1:N | ITEM_PEDIDO_ACOMPANHAMENTO |
| ACOMPANHAMENTO | 1:N | ITEM_PEDIDO_ACOMPANHAMENTO |

### 2.1 Notas sobre Relacionamentos Específicos

*   **Combos:** A tabela `COMBO_ITEM` estabelece o relacionamento entre produtos, permitindo que um produto cadastrado como combo seja composto por outros produtos. Ela possui duas chaves estrangeiras que apontam para a tabela `PRODUTO`: uma identifica o combo e a outra identifica o produto que faz parte dele.
*   **Acompanhamentos:** A tabela `ITEM_PEDIDO_ACOMPANHAMENTO` relaciona os itens de um pedido aos acompanhamentos escolhidos, permitindo registrar as opções selecionadas e suas quantidades. Essa tabela utiliza uma **chave primária composta** por `CD_ITEM` e `CD_ACOMPANHAMENTO`.
*   **Fiscal:** A tabela `NOTA_FISCAL` relaciona-se com `PEDIDO` para garantir a emissão e o controle dos documentos fiscais de cada venda realizada, mantendo o histórico de chaves de acesso e status do documento.

---

## 3. Considerações Finais

O modelo lógico da MAXfood foi estruturado para organizar as informações relacionadas aos funcionários, fornecedores, produtos, pedidos, pagamentos, compras, movimentações de estoque e emissão de notas fiscais. 

A estrutura permite registrar os pedidos realizados, controlar os produtos utilizados nas vendas, acompanhar as compras feitas com fornecedores, registrar os pagamentos recebidos e emitir os documentos fiscais exigidos. As tabelas também contemplam os pratos do dia, os combos e os acompanhamentos escolhidos pelos clientes, atendendo às principais necessidades identificadas durante o levantamento de requisitos.

---

## 4. Legenda

| Sigla | Significado |
| :--- | :--- |
| **PK** | Chave Primária |
| **FK** | Chave Estrangeira |
| **UNIQUE** | Valor único, não repetido |
| **NULL** | Permite valor nulo |
| **1:N** | Um para muitos |
