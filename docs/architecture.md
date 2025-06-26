# Arquitetura Frontend Escalável

## Stack Tecnológica

- **Framework**: NextJs 15 (ReactJS 19)
- **Linguagem**: TypeScript
- **Design System**: TailwindCSS + ShadCN + Radix UI
- **Gerenciamento de estado**: React Query + Zustand
- **Formulários**: React Hook Form + Zod
- **CI/CD**: GitHub Actions + Amplify AWS
- **Testes**: React Testing Library + Jest para unitários, Cypress para E2E testes

## Justificativa

- NextJS permite renderização híbrida (SSR/SSG/ISR), ideal para apps escaláveis.
- TypeScript oferece tipagem estática, essencial para grandes equipes manterem uma certa documentação
  do código e capturar errors no desenvolvimento.
- Tailwind + ShadCN permite design consistente e uma boa experiência de usuário.
- Tanstack Query oferece cache das requisições, revalidação e sincronização com o backend.

## Arquitetura modular

- /app (NextJs routing)
- /components (Todos components globais)
- /features (Grandes features centralizadas com seus prórprios /components, /hooks, /stores)
- /services (comunicação com APIs)
- /hooks
- /utils
- /libs
- /e2e (Cypress tests para e2e)

Dentro de cada directory criar os tests próximos do source code para facilitar localização e manutenção

## Flexibilidade e escalabilidade

- Aplicando ESLint + Prettier a está estrutura teremos uma aplicação flexisível e escalável, mantendo
  o código organizado, com uma fácil rastreabilidade. Teremos:
- **Presentation layer**: componentes visuáis (UI)
- **Application layer**: lógica de estado (Zustand e Tanstack Query)
- **Domain layer**: regras de negócio puras que podem ser mantidas nas features
- **Infrastructure layer**: comunicação com APIs, caches, auth.

- Design orientado a componentes e Feature-Driven Architecture, adotando design system desacoplado e
  escalável (com ShadCN e Tailwind), agrupar funcionalidades por domínio (ex: /features/checkout). Pode-se
  utilzar a adoção de Micro Frontends para grandes aplicações com times distintos.

## Monorepo e Turborepo

- Com Turborepo e PNPM iremos reduzir duplicidade e otimizar CI/CD com caching inteligente.

## Documentação e Governança

- Podemos manter a documentação do design system com Storybook e de toda a evolução do sistema
  no README.md com uma boa estrutura. Para as features podemos usar o Notion ou Confluence para
  manter a decisão sobre a iniciativa da feature, regras de negócio e implementação.

## Internacionalização e acessibilidade desde o início

- Uso do i18n com next-intl ou react-i18next para aplicar o translate quando necessário.
- Components com suporte a ARIA, navegação pelo teclado e dark mode são acessibilidades padrões
  que podem ser aplicadas ao projeto.
