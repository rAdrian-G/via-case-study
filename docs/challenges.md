# Desafios Técnicos e Decisões de Desenvolvimento

## 1. Desenvolvimento sem frameworks

O Quiz, por escolha, foi desenvolvido utilizando HTML5, CSS3 e JavaScript puro, sem frameworks front-end.

Essa escolha permitiu implementar diretamente a estrutura das interfaces, manipulação do DOM, lógica do questionário e integração com o Firebase.

Também tornou necessário organizar manualmente as responsabilidades do código, especialmente entre a interface do participante, a lógica do questionário e o painel administrativo.

## 2. Seleção dinâmica de perguntas

O questionário possui um banco de 20 perguntas, das quais 5 são selecionadas aleatoriamente a cada participação.

Cada pergunta apresenta quatro alternativas, com uma resposta correta.

A pontuação é calculada no front-end, atribuindo 100 pontos por resposta correta, totalizando até 500 pontos por participação.

Essa abordagem aumenta a variedade das experiências sem exigir a criação de diferentes versões fixas do questionário.

## 3. Internacionalização

A aplicação oferece conteúdo em português e espanhol.

A implementação envolve a tradução de textos, perguntas, alternativas e elementos da interface, além da adaptação de informações exibidas dinamicamente.

## 4. Integração com serviços em nuvem

A integração com o Firebase permite persistir os resultados e disponibilizá-los para consulta administrativa.

A utilização do Firestore exigiu a definição de uma estrutura de documentos e regras para validação e controle de acesso.

## 5. Painel administrativo e relatórios

O painel reúne informações dos participantes, ranking e indicadores gerais.

A exportação de dados utiliza ExcelJS, enquanto Chart.js é utilizado para gerar visualizações que complementam os relatórios.

## 6. Evolução técnica

O desenvolvimento passou por diferentes versões, incluindo mudanças na quantidade de perguntas disponíveis, seleção aleatória, internacionalização e aprimoramento da exportação de resultados.

Essas alterações foram registradas no changelog do projeto.
