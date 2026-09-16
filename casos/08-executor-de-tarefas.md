# Caso 08 — Executor de tarefas com dependências

Queremos conhecer seu jeito de resolver problemas. Neste desafio, você vai construir uma solução pequena, mostrar como ela funciona e conversar conosco sobre as decisões que tomou.

## O desafio

Um processo de preparação de dados tem tarefas que só podem começar depois de outras. Crie um executor determinístico que respeite dependências e continue executando trabalho independente quando houver falhas.

Pode ser um serviço local, biblioteca, CLI ou visualizador de execução. As ações devem ser funções simuladas, sem executar comandos arbitrários do sistema.

## Como deve funcionar

Cada tarefa tem um identificador, uma lista de dependências e uma ação simulada. Escolha uma maneira simples de configurar ações que dão certo ou falham, sem executar comandos do sistema.

Confira o plano inteiro antes de começar. Uma tarefa inválida, dependência inexistente, dependência de si mesma ou ciclo deve impedir qualquer execução, inclusive de tarefas independentes. Um plano vazio é válido.

Uma tarefa só pode começar depois que todas as suas dependências terminarem com sucesso. Execute uma por vez. Sempre que houver mais de uma pronta, escolha a primeira pela ordem crescente dos identificadores, inclusive quando novas tarefas ficarem prontas durante o processo.

Se a ação der certo, marque a tarefa como `sucesso`. Se sinalizar erro ou lançar uma exceção, marque como `falha` e registre um motivo útil. Essa falha não deve encerrar o executor.

As tarefas que dependem de uma falha, diretamente ou por outras tarefas, ficam `bloqueadas` e não executam suas ações. As tarefas independentes continuam. Cada ação roda no máximo uma vez por execução do plano.

Ao final, mostre a ordem das ações que realmente rodaram e o estado de cada tarefa. Para uma tarefa bloqueada, indique ao menos uma dependência direta que falhou ou ficou bloqueada. Não inclua tarefas bloqueadas na lista de ações executadas.

Uma nova execução começa do zero, sem reaproveitar resultados anteriores. Não precisa implementar tentativas automáticas, agendamento por horário, paralelismo, armazenamento em disco ou execução distribuída.

## Um exemplo

Monte este plano:

| Tarefa | Depende de | Ação simulada |
|---|---|---|
| A | Ninguém | Sucesso |
| B | A | Falha |
| C | A | Sucesso |
| D | B e C | Sucesso |
| E | Ninguém | Sucesso |

As ações devem rodar na ordem A, B, C, E. A, C e E terminam com sucesso, enquanto B falha e deixa D bloqueada. Embora sua ação esteja configurada para dar certo, D não chega a executá-la.

Em outro plano, se X depender de Y e Y depender de X, o plano inteiro deve ser recusado antes de qualquer ação.

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
