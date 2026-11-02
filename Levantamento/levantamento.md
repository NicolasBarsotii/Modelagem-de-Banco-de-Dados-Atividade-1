# Levantamento de Requisitos — MAXfood

**Organização:** Lanchonete MAXfood
**Local:** UNICID — Universidade Cidade de São Paulo, Campus Tatuapé.
**Responsável Entrevistado:** Rafael Novais (Proprietário/Gerente)
**Data da Entrevista:** (Colocar a data em que vocês foram lá)
**Integrantes do Grupo Presentes:** (Colocar o nome de quem foi)

---

## 1. Contexto e Objetivo
O presente documento visa registrar o levantamento de campo realizado na lanchonete MAXfood. O objetivo foi compreender a rotina operacional, os processos de negócio, os volumes de atendimento e as principais dificuldades enfrentadas pela gestão, a fim de embasar a modelagem do banco de dados do futuro sistema da organização.

---

## 2. Observação Presencial vs. Relato do Entrevistado

Durante a visita, o grupo pôde observar a dinâmica real da lanchonete. O professor destaca que a observação muitas vezes difere do relato. Abaixo, os principais pontos notados:

*   **Controle de Estoque:** O entrevistado informou que "controla o estoque para não faltar". No entanto, **observou-se** que o controle é feito visualmente, olhando as geladeiras e o depósito, sem nenhum registro formal ou planilha diária de entrada e saída.
*   **Pedidos por WhatsApp:** O dono relatou que recebe muitos pedidos por WhatsApp. Na prática, **observou-se** que o atendente anota os pedidos em um caderno de papel e, em seguida, dita em voz alta para a cozinha. Não há integração com nenhum sistema.
*   **Falta de Bebidas:** O entrevistado citou que sofre com a falta de bebidas. **Verificou-se** in loco que a geladeira de amostra (visível para o cliente) estava com poucas unidades de refrigerante, enquanto o estoque no depósito interno não é conferido com frequência.

---

## 3. Processos de Negócio Levantados

O levantamento mapeou os seguintes processos executados na MAXfood:

1.  **Atendimento e Vendas:** Ocorre no balcão (presencial), via WhatsApp ou por telefone. O cliente escolhe os itens, que são repassados para a cozinha.
2.  **Combos e Prato do Dia:** A lanchonete trabalha com combos fixos (ex: X-Burger + Batata + Refri) e oferta um "Prato do Dia" que muda diariamente e tem preço promocional.
3.  **Regras Específicas de Montagem:** Refeições permitem a escolha de até 3 acompanhamentos. Batatas e sanduíches permitem adicionar coberturas (bacon, cheddar, etc.).
4.  **Descontos:** Aplicação de desconto fixo de R$ 2,00 para alunos/funcionários da UNICID, mediante apresentação de crachá ou app.
5.  **Pagamento:** Aceita-se débito, crédito, Pix e dinheiro. A venda fiada (pendente) é rara e ocorre apenas para clientes amigos do dono, com autorização prévia.
6.  **Controle de Estoque e Compras:** O estoque é dividido entre "Amostra" (vitrine/geladeira) e "Interno" (depósito). Quando o estoque baixa, o dono entra em contato com fornecedores por telefone/WhatsApp para repor.
7.  **Perdas e Fechamento:** Há registros de perdas de produtos perecíveis (validade vencida) e a necessidade de fechar o caixa diariamente conferindo as formas de pagamento.

---

## 4. Volumes e Números da Operação

Para justificar o dimensionamento do banco de dados e a massa de testes, os seguintes números foram levantados:

*   **Funcionários:** 2 (um no atendimento e um na cozinha).
*   **Horário de Funcionamento:** Das 10h às 22h.
*   **Volume de Clientes:** Média de 45 a 50 clientes por dia, chegando a 60 em dias de pico.
*   **Estimativa de Pedidos:** Cerca de 1.200 a 1.500 pedidos por mês.

---

## 5. Problemas Identificados (Crise Operacional)

*   **P1 (Ruptura de Estoque):** Falta de controle sistemático gera falta de insumos, principalmente refrigerantes e bebidas.
*   **P2 (Desorganização de Pedidos):** Anotações manuais em papel para pedidos de WhatsApp/telefone geram riscos de perda de informações e erros na cozinha.
*   **P3 (Perdas de Perecíveis):** Prejuízos eventuais com alimentos que não foram salvos e venceram, pois não há controle de validade.
*   **P4 (Fechamento de Caixa Manual):** Dificuldade em consolidar as diferentes formas de pagamento ao final do dia, pois não há um relatório automatizado.

---

## 6. Regras de Negócio Confirmadas

*   **RN01:** Desconto de R$ 2,00 para funcionários da UNICID, exigindo comprovação.
*   **RN02:** O prato do dia é sempre um item do cardápio e muda diariamente.
*   **RN03:** Formas de pagamento: Débito, Crédito, Pix e Dinheiro.
*   **RN04:** Fiado só com autorização do dono (status pendente no sistema).
*   **RN05:** Reposição antecipada quando o estoque atingir o mínimo.
*   **RN06:** Contagem diária de estoque.
*   **RN07:** Separação entre estoque de amostra (visível) e estoque interno (depósito).
*   **RN08:** Até 3 acompanhamentos por refeição; coberturas apenas para batatas e sanduíches.

---

## 7. Conclusão do Levantamento

A MAXfood é uma operação de pequeno porte, mas com um fluxo de vendas considerável. A ausência de um sistema informatizado faz com que o dono perca tempo com controles manuais e sofra com problemas de estoque e perdas. O levantamento confirma a necessidade de um banco de dados que integre desde a entrada de mercadorias (compras) até a venda final e o fechamento de caixa, resolvendo os problemas P1 a P4 listados acima.