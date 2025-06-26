# Plano de Ação

## Diagnóstico e mapeamento

- Auditoria de código: analisar os principais arquivos e módulos:
  - Código duplicado
  - Componentes gigantescos e sem separação de responsabilidades
  - Ausência de testes
  - Uso de bibliotecas desatualizadas
- Ferramentas:
  - ESLint + SonarQube para detectar problemas automaticamente

## Priorização por impacto de risco

- Priorizar classificando os pontos técnicos com base em:
  - Risco para o funcionamento do sistema
  - Frequência de uso
  - Facilidade de refatoração

## Estabelecer um plano de refatoração incremental

- Dividir a refatoração em sprints curtas com pequenas entregas
- Garantir que toda refatoração passe por uma revisão de código
- Refatorar por contexto ou feature, tirando o update de libs

## Garantir a qualidade contínua

- Configurar o CI para rodar tests, Lint e Prettier
- Usar Feature flags para lançar novas versões em produção sem afetar todos os usuários
- Incluir logs e tracking de erros com Sentry por exemplo.

## Comunicação e documentação

- Documentar decisões técnicas
- Criar um guia de estilo utilizando o ShadCN e Tailwind
