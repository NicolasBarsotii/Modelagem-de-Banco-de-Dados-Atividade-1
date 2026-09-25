# Entrega 1 — Modelo Conceitual (DER)
### Modelagem de um sistema de gestão de informações para uma organização de pequeno porte

## Metadados

- **Nomes dos alunos e RGM**
  - Anderson Josué Quispe S. — RGM: 50132075
  - João Victor Cipriano Bezerra — RGM: 48071277
  - Luis Angel — RGM: 50132229
  - Nicolas de Oliveira Batista Barsoti — RGM: 48030058

---

## 1. Caracterização da Organização

- **Nome e natureza da organização:** Lanchonete **MAXfood**, estabelecimento comercial de alimentação com fins lucrativos, localizado dentro da UNICID — Universidade Cidade de São Paulo, Campus Tatuapé.

- **Contexto e porte:** Organização de pequeno porte. Funciona das **10h às 22h**. Possui **2 funcionários**: um no atendimento e outro na cozinha. A média é de **45 a 50 clientes por dia**, podendo chegar a **60** em dias de maior movimento. O responsável atual é **Rafael Novais**.

- **Problemas e necessidades identificados:** O controle é feito com **planilhas em Excel ou anotações em papel**, de forma pouco sistemática. Há relatos de **falta de estoque**, principalmente de refrigerantes e bebidas. Pedidos por WhatsApp/telefone são anotados manualmente. A venda fiada não é prática comum e só ocorre para alguns clientes amigos do dono. Já houve prejuízos eventuais com alimentos que não foram salvos. O responsável demonstra interesse em um sistema/aplicativo que permita, por exemplo, **tirar foto da lista/comanda e transformar os itens em um carrinho de pedido**. Atualmente **não possui sistema informatizado**.

- **Justificativa da escolha:** A MAXfood é uma organização real, acessível ao grupo, com processos claros e porte adequado para modelagem. Ela possui cadastro de fornecedores, controle de estoque, pedidos, pagamentos, combos, acompanhamentos e regras específicas, o que gera entidades e relacionamentos suficientes para a Entrega 1, sem se tornar complexa demais.

- **Evidências da organização:**
  - Endereço: UNICID — Universidade Cidade de São Paulo, Campus Tatuapé.
  - Responsável: Rafael Novais.
  - Telefone: 11913433270
  - E-mail: maxrestaurantes@gmail.com
  - Instagram: https://www.instagram.com/maxrestaurantes/
  - Google Maps: https://maps.app.goo.gl/T4cPDESrDLvxNKnm9
  - Fotos do local e do cardápio anexadas ao repositório.

---

## 2. Processos de Negócio

- **Principais processos mapeados:**
  - Cadastro de fornecedores.
  - Controle de estoque, com entrada antecipada de produtos e contagem diária.
  - Atendimento no balcão: o cliente faz o pedido, o pedido é repassado para a cozinha e depois entregue ao cliente.
  - Pedidos por WhatsApp e telefone, com anotações em caderno ou planilha.
  - Pagamento nas formas débito, crédito, Pix e dinheiro.
  - Definição e venda do prato do dia, que é um prato já existente no cardápio e muda diariamente.
  - Venda de combos (sanduíche + batata + bebida).
  - Montagem de refeições com escolha de até 3 acompanhamentos.
  - Adição de coberturas (bacon, mussarela, cheddar, requeijão) em batatas e sanduíches.
  - Aplicação de desconto de R$ 2,00 para funcionários da UNICID, mediante comprovação de vínculo (crachá ou app).
  - Venda fiada ocasional, apenas para clientes amigos do dono.

- **Fluxogramas:** (Opcional) Não foram elaborados fluxogramas visuais; a descrição textual acima cobre os processos-chave.

---

## 3. Requisitos do Sistema

### 3.1 Requisitos Funcionais

- O sistema deve permitir cadastrar e gerenciar fornecedores.
- O sistema deve permitir cadastrar e gerenciar produtos.
- O sistema deve registrar entradas, saídas e ajustes de estoque.
- O sistema deve emitir alerta quando o estoque estiver abaixo do mínimo, especialmente para refrigerantes e bebidas.
- O sistema deve permitir registrar pedidos feitos no balcão.
- O sistema deve permitir registrar pedidos recebidos por WhatsApp ou telefone.
- O sistema deve permitir adicionar itens ao pedido e calcular o total automaticamente.
- O sistema deve permitir registrar o prato do dia e seu preço promocional.
- O sistema deve permitir aplicar desconto de R$ 2,00 para funcionários da UNICID, com validação de vínculo.
- O sistema deve permitir registrar a forma de pagamento: débito, crédito, Pix ou dinheiro.
- O sistema deve permitir registrar venda fiada, com identificação do cliente e status de pagamento pendente, quando autorizada pelo dono.
- O sistema deve permitir, futuramente, tirar foto de uma lista/comanda e converter os itens em carrinho de pedido.
- O sistema deve permitir consultar o histórico de pedidos e movimentações de estoque.
- O sistema deve permitir compor combos a partir de produtos já cadastrados.
- O sistema deve permitir selecionar acompanhamentos (até 3) para refeições.
- O sistema deve permitir selecionar coberturas para batatas e sanduíches.

### 3.2 Requisitos Não Funcionais

- **Usabilidade:** interface simples e rápida, adequada para uso durante atendimento no balcão.
- **Disponibilidade:** funcionamento durante o horário da lanchonete, das 10h às 22h.
- **Desempenho:** registro de pedido e consulta de estoque em poucos segundos.
- **Segurança:** controle de acesso por usuário/funcionário.
- **Integridade:** totais de pedidos e baixas de estoque devem ser consistentes.
- **Backup:** os dados devem ter rotina de backup para evitar perdas.
- **Compatibilidade:** preferência por acesso via celular/tablet, por causa do uso no balcão e dos pedidos por WhatsApp.
- **Privacidade:** não armazenar dados pessoais além do necessário; não há cadastro de clientes atualmente.

---

## 4. Regras de Negócio

- **Regras operacionais:**
  - O desconto para funcionários da UNICID é de **R$ 2,00 a menos**, aplicável a qualquer item, mediante comprovação de vínculo (crachá ou app).
  - O prato do dia é sempre um prato já cadastrado no cardápio e muda diariamente.
  - As formas de pagamento aceitas são **débito, crédito, Pix e dinheiro**.
  - A venda fiada não é prática comum; só ocorre para clientes amigos do dono.
  - O estoque é controlado de forma antecipada para evitar falta.
  - Há contagem diária de estoque.
  - Existe estoque de produtos de amostra (itens visíveis para os clientes) e estoque interno (itens não visíveis).
  - Fornecedores são cadastrados; clientes não são cadastrados atualmente.
  - Pedidos por WhatsApp/telefone são anotados em caderno ou planilha.

- **Restrições organizacionais:**
  - Há regras padrão de vigilância sanitária, mas elas não atrapalham a operação.
  - Não há regra específica da faculdade que impeça o funcionamento, segundo a entrevista.
  - A política interna mais relevante é o desconto de R$ 2,00 para funcionários da UNICID.
  - O horário de funcionamento é das 10h às 22h.

---

## 5. Dicionário de Dados Conceitual (Preliminar)

> Exemplos de valores, se usados, devem ser fictícios. Não inserir dados reais de clientes, funcionários ou fornecedores.

### Entidade: FORNECEDOR

| Atributo | Descrição | Regra de negócio associada |
|----------|-----------|------------------------------|
| id_fornecedor | Identificador único do fornecedor | Obrigatório |
| nome | Nome ou razão social | Obrigatório |
| cnpj | CNPJ do fornecedor | Opcional, único quando informado |
| telefone | Telefone de contato | Obrigatório |
| email | E-mail de contato | Opcional |
| endereco | Endereço do fornecedor | Opcional |
| contato_responsavel | Pessoa responsável na empresa | Opcional |
| ativo | Indica se o fornecedor está ativo | Padrão: ativo |

### Entidade: PRODUTO

| Atributo | Descrição | Regra de negócio associada |
|----------|-----------|------------------------------|
| id_produto | Identificador único do produto | Obrigatório |
| nome | Nome do produto (ex: X-Burger, Batata Frita) | Obrigatório |
| descricao | Descrição do produto | Opcional |
| categoria | Categoria (Lanches, Refeições, Espetinhos, Pastéis, Saladas, Massas, Bebidas, etc.) | Obrigatório |
| preco_venda | Preço de venda atual | Obrigatório, maior ou igual a zero |
| preco_combo | Preço quando vendido como combo (se aplicável) | Opcional, maior ou igual a zero |
| unidade_medida | Unidade (un, porção, prato etc.) | Obrigatório |
| tipo_estoque | Interno ou amostra | Obrigatório |
| quantidade_estoque | Quantidade disponível | Maior ou igual a zero |
| estoque_minimo | Quantidade mínima para alerta | Maior ou igual a zero |
| perecivel | Indica se o produto é perecível | Sim/Não |
| permite_acompanhamento | Indica se o produto permite escolher acompanhamentos | Sim/Não (ex: Refeições = Sim; Saladas = Não) |
| permite_cobertura | Indica se o produto permite coberturas | Sim/Não (ex: Batata Frita = Sim) |
| ativo | Indica se o produto está ativo | Padrão: ativo |

### Entidade: ESTOQUE_MOVIMENTACAO

| Atributo | Descrição | Regra de negócio associada |
|----------|-----------|------------------------------|
| id_movimentacao | Identificador único da movimentação | Obrigatório |
| id_produto | Produto movimentado | Referência ao PRODUTO, obrigatório |
| tipo_movimentacao | Entrada, saída ou ajuste | Obrigatório |
| quantidade | Quantidade movimentada | Maior que zero |
| data_hora | Data e hora da movimentação | Obrigatório |
| id_fornecedor | Fornecedor relacionado, quando for entrada | Referência opcional |
| observacao | Observação sobre a movimentação | Opcional |

### Entidade: PEDIDO

| Atributo | Descrição | Regra de negócio associada |
|----------|-----------|------------------------------|
| id_pedido | Identificador único do pedido | Obrigatório |
| data_hora | Data e hora do pedido | Obrigatório |
| canal | Balcão, WhatsApp ou telefone | Obrigatório |
| status | Aberto, em preparo, entregue, cancelado | Obrigatório |
| nome_cliente | Nome do cliente, quando informado | Opcional, pois não há cadastro de clientes |
| telefone_cliente | Telefone do cliente, quando informado | Opcional |
| total | Valor total do pedido | Calculado |
| desconto_valor | Valor do desconto aplicado | Maior ou igual a zero |
| desconto_motivo | Motivo do desconto | Ex.: funcionário da UNICID |
| id_funcionario | Funcionário que registrou o pedido | Referência ao FUNCIONARIO |
| observacao | Observações do pedido | Opcional |

### Entidade: ITEM_PEDIDO

| Atributo | Descrição | Regra de negócio associada |
|----------|-----------|------------------------------|
| id_item | Identificador único do item | Obrigatório |
| id_pedido | Pedido ao qual o item pertence | Referência ao PEDIDO, obrigatório |
| id_produto | Produto do item | Referência ao PRODUTO, obrigatório |
| quantidade | Quantidade pedida | Maior que zero |
| preco_unitario | Preço unitário no momento da venda | Maior ou igual a zero |
| subtotal | Quantidade × preço unitário | Calculado |
| observacao | Observação do item | Opcional |

### Entidade: PAGAMENTO

| Atributo | Descrição | Regra de negócio associada |
|----------|-----------|------------------------------|
| id_pagamento | Identificador único do pagamento | Obrigatório |
| id_pedido | Pedido pago | Referência ao PEDIDO, obrigatório |
| forma_pagamento | Débito, crédito, Pix ou dinheiro | Obrigatório |
| valor | Valor pago | Maior que zero |
| data_hora | Data e hora do pagamento | Obrigatório |
| status | Pendente, pago ou cancelado | Obrigatório |

### Entidade: FUNCIONARIO

| Atributo | Descrição | Regra de negócio associada |
|----------|-----------|------------------------------|
| id_funcionario | Identificador único do funcionário | Obrigatório |
| nome | Nome do funcionário | Obrigatório |
| cargo | Cargo/função (atendimento ou cozinha) | Obrigatório |
| telefone | Telefone de contato | Opcional |
| email | E-mail de contato | Opcional |
| ativo | Indica se está ativo | Padrão: ativo |

### Entidade: PRATO_DO_DIA

| Atributo | Descrição | Regra de negócio associada |
|----------|-----------|------------------------------|
| id_prato_dia | Identificador único do prato do dia | Obrigatório |
| data | Data de oferta | Obrigatório |
| id_produto | Produto ofertado como prato do dia | Referência ao PRODUTO, obrigatório |
| preco_promocional | Preço promocional do dia | Maior ou igual a zero |
| descricao | Descrição complementar | Opcional |
| ativo | Indica se a oferta está ativa | Padrão: ativo |

### Entidade: COMBO_ITEM

| Atributo | Descrição | Regra de negócio associada |
|----------|-----------|------------------------------|
| id_combo_item | Identificador único | Obrigatório |
| id_produto_combo | Produto que é o combo (ex: X-Burger Combo) | Referência ao PRODUTO, obrigatório |
| id_produto_item | Produto que compõe o combo (ex: Batata Frita) | Referência ao PRODUTO, obrigatório |
| quantidade | Quantidade do item no combo | Maior que zero |

### Entidade: ACOMPANHAMENTO

| Atributo | Descrição | Regra de negócio associada |
|----------|-----------|------------------------------|
| id_acompanhamento | Identificador único | Obrigatório |
| nome | Nome do acompanhamento/cobertura (ex: Arroz, Feijão, Bacon, Cheddar) | Obrigatório |
| tipo | Tipo (Acompanhamento ou Cobertura) | Obrigatório |
| preco_adicional | Preço extra, se houver | Padrão: 0,00 |

### Entidade: ITEM_PEDIDO_ACOMPANHAMENTO

| Atributo | Descrição | Regra de negócio associada |
|----------|-----------|------------------------------|
| id_item_pedido | Item do pedido | Referência ao ITEM_PEDIDO, obrigatório |
| id_acompanhamento | Acompanhamento escolhido | Referência ao ACOMPANHAMENTO, obrigatório |
| quantidade | Quantidade escolhida | Maior que zero |

---

## 6. Modelagem Conceitual (Entidades, Atributos, Relacionamentos)

- **Entidades reconhecidas:**
  - **FORNECEDOR:** porque a lanchonete possui cadastro de fornecedores e faz pedidos de reposição.
  - **PRODUTO:** porque há controle de estoque, preços, categorias e itens vendidos.
  - **ESTOQUE_MOVIMENTACAO:** porque o estoque precisa registrar entradas, saídas e ajustes, inclusive contagem diária.
  - **PEDIDO:** porque é o núcleo do atendimento, tanto no balcão quanto por WhatsApp/telefone.
  - **ITEM_PEDIDO:** porque um pedido pode conter vários produtos e um produto pode aparecer em vários pedidos.
  - **PAGAMENTO:** porque há diferentes formas de pagamento e necessidade de controle financeiro.
  - **FUNCIONARIO:** porque há funcionários registrando pedidos e porque o sistema precisa de responsável pelo registro.
  - **PRATO_DO_DIA:** porque existe oferta diária com preço promocional, regra específica da organização.
  - **COMBO_ITEM:** porque o cardápio possui combos (sanduíche + batata + bebida) que são compostos por outros produtos.
  - **ACOMPANHAMENTO:** porque as refeições permitem escolher até 3 acompanhamentos e as batatas permitem coberturas.
  - **ITEM_PEDIDO_ACOMPANHAMENTO:** porque um item do pedido pode ter vários acompanhamentos/coberturas escolhidos.

- **Atributos e classificações:** conforme dicionário preliminar acima.

- **Relacionamentos pertinentes:**
  - FORNECEDOR 1:N ESTOQUE_MOVIMENTACAO — um fornecedor pode gerar várias entradas de estoque.
  - PRODUTO 1:N ESTOQUE_MOVIMENTACAO — um produto pode ter várias movimentações.
  - FUNCIONARIO 1:N PEDIDO — um funcionário pode registrar vários pedidos.
  - PEDIDO 1:N ITEM_PEDIDO — um pedido contém vários itens.
  - PRODUTO 1:N ITEM_PEDIDO — um produto pode compor vários itens de pedidos.
  - PEDIDO 1:N PAGAMENTO — um pedido pode ter um ou mais pagamentos, inclusive pagamento misto.
  - PRODUTO 1:N PRATO_DO_DIA — um produto pode ser ofertado como prato do dia em várias datas.
  - PRODUTO 1:N COMBO_ITEM (como combo) — um combo é composto por vários itens.
  - PRODUTO 1:N COMBO_ITEM (como item) — um produto pode compor vários combos.
  - ITEM_PEDIDO 1:N ITEM_PEDIDO_ACOMPANHAMENTO — um item do pedido pode ter vários acompanhamentos.
  - ACOMPANHAMENTO 1:N ITEM_PEDIDO_ACOMPANHAMENTO — um acompanhamento pode ser escolhido em vários itens de pedido.

- **Restrições e políticas organizacionais aplicadas ao modelo:**
  - Não foi criada entidade CLIENTE porque a lanchonete não realiza cadastro de clientes atualmente.
  - O desconto de R$ 2,00 para funcionários da UNICID foi modelado como atributo do PEDIDO, pois é uma regra simples e não exige cadastro de cliente.
  - A venda fiada pode ser representada pelo status de pagamento pendente, mas só é autorizada pelo dono para clientes específicos.
  - O estoque de amostra (itens visíveis) e o estoque interno foram diferenciados pelo atributo `tipo_estoque`.

---

## 7. Diagrama Entidade-Relacionamento (DER)

> A imagem do DER está anexada ao repositório (`der.png`).

![DER](der.png)

---

## 8. Justificativa Técnica

A modelagem parte dos processos reais observados na MAXfood. Optou-se por não criar a entidade **CLIENTE** porque a lanchonete não faz cadastro de clientes; quando necessário, nome e telefone ficam como atributos opcionais do pedido. Isso evita criar uma entidade sem dados reais de apoio nesta etapa.

A entidade **PEDIDO** foi separada de **ITEM_PEDIDO** porque um pedido pode conter vários produtos, e um mesmo produto pode aparecer em vários pedidos. Essa separação resolve o relacionamento N:N entre pedido e produto e permite guardar o preço praticado no momento da venda.

A entidade **ESTOQUE_MOVIMENTACAO** foi criada em vez de apenas um campo "quantidade em estoque" no produto, porque a lanchonete faz entradas, saídas, contagem diária e precisa de histórico. O campo `tipo_estoque` diferencia estoque interno e estoque de amostra (itens visíveis para os clientes).

A entidade **PRATO_DO_DIA** foi mantida separada porque é uma oferta diária com preço promocional, e não apenas uma característica fixa do produto. Isso permite representar mudanças de preço e de data sem alterar o cadastro do produto.

A entidade **PAGAMENTO** foi separada de **PEDIDO** para permitir mais de uma forma de pagamento por pedido, controlar venda fiada como pendência e registrar o status financeiro. O desconto de R$ 2,00 foi modelado como atributo do pedido por ser uma regra simples e direta.

A criação da entidade **COMBO_ITEM** resolve o relacionamento N:N entre produtos, permitindo que um combo seja decomposto em seus itens (sanduíche, batata, bebida) sem duplicar o cadastro do produto. Já a entidade **ACOMPANHAMENTO** e a tabela associativa **ITEM_PEDIDO_ACOMPANHAMENTO** permitem registrar as escolhas feitas pelo cliente (até 3 acompanhamentos para refeições, ou coberturas para batatas), mantendo o histórico do que foi efetivamente vendido. O campo `permite_acompanhamento` e `permite_cobertura` no produto ajuda o sistema a validar essas escolhas no momento do pedido.

Por fim, **FUNCIONARIO** permite identificar quem registrou o pedido, apoiando responsabilidade e controle interno.

---

## 9. Uso de Inteligência Artificial

| Item | O que registrar |
|------|------------------|
| **Ferramenta e etapa** | **DeepSeek**. Utilizada em três etapas principais: (1) organização e estruturação das anotações brutas da pesquisa de campo; (2) sugestão da modelagem conceitual (entidades, atributos, relacionamentos e cardinalidades) com base nos processos reais da MAXfood; (3) formatação do README no padrão exigido pelo esqueleto da entrega e geração do código do DER em Mermaid. |
| **Motivação** | O grupo precisava transformar anotações de entrevista, fotos do cardápio e observações de campo em um documento técnico padronizado. A IA foi usada para agilizar a estruturação inicial e para servir como "segunda opinião" na modelagem, evitando que alguma entidade ou relacionamento importante fosse esquecido. |
| **Prompt(s) utilizados** | 1) "Deepseek, preciso fazer um trabalho da faculdade para construção de banco de dados, ele forneceu um arquivo de esqueleto de como deve ficar o documento, basicamente deve ficar exata exatamente igual ao dele, dá uma olhada:" (seguido do arquivo `00-c_Esqueleto_Entrega_1.md`).<br>2) "Já fiz a pesquisa de campo, da uma olhada, eu fiz uma anotações da pesquisa de campo com no caso, a lanchonete maxFOOD, que fica na universidade mesmo, ve se da para mesclar com as suas informações:" (seguido das anotações da entrevista com Rafael Novais).<br>3) "Certo, vou te mandar uma foto dos cardápios também:" (seguido das imagens do cardápio).<br>4) "perfeito, me fala o que está faltando para ficar exatamente igual?"<br>5) "1. Dados Administrativos... [respostas com dados faltantes da entrevista]". |
| **Resposta recebida** | A IA estruturou o README seguindo o esqueleto, sugeriu entidades como FORNECEDOR, PRODUTO, PEDIDO, ITEM_PEDIDO, PAGAMENTO, FUNCIONARIO, PRATO_DO_DIA, COMBO_ITEM, ACOMPANHAMENTO e ITEM_PEDIDO_ACOMPANHAMENTO. Também gerou o código Mermaid para o DER e o modelo do dicionário de dados, além de apontar lacunas que precisavam ser confirmadas com o responsável (ex.: significado dos números 45-50 e 60, regras de estoque de amostra, etc.). |
| **Fontes consultadas e verificadas** | A IA não citou fontes externas. Todas as sugestões foram confrontadas com as anotações da entrevista com o responsável Rafael Novais e com as fotos do cardápio. Por exemplo, a IA sugeriu uma entidade CLIENTE, mas o grupo verificou na entrevista que a MAXfood **não realiza cadastro de clientes**, e a sugestão foi descartada. |
| **Trechos rejeitados ou corrigidos** | - **Entidade CLIENTE:** sugerida pela IA, mas rejeitada porque a lanchonete não faz cadastro de clientes. Os dados de cliente (nome e telefone) foram modelados como atributos opcionais do PEDIDO.<br>- **Venda fiada:** a IA inicialmente modelou como uma prática comum; o grupo corrigiu para "ocasional e apenas para clientes amigos do dono", conforme a entrevista.<br>- **Estoque de amostra:** a IA interpretou como "amostras grátis de fornecedores", mas o grupo corrigiu para "itens visíveis para os clientes", conforme esclarecido pelo responsável.<br>- **Desconto de R$ 2,00:** a IA sugeriu modelar como uma entidade separada; o grupo optou por manter como atributo do PEDIDO por ser uma regra simples e direta. |
| **Justificativa da escolha final** | O grupo manteve a estrutura geral sugerida pela IA porque ela seguiu fielmente o esqueleto do professor. No entanto, todo o conteúdo foi validado e adaptado à realidade da MAXfood. As entidades e regras que não correspondiam aos processos reais foram removidas ou corrigidas. A modelagem final reflete exclusivamente o que foi observado na pesquisa de campo. |
| **Reflexão crítica** | A IA foi útil para agilizar a organização e sugerir uma modelagem inicial, mas demonstrou uma tendência a generalizar modelos de lanchonete, criando entidades que não existem na MAXfood (como CLIENTE). Também interpretou incorretamente termos específicos da organização, como "estoque de amostra". Isso reforça que a IA deve ser usada como apoio, e nunca como substituta da pesquisa de campo e da validação humana. O grupo aprendeu que é essencial questionar e verificar cada sugestão da IA com os dados reais. |

---

## Critérios Atitudinais (20%)
**Estes critérios NÃO constam explicitamente como item de entrega no README.** Eles são avaliados por meio de **Avaliação 360º entre os integrantes do grupo** e, no caso da Colaboração, também pela **colaboração equilibrada no histórico de commits** do repositório GitHub.

---

## Resumo dos Pesos

| Dimensão | Peso total |
|----------|-----------|
| Conceitual (contexto, requisitos/regras, modelagem, justificativa técnica) | 30% |
| Procedimental (requisitos, fluxogramas, dicionário de dados, DER) | 50% |
| Atitudinal (participação, comprometimento, colaboração, autonomia) | 20% |

**Entrega final:** README.md completo + DER + Dicionário de Dados em HTML (com exceção dos cursos GTI) anexado no repositório GitHub do grupo.