# Caso 06 — Avaliador de predições e abstenções

Queremos conhecer seu jeito de resolver problemas. Neste desafio, você vai construir uma solução pequena, mostrar como ela funciona e conversar conosco sobre as decisões que tomou.

## O desafio

Uma equipe recebe resultados de um classificador e precisa entender em quais casos ele decide, erra ou se abstém. Crie uma ferramenta local de avaliação a partir de predições já calculadas.

Você pode explorar a análise de dados, a visualização dos resultados ou o cálculo das métricas a partir das predições fornecidas.

## Como deve funcionar

Configure pelo menos duas classes e um limite de confiança entre 0 e 1, inclusive. Use 0,7 como padrão. Se a configuração for inválida, informe o erro antes de processar os registros.

Cada registro tem um identificador, sua classe real e uma probabilidade para cada classe configurada. As probabilidades devem estar entre 0 e 1 e somar 1, com tolerância de 0,000001. Registros que não atendam a essas regras são inválidos.

A previsão é a classe com maior probabilidade. Em empate, escolha a primeira pela ordem crescente dos identificadores. Quando a maior probabilidade ficar abaixo do limite de confiança, retorne `abstencao`: o classificador não tomou uma decisão. Se for exatamente igual ao limite, ele pode decidir.

Confira a validade do registro antes de procurar repetições. Só o primeiro registro válido de cada identificador entra nas métricas. Uma repetição válida retorna `duplicado` e não conta, mesmo que seu conteúdo tenha mudado. Um registro inválido não ocupa o identificador. Informe os erros e continue com o restante do lote.

Mostre o resultado de cada registro e os totais de registros válidos únicos, decisões, abstenções e acertos. Monte também uma matriz de confusão apenas com as decisões: cada linha representa a classe real e cada coluna, a classe prevista.

Calcule cobertura como decisões divididas por registros válidos únicos, e acurácia das decisões como acertos divididos por decisões. Se um denominador for zero, indique que a métrica não está disponível. Permita avaliar o mesmo lote novamente com outro limite, começando o cálculo do zero. Não precisa treinar um modelo, criar um dashboard completo ou fazer calibração estatística.

## Um exemplo

Use as classes `gato` e `cao`, com limite de confiança 0,7:

| Registro | Classe real | Probabilidade de gato | Probabilidade de cao | Resultado |
|---|---|---|---|---|
| R1 | gato | 0,8 | 0,2 | Acerto. |
| R2 | cao | 0,6 | 0,4 | Abstenção. |
| R3 | cao | 0,7 | 0,3 | Erro. |
| R4 | gato | 0,8 | 0,4 | Inválido: as probabilidades somam 1,2. |

Se R1 chegar de novo com dados válidos, conte-o como duplicado. Ao final, são 3 registros válidos únicos, 2 decisões, 1 abstenção e 1 acerto. A cobertura é 2/3 e a acurácia das decisões é 1/2.

Na matriz de confusão, as células real gato/previsto gato e real cao/previsto gato têm valor 1. As demais ficam em zero.

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
