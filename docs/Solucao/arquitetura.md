---
sidebar_position: 2
title: Arquitetura
---

import useBaseUrl from '@docusaurus/useBaseUrl';

&nbsp;&nbsp;&nbsp;&nbsp;Esta seção apresenta a arquitetura proposta da solução, incluindo sugestões para a organização do sistema, seus componentes e tecnologias recomendadas. Desse modo, os diagramas ilustram como pode ocorrer a comunicação entre as diferentes camadas, enquanto o texto descreve o papel de cada componente e aponta possíveis tecnologias a serem utilizadas.

&nbsp;&nbsp;&nbsp;&nbsp;Nesse sentido, a Figura 1 abaixo representa o diagrama da arquitetura da solução.

<div align="center">
  <sup>Figura 1 - Diagrama de Arquitetura</sup>
  <br />
  <img src={useBaseUrl('/img/arquitetura.png')} alt="Diagrama de Arquitetura" style={{maxWidth: "800px"}} />
  <br />
  <sup>Fonte: Material produzido pelos autores (2025).</sup>
</div>

## Componentes

### Aplicativo Mobile
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

### API Gateway
- **Responsabilidades**:
  - Autenticação e autorização
  - Rate limiting
  - Roteamento de requisições
  - Logs de auditoria

### Módulo de Segurança Anti-Fraude
- **Componentes**:
  - Análise comportamental (horários, localização, padrões)
  - Validação biométrica (voz, digital)
  - Score de risco em tempo real
  - Sistema de alertas multicamadas

### Camada de Microsserviços

#### Serviço de Perfil do Cliente Senior
- **Funcionalidades**:
  - Gestão de preferências de acessibilidade
  - Histórico de interações
  - Configurações de privacidade LGPD
  - Perfil de risco atualizado

#### Serviço de Recomendações Inteligentes
- **Modelos de Recomendação**:

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

#### Serviço de Conteúdo Educacional
- **Funcionalidades**:
  - Curadoria de conteúdo por perfil
  - Geração de reels personalizados
  - Sistema de progressão em letramento financeiro
  - Integração com Rádio Itaú

### Dados e Armazenamento

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

### Pipeline de Machine Learning
- **Fluxo**:
  1. Coleta dados com consentimento
  2. Processamento
  3. Feature Engineering (Criação de variáveis para modelos)
  4. Treinamento (atualização automática dos modelos)
  5. Deploy (versionamento e A/B testing)

### Open Banking Hub
- **APIs Expostas**:
  - Dados de conta (com consentimento)
  - Histórico de transações
  - Produtos contratados
- **APIs Consumidas**:
  - Dados de outras instituições (consolidação financeira)
  - Bureau de crédito para análise de risco

## Diagrama

&nbsp;&nbsp;&nbsp;&nbsp;Nesse sentido, a Figura 2 abaixo mostra uma versão simplificada da arquitetura para facilitar a visualização, propondo a organização dos principais componentes.


<div align="center">
  <sup>Figura 2 - Diagrama de Arquitetura Simplificado</sup>
  <br />
  <img src={useBaseUrl('/img/arquitetura_simplificada.png')} alt="Diagrama de Arquitetura Simplificado" style={{maxWidth: "600px"}} />
  <br />
  <sup>Fonte: Material produzido pelos autores (2025).</sup>
</div>

&nbsp;&nbsp;&nbsp;&nbsp;A Figura 2 ilustra o fluxo de comunicação entre os principais componentes do sistema. O **Aplicativo Mobile Acessível** atua como ponto de entrada, enviando requisições ao **API Gateway**, que centraliza o controle de acesso, autenticação e roteamento. O API Gateway direciona as solicitações para os microsserviços apropriados — como o **Módulo de Segurança Anti-Fraude**, **Serviço de Perfil**, **Recomendações Inteligentes** e **Conteúdo Educacional** —, garantindo que cada serviço receba apenas as informações necessárias.

&nbsp;&nbsp;&nbsp;&nbsp;Esses microsserviços, por sua vez, interagem com as camadas de dados, como o **Data Lake** (para armazenamento seguro e processamento de dados conforme a LGPD) e bancos de dados especializados (**PostgreSQL**, **Redis**, **Neo4j**, **DynamoDB**), além do **Sistema de Consentimento LGPD** para validação e rastreamento de permissões dos usuários. O fluxo é bidirecional: respostas e dados processados retornam pelos mesmos canais a fim de retreinar os modelos.

&nbsp;&nbsp;&nbsp;&nbsp;Já o **Open Banking Hub** conecta o ecossistema a instituições externas, permitindo tanto o consumo quanto a exposição de APIs mediado pelo gateway.

&nbsp;&nbsp;&nbsp;&nbsp;Dessa forma, a arquitetura proposta integra acessibilidade, segurança e conformidade regulatória para criar uma experiência digital inclusiva para o público sênior. Assim, ao combinar tecnologias, microsserviços e governança de dados, a solução garante não apenas facilidade de uso, mas também proteção contra fraudes e personalização de serviços.