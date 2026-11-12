# Acessibilidade e Internacionalização

## 1. Visão geral

O Quiz incorpora recursos de acessibilidade para tornar a experiência de utilização mais flexível e inclusiva.

As funcionalidades estão distribuídas entre recursos visuais, leitura de conteúdo e suporte a diferentes idiomas.

## 2. Recursos visuais

A aplicação disponibiliza um modo de alto contraste, permitindo modificar a apresentação visual da interface para melhorar a distinção entre elementos.

O recurso é controlado por meio de interações na própria interface.

## 3. Leitura de conteúdo

O sistema utiliza a Web Speech API do navegador, por meio de `speechSynthesis` e `SpeechSynthesisUtterance`.

Entre os recursos implementados estão:
- Leitura de textos.
- Controle de reprodução.
- Pausa e retomada.
- Interrupção da leitura.

## 4. Integração com VLibras

A aplicação incorpora o VLibras como recurso complementar de acessibilidade, oferecendo suporte à tradução de conteúdos para Libras.

## 5. Internacionalização

O VIA disponibiliza interfaces em português e espanhol.

A tradução contempla textos, perguntas, alternativas e elementos dinâmicos do questionário.

A implementação permite atender participantes que utilizam diferentes idiomas sem exigir aplicações separadas.

## 6. Considerações

A combinação de recursos visuais, leitura automatizada e integração com ferramentas de acessibilidade amplia as possibilidades de interação com o sistema.

Esses recursos representam decisões de desenvolvimento voltadas à inclusão e à experiência do usuário.

A presença dessas funcionalidades não significa, por si só, conformidade integral com padrões de acessibilidade. Uma evolução possível é realizar testes específicos com leitores de tela, navegação por teclado e ferramentas de avaliação de acessibilidade.
