# Caso 07 — Monitor de sensores com histerese

Queremos conhecer seu jeito de resolver problemas. Neste desafio, você vai construir uma solução pequena, mostrar como ela funciona e conversar conosco sobre as decisões que tomou.

## O desafio

Um equipamento precisa sinalizar aquecimento sem alternar o alerta a cada pequena oscilação. Crie um monitor com histerese, detecção de leitura antiga e indicação de sensor sem atualização.

Você pode simular o equipamento no computador, criar um painel ou oferecer uma biblioteca ou aplicação de terminal.

## Como deve funcionar

Configure os limites `baixo` e `alto`, com `baixo < alto`, o tempo de espera (`timeout`) e a capacidade de sensores. Use nos exemplos baixo=40, alto=60, timeout=5 e capacidade=2. Confira a configuração antes de receber leituras.

Cada leitura traz o identificador do sensor, o instante da medição (`timestamp`) e um valor. Cada sensor começa no estado normal. Ele passa para alta quando o valor chega a `alto` ou o ultrapassa. Só volta ao normal quando o valor chega a `baixo` ou fica abaixo dele. Entre os limites, mantém o estado anterior. Esse intervalo evita que pequenas oscilações façam o alerta ligar e desligar sem parar.

Depois de conferir os campos, aceite a leitura apenas se seu timestamp for maior que o último aceito daquele sensor. Se for igual ou menor, retorne `ignorada` sem mudar nada. Uma leitura inválida também não altera dados nem cria um sensor.

Registre uma transição apenas quando o estado mudar entre normal e alta. A primeira leitura já pode causar uma transição para alta. Os sensores são independentes. Quando a capacidade estiver cheia, recuse sensores novos sem remover os existentes.

Permita consultar um resumo passando o instante `agora`, que não pode ser anterior à leitura mais recente. Um sensor fica `sem_atualizacao` quando `agora - ultimo_timestamp >= timeout`. Esse aviso é separado de normal/alta: não gera transição nem apaga o histórico. A consulta não muda dados e retorna vazio se ainda não houver sensores.

Mostre o resultado de cada leitura, as transições e um resumo por sensor com último valor, timestamp, normal/alta e aviso de falta de atualização. Não é preciso guardar todas as leituras, usar hardware real, salvar em disco ou garantir prazos rígidos de execução.

## Um exemplo

Com baixo=40 e alto=60, envie estas leituras do sensor S:

| Instante | Valor | Resultado |
|---|---|---|
| 1 | 59 | Continua normal. |
| 2 | 60 | Passa para alta: primeira transição. |
| 3 | 50 | Continua alta. |
| 4 | 40 | Volta ao normal: segunda transição. |
| 4 | 90 | A leitura é ignorada e o último valor continua sendo 40. |

Com timeout=5, uma consulta no instante 8 ainda mostra S atualizado. No instante 9, mostra `sem_atualizacao`.

Uma nova leitura no instante 10, com valor 70, leva S para alta e gera a terceira transição. Uma consulta nesse mesmo instante já mostra o sensor atualizado.

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
