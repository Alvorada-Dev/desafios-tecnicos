# Caso 03 — Planejador de rotas com bloqueios

Queremos conhecer seu jeito de resolver problemas. Neste desafio, você vai construir uma solução pequena, mostrar como ela funciona e conversar conosco sobre as decisões que tomou.

## O desafio

Uma operação precisa encontrar o trajeto de menor custo em uma malha de locais. Crie um planejador que permita bloquear conexões e recalcular o caminho.

Você pode criar uma visualização do mapa, uma biblioteca de algoritmos, uma aplicação de terminal ou uma API.

## Como deve funcionar

Represente os locais como nós de um grafo e as conexões como arestas dirigidas: uma conexão de A para B não permite, sozinha, voltar de B para A. Cada nó tem um identificador. Cada aresta tem seu próprio identificador, origem, destino e custo positivo. Podem existir ciclos e mais de uma aresta entre os mesmos nós.

Confira todos os dados antes de carregar o grafo. Um identificador repetido, custo inválido ou referência a um nó inexistente deve impedir a carga inteira. Se já houver um grafo carregado, preserve-o nesse caso. Uma carga vazia é válida. Uma carga bem-sucedida substitui o grafo anterior e deixa todas as arestas desbloqueadas.

Dada uma origem e um destino, encontre um caminho de menor custo total. Mostre os nós e as arestas percorridos, além do custo. Se houver empate, qualquer caminho mínimo serve, e você pode explicar como sua solução faz essa escolha. O custo informado deve corresponder à soma das arestas do caminho.

Se origem e destino forem o mesmo nó existente, o caminho contém só esse nó, nenhuma aresta e custo zero. Se um dos nós não existir, informe o erro. Se os dois existirem, mas não houver caminho, retorne `sem_rota`.

Permita bloquear e desbloquear uma aresta pelo identificador. Uma consulta deve considerar os bloqueios atuais, sem alterar o grafo. Repetir um bloqueio ou desbloqueio já aplicado não muda nada, enquanto um identificador inexistente gera erro. Arestas bloqueadas nunca entram na rota.

Explique como o custo de processamento cresce com o tamanho do grafo. Você pode usar uma biblioteca ou implementar o algoritmo. Não precisa oferecer cache, rotas alternativas, tráfego em tempo real ou custos negativos.

## Um exemplo

Use os nós A, B, C e D, com estas conexões:

| Aresta | Caminho | Custo |
|---|---|---|
| e1 | A → B | 2 |
| e2 | B → D | 2 |
| e3 | A → C | 1 |
| e4 | C → D | 6 |
| e5 | A → D | 9 |

A rota mais barata de A até D é A → B → D, com custo 4. Ao bloquear e2, ela passa a ser A → C → D, com custo 7. Se bloquear também e4, sobra A → D, com custo 9. Bloqueando e5 em seguida, o resultado é `sem_rota`.

Uma consulta de D até A também retorna `sem_rota`: as conexões só permitem andar no sentido indicado.

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
