# Painel Administrativo e Exportação de Relatórios

## 1. Visão geral

O Quiz possui uma interface administrativa destinada à consulta dos resultados e ao acompanhamento dos indicadores de participação.

O painel utiliza dados armazenados no Cloud Firestore e disponibiliza recursos de visualização e exportação.

## 2. Autenticação e acesso

O acesso ao painel é protegido pelo Firebase Authentication.

Após a autenticação, o sistema verifica a custom claim `admin` para determinar se o usuário possui autorização administrativa.

As regras do Firestore também restringem a leitura dos registros a usuários autenticados com essa permissão.

## 3. Indicadores

O painel apresenta informações consolidadas sobre:
- Quantidade de participantes.
- Pontuação média.
- Maior pontuação registrada.

Esses indicadores oferecem uma visão geral dos resultados armazenados.

## 4. Ranking

Os participantes são organizados por pontuação em ordem decrescente.

Em caso de pontuações iguais, o código utiliza o nome como critério adicional de ordenação.

O ranking facilita a consulta e a comparação dos resultados.

## 5. Visualização de dados

O projeto utiliza Chart.js para construir gráficos que complementam os indicadores administrativos.

As visualizações incluem distribuições relacionadas às unidades, áreas e faixas de pontuação.

## 6. Exportação XLSX

A exportação é implementada com a biblioteca ExcelJS.

O arquivo gerado possui três planilhas:

| Planilha | Conteúdo |
|---|---|
| `Resultados` | Dados dos participantes |
| `Ranking` | Participantes organizados por pontuação |
| `Resumo` | Indicadores e visualizações consolidadas |

Os gráficos produzidos com Chart.js são incorporados ao relatório como imagens.

## 7. Benefícios

A exportação permite consultar e analisar os resultados fora da aplicação, além de facilitar o compartilhamento dos dados com pessoas autorizadas.

A divisão em três planilhas organiza as informações em diferentes níveis de análise, desde os registros individuais até os indicadores consolidados.
