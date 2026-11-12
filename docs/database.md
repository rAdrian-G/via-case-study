# Modelagem e Persistência de Dados

## 1. Banco de dados

O VIA utiliza o Cloud Firestore, banco de dados NoSQL baseado em documentos e coleções, para armazenar os resultados do questionário.

A coleção principal utilizada pela aplicação é:

`players`

## 2. Estrutura dos documentos

Cada documento representa um registro de participação no questionário.

| Campo | Tipo | Descrição |
|---|---|---|
| `nome` | String | Nome informado pelo participante |
| `matricula` | String | Identificador funcional informado |
| `unidade` | String | Unidade selecionada |
| `area` | String | Área de atuação |
| `pontuacao` | Number | Pontuação obtida |
| `quiz` | String | Identificador da versão do questionário |
| `data` | Timestamp | Data e horário do registro |

O identificador do documento é gerado automaticamente pelo Firestore por meio de `addDoc()`.

## 3. Persistência

A função `savePlayer()` é responsável por enviar os dados ao banco.

O registro utiliza `serverTimestamp()` para atribuir o horário de gravação no servidor, evitando depender exclusivamente do relógio local do navegador.

Os registros são identificados pelo campo `quiz`, que permite associar os resultados a uma versão específica do questionário.

## 4. Validação dos dados

As regras de segurança do Firestore verificam:
- Presença dos campos obrigatórios.
- Ausência de campos não autorizados.
- Tipos de dados esperados.
- Limites de tamanho dos campos textuais.
- Identificador esperado do questionário.
- Formato e intervalo permitido da pontuação.
- Horário limite para criação de registros.

## 5. Consulta dos dados

A interface administrativa utiliza `getDocs()` para recuperar os documentos da coleção `players`.

Após a consulta, os dados são organizados em memória para:
- Ordenação por pontuação.
- Construção do ranking.
- Cálculo de indicadores.
- Geração dos relatórios exportáveis.

## 6. Observação sobre unicidade da matrícula

Durante a utilização do sistema, foi relatado que a aplicação impedia o registro duplicado de matrículas.

Entretanto, na versão do código analisada, a função de persistência utiliza `addDoc()`, que gera um identificador automático para cada documento. As regras fornecidas também validam a matrícula como campo textual, mas não implementam uma restrição explícita de unicidade.

Portanto, o comportamento observado em operação deve ser distinguido da garantia de unicidade implementada no banco de dados.

Uma implementação futura poderia utilizar uma operação transacional ou uma estrutura de documentos com identificadores determinísticos, acompanhada de regras que impeçam a criação duplicada.
