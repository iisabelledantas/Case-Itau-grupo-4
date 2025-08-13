---
sidebar_position: 2
title: Arquitetura
---

&nbsp;&nbsp;&nbsp;&nbsp;Esta seção apresenta a arquitetura proposta da solução, incluindo sugestões para a organização do sistema, seus componentes e tecnologias recomendadas. O diagrama a seguir ilustra como pode ocorrer a comunicação entre as diferentes camadas, enquanto o texto subsequente descreve o papel de cada componente e aponta possíveis tecnologias a serem utilizadas.


Colocar imagem do diagrama


## Aplicativo Mobile Acessível
- **Componentes Principais**:
  - Interface Simplificada
  - Controles de Acessibilidade (fonte, contraste, voz)
  - Navegação por gestos simples
  - Modo tutorial interativo

- **Funcionalidades Específicas**:
    - **Rádio Itaú**: Podcast com temas específicos voltados para o público idoso
    - **Vídeos Educativos**: Reprodução de vídeos curtos sobre investimentos, serviços do Itaú, uso do aplicativo, dicas para evitar fraudes e golpes
    - **Painel Anti-Fraude**: Tela com alertas sobre fraudes
    - **Chat com Avatar**: Avatar que ajudará o usuário com as dúvidas dele acerca dos serviços oferecidos pelo Itaú e com o uso do app

## API Gateway
- **Responsabilidades**:
  - Autenticação e autorização
  - Rate limiting
  - Roteamento de requisições
  - Logs de auditoria

## Módulo de Segurança Anti-Fraude
- **Componentes**:
  - Análise comportamental (horários, localização, padrões)
  - Validação biométrica (voz, digital)
  - Score de risco em tempo real
  - Sistema de alertas multicamadas

## Camada de Microsserviços

### Serviço de Perfil do Cliente Senior
- **Funcionalidades**:
  - Gestão de preferências de acessibilidade
  - Histórico de interações
  - Configurações de privacidade LGPD
  - Perfil de risco atualizado

### Serviço de Recomendações Inteligentes
**Modelos de Recomendação**:

1. **Modelo Demográfico**:
   - Características: idade, aposentadoria, patrimônio
   - Possível algoritmo: Clustering K-means para segmentação
   - Features: faixa etária, tempo como cliente, valor em conta, localidade

2. **Modelo de Bolha Social**:
   - Filtragem colaborativa baseada em similaridade
   - Privacy-preserving: dados anonimizados e agregados
   - Comparação com peers da mesma região/faixa etária

3. **Modelo de Histórico Pessoal**:
   - Análise de padrões de investimento anteriores
   - Possível algoritmo: Sequential Pattern Mining

4. **Modelo de Momento de Vida**:
   - Regras baseadas em marcos (aposentadoria, planejamento sucessório)
   - Árvore de decisão adaptada para seniores
   - Produtos relevantes: previdência, seguros, planejamento patrimonial

### Serviço de Conteúdo Educacional
- **Funcionalidades**:
  - Curadoria de conteúdo por perfil
  - Geração de reels personalizados
  - Sistema de progressão em letramento financeiro
  - Integração com Rádio Itaú

## Dados e Armazenamento

#### **Data Lake - Conformidade LGPD**
- **Tecnologia**: AWS S3 com Amazon Lake Formation
- **Estrutura**:
  - **Raw Zone**: Dados brutos com consentimento explícito
  - **Processed Zone**: Dados processados e anonimizados
  - **Curated Zone**: Datasets para modelos de ML

#### **Bancos de Dados**:
- **PostgreSQL**: Dados transacionais e de perfil
- **Redis**: Cache de sessões e recomendações
- **Neo4j**: Grafo de relacionamentos da bolha social (anonimizados)
- **Amazon DynamoDB**: Logs de auditoria e conformidade

### **Sistema de Consentimento LGPD**
- **Funcionalidades**:
  - Rastreamento granular de consentimentos
  - Versionamento de termos de uso
  - APIs para exercício de direitos (portabilidade, exclusão)
  - Dashboard de transparência para o cliente

## Camada de Inteligência e Analytics

### Pipeline de Machine Learning
- **Fluxo**:
  1. Coleta dados com consentimento
  2. Processamento
  3. Feature Engineering (Criação de variáveis para modelos)
  4. Treinamento (atualização automática dos modelos)
  5. Deploy (versionamento e A/B testing)

### Real-time Analytics
- **Funcionalidades**:
  - Stream processing para detecção de fraudes
  - Análise de comportamento em tempo real
  - Triggers para recomendações contextuais

## Open Banking Hub
- **APIs Expostas**:
  - Dados de conta (com consentimento)
  - Histórico de transações
  - Produtos contratados
- **APIs Consumidas**:
  - Dados de outras instituições (consolidação financeira)
  - Bureau de crédito para análise de risco

&nbsp;&nbsp;&nbsp;&nbsp;Dessa forma, a arquitetura proposta integra acessibilidade, segurança e conformidade regulatória para criar uma experiência digital inclusiva para o público sênior. Assim, ao combinar tecnologias, microsserviços e governança de dados, a solução garante não apenas facilidade de uso, mas também proteção contra fraudes e personalização de serviços. Dessa forma, o ecossistema apresentado está preparado para evoluir continuamente acompanhando as necessidades dos usuários.