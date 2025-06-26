# Integração e APIs

## Camada de cliente

- Criar um apiClient usando Axios ou Fetch com configurações globais
  - BaseUrl, timeouts, headers padrão
  - Interceptors para autenticações com Bearer JWT e tratamento de errors

## Organização por módulo ou domínio

- Separar os serviços por exemplo: userService, orderService ...

## Custom Hooks

- Utilizar custom hooks para chamar os serviços e gerenciar o estado de loading, dados, erros

## Autenticação e autorização

- Usar métodos como JWT, OAuth ou API Keys via headers de autorização
- Usar o interceptor para adicionar tokens, renovar tokens e redirecionar para o login em caso de não autenticado.

## Tratamento de errors

- Manter uma estrutura uniforme (code, message, details)
- Mapear mensagens User Friendly no Frontend
- Lógica de retry para evitar errors de integração

## Logging e monitoramento

- Registrar errors de API no Frontend com Sentry
- Monitorar performance e disponilidade das APIs, detectando falhas e lentidão

## Otimização

- Implementar cache com NextJs ou Tanstack Query para evitar muitos requests desnecessários retornando os mesmos dados
- Paginação nos components de lista
- Lazy loading para evitar grandes chunks para renderização no browser
