# Arquitetura do Sistema VIA

## 1. Visão geral

O VIA é uma aplicação web interativa desenvolvida para uma iniciativa corporativa de Diversidade e Inclusão. O sistema permite que participantes respondam a um questionário, recebam uma pontuação e tenham seus resultados registrados em uma base de dados centralizada.

A aplicação também possui uma interface administrativa para consulta dos participantes, visualização de indicadores e exportação de relatórios.

## 2. Tecnologias utilizadas

| Tecnologia | Aplicação no projeto |
|---|---|
| HTML5 | Estrutura das interfaces |
| CSS3 | Estilização, responsividade e acessibilidade visual |
| JavaScript | Lógica do questionário, interações e integração com serviços |
| Firebase Authentication | Autenticação administrativa |
| Cloud Firestore | Persistência dos resultados |
| Firebase Hosting | Hospedagem da aplicação |
| Chart.js | Visualização de indicadores |
| ExcelJS | Geração de planilhas XLSX |
| VLibras | Recurso de acessibilidade |

O projeto utiliza JavaScript puro, sem dependência de frameworks front-end como React, Vue ou Angular.

## 3. Organização da aplicação

O sistema é dividido em duas interfaces principais:

### Interface do participante

Responsável por:
- Coletar os dados de identificação do participante.
- Apresentar perguntas e alternativas.
- Calcular a pontuação durante a execução do questionário.
- Oferecer suporte aos idiomas disponíveis.
- Registrar os resultados no Cloud Firestore.
- Disponibilizar recursos de acessibilidade.

### Interface administrativa

Responsável por:
- Autenticar usuários administrativos.
- Verificar permissões por meio de custom claims do Firebase Authentication.
- Consultar os registros armazenados.
- Organizar os participantes por pontuação.
- Exibir indicadores gerais.
- Exportar relatórios em formato XLSX.

## 4. Fluxo arquitetural

O front-end se comunica diretamente com os serviços Firebase por meio do SDK JavaScript.

**Fluxo do participante:**

1. O participante acessa a aplicação.
2. Preenche os dados solicitados.
3. Responde às perguntas apresentadas.
4. A aplicação calcula a pontuação.
5. Os dados são enviados ao Cloud Firestore.
6. O resultado fica disponível para consulta administrativa.

**Fluxo administrativo:**

1. O administrador acessa a interface restrita.
2. Realiza a autenticação.
3. O sistema verifica a custom claim `admin`.
4. Com a permissão validada, os registros são consultados.
5. Os dados são organizados e apresentados em indicadores e ranking.
6. O administrador pode exportar os resultados.

## 5. Modelo arquitetural

A solução utiliza uma arquitetura web client-side integrada a serviços gerenciados em nuvem.

O Firebase atua como Backend as a Service (BaaS), oferecendo recursos de autenticação, banco de dados e hospedagem sem a necessidade de manter um servidor próprio para essas funcionalidades.

## 6. Considerações técnicas

A separação entre a interface do participante e a interface administrativa permite organizar responsabilidades distintas dentro da aplicação.

A utilização de serviços gerenciados reduz a necessidade de infraestrutura própria e permite que o sistema seja disponibilizado por meio de hospedagem web.
