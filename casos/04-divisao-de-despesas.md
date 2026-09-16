# Caso 04 — Divisão de despesas de um grupo

Queremos conhecer seu jeito de resolver problemas. Neste desafio, você vai construir uma solução pequena, mostrar como ela funciona e conversar conosco sobre as decisões que tomou.

## O desafio

Um grupo divide despesas e quer saber quanto cada pessoa deve receber ou pagar. Crie um livro de despesas com rateio exato e possibilidade de estorno.

Você pode apresentar a solução como app, interface web, serviço, biblioteca ou aplicação de terminal.

## Como deve funcionar

Comece com uma lista fixa de participantes. Cada despesa tem um identificador, um pagador, um valor positivo em centavos inteiros e os participantes que vão dividi-la. O pagador pode estar fora desse grupo.

Divida o valor igualmente entre os beneficiários, sempre em centavos inteiros. Se sobrarem centavos, distribua um por pessoa, seguindo a ordem crescente dos identificadores. Assim, mudar a ordem da lista recebida não muda o resultado do rateio.

Quem pagou recebe um crédito pelo valor total. Cada beneficiário recebe um débito pela sua parte. O saldo indica quanto a pessoa tem a receber, quando positivo, ou a pagar, quando negativo. A soma dos saldos do grupo deve ser sempre zero.

Estornar uma despesa desfaz exatamente seu efeito nos saldos. Se ela já estiver estornada, retorne `ja_estornada` sem mudar nada. Se não existir, informe o erro. O identificador de uma despesa estornada não pode ser usado em outra despesa.

Mostre o rateio e a situação de cada despesa, além dos saldos de todos os participantes em ordem de identificador. Operações inválidas não mudam os saldos nem ocupam o identificador da tentativa.

Tudo pode funcionar em memória, uma operação por vez. Não precisa fazer pagamentos, calcular a menor quantidade de transferências para quitar o grupo ou lidar com moedas diferentes, juros e câmbio.

## Um exemplo

O grupo tem A, B e C. Primeiro, A paga a despesa E1, de 100 centavos, para os três. Mesmo que os beneficiários cheguem na ordem C, B, A, o rateio é A=34, B=33 e C=33.

Depois, B paga E2, de 60 centavos, para A e C. Os saldos devem evoluir assim:

| Momento | A | B | C |
|---|---|---|---|
| Após E1 | 66 | -33 | -33 |
| Após E2 | 36 | 27 | -63 |
| Após estornar E1 | -30 | 60 | -30 |

Os valores estão em centavos. Estornar E1 novamente não altera os saldos.

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
