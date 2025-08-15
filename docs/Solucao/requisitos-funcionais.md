---
sidebar_position: 1
title: Requisitos Funcionais
---


# Requisitos Funcionais 

&emsp; Segundo Sommerville, Sawyer (1997), Pressman e Maxim (2021), a Engenharia de Requisitos se trata da elicitação de funcionalidades e restrições que uma solução deve atender, refletindo as necessidades e expectativas de stakeholders. Esses requisitos são divididos em funcionais, que especificam as ações que sistema ou dispositivo deve realizar, e não funcionais, que determinam suas limitações de escopo, como desempenho, design, segurança e usabilidade. Requisitos são conceitos essenciais para o desenvolvimento de tecnologias e devem ser analisados com cuidado, conciliando as necessidades dos clientes e as limitações técnicas, de forma a se desenvolver sistemas de qualidade, confiáveis e eficientes.  

| RF\# | Descrição | Regra de Negócio |
| :---- | :---- | :---- |
| **RF001** | O sistema deve apresentar um avatar animado que pode ser ativado ou desativado pelo usuário. | O avatar deve estar desativado por padrão para não ser intrusivo. A preferência do usuário (ativado/desativado) deve ser salva e mantida entre as sessões. |
| **RF002** | O avatar deve guiar o usuário ao acessar uma nova seção pela primeira vez. | A explicação inicial de uma seção só deve ocorrer uma única vez. O avatar deve destacar visualmente os elementos da tela sobre os quais está falando. |
| **RF003** | O usuário deve poder solicitar ajuda do avatar a qualquer momento. | Um ícone flutuante e discreto do avatar deve estar presente em todas as telas (quando ativado), permitindo que o usuário peça ajuda contextual sob demanda. |
| **RF004** | O sistema deve permitir a configuração de acessibilidade (fonte e contraste). | As configurações de acessibilidade devem ser aplicadas em toda a aplicação e demonstradas em tempo real pelo avatar conforme o usuário as ajusta. |
| **RF005** | O sistema deve solicitar o consentimento do usuário para usar seus dados para recomendações. | O consentimento deve ser explícito (opt-in) e pode ser revogado a qualquer momento pelo usuário na área de configurações de privacidade, conforme a LGPD. |
| **RF006** | O sistema deve analisar o perfil do cliente para identificar seu momento de vida e perfil de risco. | A análise deve ser processada internamente, usando dados transacionais e cadastrais autorizados, para classificar o cliente em perfis pré-definidos. |
| **RF007** | O sistema deve apresentar uma seção de recomendações personalizadas. | As sugestões devem ser limitadas a um máximo de 3 recomendações ativas para evitar sobrecarga de informação e facilitar a tomada de decisão. |
| **RF008** | Cada recomendação deve ser acompanhada de uma explicação curta e objetiva. | A justificativa da recomendação deve conectar diretamente o produto a um objetivo ou perfil do cliente (ex: "Para proteger sua família" ou "Para fazer seu dinheiro render com segurança"). |
| **RF009** | O sistema não deve exibir dados que permitam a identificação de outros clientes. | Nenhuma informação pessoal identificável (PII) de outros clientes pode ser usada ou exibida. A regra é a anonimização total dos dados na origem. |
| **RF010** | O sistema deve conter uma seção "Rádio Itaú" com uma lista de faixas de áudio. | A "Rádio Itaú" deve funcionar como um podcast que será atualizado diariamente pela manhã com as principais notícias do mercado financeiro. |
| **RF011** | As faixas de áudio devem ter no máximo 1 minuto e usar linguagem clara. | O conteúdo deve ser produzido em formato de "pílulas de conhecimento", com roteiros que evitem jargões financeiros para garantir a fácil compreensão pelo público-alvo. |
| **RF012** | O sistema deve notificar o usuário sobre transações suspeitas. | A notificação deve ser enviada em tempo real, no momento da tentativa da transação, para permitir uma ação rápida do usuário. |
| **RF013** | O painel deve exibir e destacar transações suspeitas. | As transações suspeitas devem ter um destaque visual claro (ex: cor vermelha, ícone de alerta) na lista de transações para fácil identificação. |
| **RF014** | O usuário deve ter um botão de "Bloqueio Emergencial" visível no painel. | O botão deve ser de fácil acesso na tela principal ou no painel antifraude, permitindo o bloqueio com um único toque seguido de confirmação. |
| **RF015** | O sistema deve exigir uma confirmação para o bloqueio emergencial. | Para evitar acionamentos acidentais, o sistema deve solicitar uma segunda confirmação (senha, biometria ou face id) antes de executar o bloqueio da conta e cartões. |
| **RF016** | O sistema deve ter uma seção "Aprenda com vídeos" com rolagem vertical. | A interface deve ser intuitiva e familiar, facilitando a navegação e o consumo do conteúdo em vídeo. |
| **RF017** | Os vídeos devem possuir uma duração de no máximo 40 segundos e com linguagem clara. | O formato de vídeo curto e dinâmico visa capturar a atenção e transmitir a informação de forma rápida e eficiente. |
| **RF018** | Os vídeos devem possuir legendas claras e ativadas por padrão. | As legendas garantem a acessibilidade para deficientes auditivos e facilitam a compreensão em ambientes barulhentos ou situações onde o áudio não pode ser reproduzido. |
| **RF019** | O sistema deve permitir que o usuário curta e compartilhe os vídeos. | A funcionalidade de compartilhamento deve gerar um link para o vídeo, permitindo que o usuário o envie para familiares e amigos, ampliando o alcance da educação financeira. |

&emsp; Através da elaboração de Requisitos Funcionais e suas regras de negócio, é possível se delimitar as atuações esperadas do sistema de recomendação, o que possibilita transparência e alinhamento de expectativas no trabalho, bem como facilita o gerenciamento de escopo.