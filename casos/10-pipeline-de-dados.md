# Caso 10 — Pipeline de vendas e conciliação de pagamentos

Queremos conhecer seu jeito de resolver problemas. Neste desafio, você vai construir uma solução pequena, mostrar como ela funciona e conversar conosco sobre as decisões que tomou.

## O desafio

Uma operação de comércio eletrônico precisa consolidar seus dados de pedidos, produtos, clientes e pagamentos para acompanhar as vendas e identificar inconsistências.

Crie um pipeline em Python que extraia os arquivos abaixo, trate os dados e os carregue em PostgreSQL, permitindo responder às três perguntas de negócio por meio de SQL.

## Os dados

Use estes arquivos do Brazilian E-Commerce Public Dataset by Olist, disponível no Kaggle:

| Fonte de dados | Conteúdo |
|---|---|
| [olist_orders_dataset.csv](https://www.kaggle.com/datasets/olistbr/brazilian-ecommerce?select=olist_orders_dataset.csv) | Pedidos, status e datas. |
| [olist_order_items_dataset.csv](https://www.kaggle.com/datasets/olistbr/brazilian-ecommerce?select=olist_order_items_dataset.csv) | Itens, preços e fretes. |
| [olist_order_payments_dataset.csv](https://www.kaggle.com/datasets/olistbr/brazilian-ecommerce?select=olist_order_payments_dataset.csv) | Pagamentos. |
| [olist_customers_dataset.csv](https://www.kaggle.com/datasets/olistbr/brazilian-ecommerce?select=olist_customers_dataset.csv) | Clientes e localização. |
| [olist_products_dataset.csv](https://www.kaggle.com/datasets/olistbr/brazilian-ecommerce?select=olist_products_dataset.csv) | Produtos e categorias. |

Os links abrem cada arquivo no Kaggle. Você também pode baixar os arquivos juntos na [página da base Olist](https://www.kaggle.com/datasets/olistbr/brazilian-ecommerce). O download pode ser manual; documente como obter os arquivos e onde colocá-los para executar o pipeline.

## Como deve funcionar

O pipeline deve permitir responder:

1. **Qual é o valor de vendas e o ticket médio por mês e estado do cliente?** Considere pedidos entregues (`order_status = 'delivered'`), utilize a data da compra (`order_purchase_timestamp`) e exclua o frete. O ticket médio corresponde ao valor de vendas dividido pela quantidade de pedidos distintos.
2. **Quais são as dez categorias de produtos com maior valor de vendas em cada mês?** Considere pedidos entregues, utilize a data da compra e exclua o frete.
3. **Quais pedidos não possuem pagamentos registrados ou apresentam divergência entre o total pago e a soma dos itens com frete?** Considere todos os status e diferenças absolutas superiores a R$ 0,01. Apresente o identificador e o status do pedido, os valores comparados e o motivo da sinalização.

O valor de vendas é a soma de `price` dos itens. Para a conciliação, compare a soma de `payment_value` com a soma de `price + freight_value` de cada pedido. Os resultados devem permanecer corretos quando um pedido tiver vários itens ou vários pagamentos.

O pipeline deve poder ser executado novamente com os mesmos arquivos sem duplicar registros nem alterar os totais. Identifique e documente os problemas de qualidade encontrados, explique o tratamento adotado e registre o resultado de cada execução, incluindo quantidades processadas e eventuais falhas.

Você tem liberdade para definir a modelagem, a organização do código e a forma de executar o pipeline. Escolha a profundidade da solução conforme sua experiência e justifique as principais decisões. Se fizer sentido para sua abordagem, demonstre ou discuta como ela lidaria com maiores volumes, novas fontes, atualizações dos dados e recuperação de falhas. Diferencie o que foi implementado e validado das melhorias propostas.

Vamos considerar a correção dos resultados, a confiabilidade do processamento, a clareza da comunicação e a adequação das decisões ao problema.

## Um exemplo

Considere estes pedidos fictícios, todos comprados em janeiro de 2018 por clientes de SP:

| Pedido | Status | Categoria dos itens | Preços dos itens | Fretes dos itens | Pagamentos |
|---|---|---|---|---|---|
| A | `delivered` | Livros | R$ 60,00 e R$ 40,00 | R$ 6,00 e R$ 4,00 | R$ 70,00 e R$ 40,00 |
| B | `delivered` | Papelaria | R$ 50,00 | R$ 5,00 | R$ 54,98 |
| C | `canceled` | Livros | R$ 30,00 | R$ 3,00 | Nenhum. |

O valor de vendas de janeiro em SP é R$ 150,00 e o ticket médio é R$ 75,00. Livros aparece com R$ 100,00 em vendas e Papelaria com R$ 50,00. O pedido cancelado fica fora desses cálculos.

Na conciliação, A está correto: os pagamentos somam R$ 110,00, assim como os itens com frete. B tem uma divergência de R$ 0,02 e C deve ser sinalizado por não possuir pagamento registrado. Reexecutar o pipeline deve preservar esses resultados.

## Como organizar seu tempo

Nossa sugestão é dedicar até quatro horas à implementação, aos testes e à documentação. Se não conseguir terminar tudo nesse tempo, envie o que fez e conte o que ficou pendente. O objetivo é ter uma solução pequena que sirva de ponto de partida para nossa conversa.

Priorize o pipeline funcionando, as respostas às três perguntas e a conferência dos resultados. Use a documentação e o vídeo para explicar os limites da solução e as evoluções que considera necessárias.

## Ferramentas e uso de IA

Use Python, SQL e PostgreSQL. As bibliotecas e ferramentas de apoio ficam a seu critério. Ofereça uma forma local de executar o pipeline e consultar os resultados, sem depender de serviços pagos.

Pode usar IA, documentação e bibliotecas. Conte como essas ferramentas ajudaram, o que você aproveitou ou mudou e como conferiu o resultado. Não precisamos do histórico de conversas com a IA, pois queremos conhecer suas decisões e a maneira como você verificou o código.

Use a base pública indicada e dados fictícios nos testes. Deixe de fora credenciais, dados pessoais adicionais e código de empregadores.

## O que entregar

A entrega tem duas partes:

- **Um repositório Git com o código do pipeline, os scripts SQL, os resultados das três perguntas, os testes e a documentação da solução.** O README, escrito em inglês, deve explicar como obter os dados, preparar o ambiente, executar o pipeline, consultar os resultados e rodar os testes. Inclua suas principais decisões, os problemas de qualidade encontrados e o que ficou pendente.
- **Um vídeo de até 30 minutos, gravado em inglês, explicando a solução.** Mostre o pipeline funcionando, percorra os trechos de código e SQL mais importantes e conte por que escolheu essa abordagem.

### Repositório e documentação

Crie o repositório no serviço de sua preferência. No README, informe o nome ou número do caso, o foco escolhido e quanto tempo você dedicou ao trabalho. Quem clonar o projeto deve conseguir reproduzir a execução e os resultados com as instruções que você deixou.

Ao explicar os testes, destaque até três situações que ajudem a entender sua solução, como a repetição da carga, um pedido com vários itens e pagamentos ou uma divergência no limite de um centavo. Conte o resultado esperado e que tipo de erro cada teste ajuda a encontrar. Você pode escrever outros testes, sem precisar atingir um percentual de cobertura.

Conte também duas decisões que tomou durante o trabalho, explicando o que queria conferir, como investigou e o que concluiu. Uma delas pode ser sobre uma sugestão da IA, se você a usou. Essas notas podem ficar no próprio README e não precisam seguir um formulário.

Registre as premissas que precisou adotar, por exemplo para categorias ausentes ou empates no ranking. A quantidade de commits não conta na avaliação.

### Vídeo explicando a solução

O vídeo deve ser gravado em inglês, do início ao fim. Escolha um cenário diferente do exemplo deste documento, explique o resultado que espera e execute a solução para compará-lo com o que aconteceu. Mostre também um teste importante e o trecho de código ou SQL que ele ajuda a conferir.

Ao percorrer o projeto, conte por que escolheu uma abordagem, que alternativa considerou e onde a solução tem limites. Mostre como investigou uma inconsistência nos dados ou verificou um resultado que parecia errado.

Não precisa mostrar o rosto, criar slides, editar a gravação ou repetir seu currículo. Use o tempo para explicar o trabalho, incluindo como verificou as sugestões da IA, quando houver. Se precisar de outro formato de apresentação, converse com a pessoa que acompanha seu processo.

## Como enviar

Quando estiver pronto, responda pelo mesmo canal em que recebeu o convite, compartilhando:

- O link do repositório e o hash completo do commit que devemos avaliar.
- O link do vídeo, que também pode ficar no README.
- O nome ou número do caso, o foco escolhido e o tempo aproximado utilizado.
- Alguma observação necessária para executar a solução, se houver.

Sua solução deve ficar no seu próprio repositório, sem abrir um PR neste catálogo.

O repositório pode ser privado. Nesse caso, peça à pessoa responsável os usuários que devem receber acesso de leitura. Confira também se conseguimos abrir o vídeo, sem enviar senhas ou tokens. Vamos confirmar o recebimento e o acesso aos arquivos.

O commit identifica o código entregue. Se continuar trabalhando e quiser incluir uma mudança na avaliação, basta avisar e enviar o novo hash. Você também pode corrigir links, permissões e instruções de execução depois do envio.
