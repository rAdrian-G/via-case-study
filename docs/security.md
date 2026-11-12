# Segurança e Controle de Acesso

## 1. Visão geral

O VIA utiliza Firebase Authentication e regras de segurança do Cloud Firestore para controlar o acesso aos dados.

A aplicação possui dois contextos de utilização: participação pública no questionário e acesso restrito à interface administrativa.

## 2. Autenticação administrativa

A interface administrativa utiliza autenticação por e-mail e senha, por meio da função `signInWithEmailAndPassword()`.

Após a autenticação, o sistema solicita o resultado do token de autenticação e verifica a presença da custom claim:

`admin: true`

Caso a permissão não esteja presente, o usuário não recebe acesso à interface administrativa e é desconectado.

## 3. Regras do Firestore

As regras da coleção `players` estabelecem condições distintas para leitura e criação.

### Criação de registros

A criação é permitida somente quando:
- O registro respeita o período de funcionamento definido.
- Todos os campos obrigatórios estão presentes.
- Não existem campos adicionais.
- Os valores respeitam os tipos e limites definidos.
- O identificador do questionário corresponde à versão esperada.
- A pontuação respeita os limites estabelecidos.

### Leitura de registros

A leitura é permitida somente quando o usuário está autenticado e possui a custom claim `admin` com valor `true`.

### Atualização e exclusão

As regras fornecidas não permitem atualização ou exclusão dos documentos da coleção.

## 4. Integridade dos dados

As regras de validação ajudam a impedir registros com estrutura inválida ou campos inesperados.

Entretanto, a pontuação é enviada pelo cliente e validada apenas por tipo, intervalo e múltiplo permitido. Isso não comprova que a pontuação foi calculada corretamente pelo questionário.

Uma evolução possível seria validar o resultado no servidor, por meio de uma Cloud Function ou outro mecanismo confiável.

## 5. Pontos de atenção identificados na revisão estática

- **Unicidade:** as regras analisadas não garantem matrícula única.
- **Pontuação:** a validação atual não impede que um cliente envie uma pontuação dentro do intervalo permitido sem seguir a lógica real do questionário.
- **Renderização:** a tabela administrativa utiliza `innerHTML` com dados recuperados do banco. É recomendável utilizar `textContent` para inserir valores fornecidos por usuários e reduzir o risco de XSS.
- **Autenticação e consulta:** a rotina de carregamento dos registros merece uma revisão de sequência para garantir que a consulta ocorra após a restauração e validação da sessão administrativa.
- **Credenciais e configuração:** arquivos públicos não devem conter credenciais privadas, dados internos ou identificadores de projetos que não tenham autorização para divulgação.

## 6. Conclusão

A aplicação possui uma estrutura de controle de acesso baseada nos serviços do Firebase, com separação entre autenticação administrativa e regras de leitura dos dados.

A revisão também identificou oportunidades de evolução relacionadas à integridade da pontuação, unicidade de registros e segurança da renderização dos dados.
