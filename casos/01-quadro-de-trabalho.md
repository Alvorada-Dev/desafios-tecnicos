# Caso 01 — Quadro de trabalho com histórico

Queremos conhecer seu jeito de resolver problemas. Neste desafio, você vai construir uma solução pequena, mostrar como ela funciona e conversar conosco sobre as decisões que tomou.

## O desafio

Uma equipe precisa acompanhar tarefas sem perder alterações acidentais. Crie um quadro com as colunas `a_fazer`, `em_andamento` e `concluido`, limite de trabalho em andamento e opção de desfazer a última mudança.

Você pode trabalhar a interação em uma tela ou oferecer as ações por comandos ou funções.

## Como deve funcionar

Uma tarefa tem um identificador (`id`) e um título, ambos em texto. Toda tarefa nova entra em `a_fazer`.

A pessoa pode mover uma tarefa para qualquer uma das três colunas. Se a tarefa não existir ou a coluna for desconhecida, explique o erro e mantenha o quadro como estava. Mover uma tarefa para a coluna onde ela já está não muda nada.

A coluna `em_andamento` tem um limite de tarefas, configurado antes do uso. Use 2 como padrão.

A opção de desfazer volta uma criação ou movimentação por vez, começando pela última que realmente mudou o quadro. Ao desfazer, uma tarefa recém-criada é removida, enquanto uma tarefa movimentada volta à coluna anterior. O próprio desfazer não cria uma nova entrada no histórico. Quando não houver nada para desfazer, retorne `nada_a_desfazer`.

Mostre as tarefas de cada coluna em ordem crescente de identificador e indique se é possível desfazer. Deixe claro quando uma ação funcionou, falhou ou não mudou nada. Em caso de falha, preserve tanto o quadro quanto o histórico.

As ações podem acontecer uma de cada vez, com tudo em memória. Não precisa implementar login, colaboração em tempo real, exclusão, refazer ou armazenamento em disco.

## Um exemplo

Use o limite padrão de duas tarefas em andamento. Crie A, B e C em `a_fazer` e faça estas ações, na ordem:

| Ação | O que deve acontecer |
|---|---|
| Mover A para `em_andamento` | A mudança funciona. |
| Mover B para `em_andamento` | A mudança funciona e a coluna chega ao limite de duas tarefas. |
| Mover C para `em_andamento` | O limite impede a mudança e C continua em `a_fazer`. |
| Desfazer | B volta para `a_fazer`. A tentativa de mover C não entrou no histórico. |
| Mover C para `concluido` | A mudança funciona. |
| Mover C para `concluido` outra vez | Nada muda. |
| Desfazer | C volta para `a_fazer`. |

## Como organizar seu tempo

Nossa sugestão é dedicar até quatro horas à implementação, aos testes e à documentação. Se não conseguir terminar tudo nesse tempo, envie o que fez e conte o que ficou pendente. O objetivo é ter uma solução pequena que sirva de ponto de partida para nossa conversa.

## Ferramentas e uso de IA

Use a linguagem e as ferramentas com que se sente mais à vontade. A solução pode ser uma interface, API, aplicação de terminal, biblioteca com exemplo executável ou simulador. Escolha a forma que melhor combina com seu foco, seja front, mobile, back, arquitetura, algoritmos ou dados.

As regras do desafio valem para qualquer abordagem, mas você tem liberdade para decidir como organizar e apresentar a solução. Não é necessário publicar a aplicação, pagar por serviços ou usar hardware. Se depender de um serviço externo, ofereça uma forma local de demonstrar o funcionamento.

Pode usar IA, documentação e bibliotecas. Conte como essas ferramentas ajudaram, o que você aproveitou ou mudou e como conferiu o resultado. Não precisamos do histórico de conversas com a IA, pois queremos conhecer suas decisões e a maneira como você verificou o código.

## O que entregar

A entrega tem duas partes:

- **Um repositório Git com o código, os testes e a documentação da solução.** O README deve explicar como instalar o que for necessário, executar a aplicação e rodar os testes. Inclua uma demonstração que possamos reproduzir, suas principais decisões e o que ficou pendente.
- **Um vídeo de até 30 minutos explicando a solução.** Mostre a aplicação funcionando, percorra os trechos de código mais importantes e conte por que escolheu essa abordagem.

### Repositório e documentação

Crie o repositório no serviço de sua preferência. No README, informe o nome ou número do caso, o foco escolhido e quanto tempo você dedicou ao trabalho. Quem clonar o projeto deve conseguir acompanhar a demonstração com as instruções que você deixou.

Ao explicar os testes, destaque até três situações que ajudem a entender sua solução, como um valor no limite de uma regra, a interação entre duas regras ou uma entrada inválida. Conte o resultado esperado e que tipo de erro cada teste ajuda a encontrar. Você pode escrever outros testes, sem precisar atingir um percentual de cobertura.

Conte também duas decisões que tomou durante o trabalho, explicando o que queria conferir, como investigou e o que concluiu. Uma delas pode ser sobre uma sugestão da IA, se você a usou. Essas notas podem ficar no próprio README e não precisam seguir um formulário.

Use dados fictícios e deixe de fora credenciais, dados pessoais reais e código de empregadores. A quantidade de commits não conta na avaliação.

### Vídeo explicando a solução

A gravação deve nos ajudar a acompanhar seu raciocínio. Escolha um cenário diferente do exemplo deste documento, explique o resultado que espera e execute a solução para compará-lo com o que aconteceu. Mostre também um teste importante e o trecho de código que ele ajuda a conferir.

Ao percorrer o projeto, conte por que escolheu uma abordagem, que alternativa considerou e onde a solução tem limites. Se algo não funcionou, vale mostrar como investigou.

Não precisa mostrar o rosto, criar slides, editar a gravação ou repetir seu currículo. Use o tempo para explicar o trabalho, incluindo como verificou as sugestões da IA, quando houver. Se precisar de outro formato de apresentação, converse com a pessoa que acompanha seu processo.

## Como enviar

Quando estiver pronto, responda pelo mesmo canal em que recebeu o convite, compartilhando:

- O link do repositório e o hash completo do commit que devemos avaliar.
- O link do vídeo, que também pode ficar no README.
- O nome ou número do caso, o foco escolhido e o tempo aproximado utilizado.
- Alguma observação necessária para executar a solução, se houver.

O repositório pode ser privado. Nesse caso, peça à pessoa responsável os usuários que devem receber acesso de leitura. Confira também se conseguimos abrir o vídeo, sem enviar senhas ou tokens. Vamos confirmar o recebimento e o acesso aos arquivos.

O commit identifica o código entregue. Se continuar trabalhando e quiser incluir uma mudança na avaliação, basta avisar e enviar o novo hash. Você também pode corrigir links, permissões e instruções de execução depois do envio.
