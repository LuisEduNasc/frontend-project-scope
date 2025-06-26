# Adoção de novas tecnologias

## Etapas para avaliação da tecnologia

- Cenário:
  A aplicação atual em React com CSR tem problemas de SEO e performance no LCP (Largest Contentful Paint). A equipe considera migrar para Next.js App Router com Server Components para SSR e melhor caching.

- Critérios de avaliação:

  - Performance: tempo de renderização e carregamento
  - Acessibilidade: Suporte para padrões WCAG
  - SSR e SSG: necessidades específicas de renderização
  - Bundle size
  - Devtools

- Organizacionais:

  - Curva de aprensizado do time
  - Comunidade e documentação para a stack
  - Integração e suporte a bibliotecas como Tailwind, ShadCN, Tanstack

- Implementação de PoC

  - Escolher uma feature real e com escopo definido por exemplo: página de produto
  - Criar uma aplicação isolada
  - Comparar o mesmo fluxo implementado na stack atual com a nova stack
  - Avaliar a PoC com métricas como:
    - Tempo de desenvolvimento
    - Performance, testes com Lighthouse, como se comporta no mobile e no desktop
    - Examinar errors e bugs
    - Testabilidade com Jest e Cypress
    - Colher feedback dos desenvolvedores e stackholders

- Documentação e decisão

  - Criar documento técnico comparativo e armazenar no Confluence ou Notion
  - Anexar dados, screenshots, métricas do Lighthouse, bundle size

- Aprovação
  - Capacitar o time com treinamentos internos e incluir os desenvolvedores nos reviews
  - Adotar feature flag para habilitar gradualmente as entregas com a nova stack
  - Monitoramento pós delivery
