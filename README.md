# Frontend-project-scope

Escopo e arquitetura de um projeto frontend moderno

---

## 📘 Visão Geral

Este repositório documenta a arquitetura e as diretrizes principais adotadas em um projeto frontend moderno, utilizando uma stack atualizada e foco em escalabilidade, testes, design system, integração com APIs e adoção consciente de novas tecnologias.

---

## 📂 Estrutura dos Documentos

Cada tema principal foi isolado em um documento próprio para facilitar a leitura e evolução futura:

### `architecture.md`

Define a arquitetura base do projeto, com escolha de tecnologias (Next.js 15, Tailwind CSS, ShadCN UI, TanStack, etc).

### `refactor-plan.md`

Plano detalhado de refatoração para código legado, com ações progressivas, encapsulamento de dívidas técnicas,.

### `api-structure.md`

Organização da integração com APIs, incluindo padrões de autenticação (JWT), tratamento de erros, uso de `apiClient`, divisão por domínio e hooks reutilizáveis.

### `design-system.md`

Estratégia de implementação e governança de um Design System com ShadCN UI + Tailwind. Contém tokens, documentação com Storybook, boas práticas.

### `ci-quality.md`

Pipeline de CI/CD configurado com GitHub Actions, testes unitários (Jest), E2E (Cypress), lint, coverage mínimo.

### `new-tech-eval.md`

Plano para adoção de novas tecnologias, com definição de critérios técnicos e organizacionais, execução de provas de conceito (PoCs) e processo gradual de migração.

---

## 🧭 Como navegar

Todos os tópicos foram escritos com foco prático, e a estrutura de diretórios reflete as decisões técnicas.
