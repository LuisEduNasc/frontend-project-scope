# Design e UX

## Abordagem técnica

- Fazer auditoria e inventário de UI:
  - Mapear detalhes de design como cores, tipografia, espaçamento, o básico de design
  - Identificar componentes comuns entre os projetos como botões, inputs, cards, entre outros.
- Ferramentas:
  - Figma, Storybook

## Definição de temas

- Criar a base do design system, como:

```
theme: {
  extend: {
    colors: {
      primary: '#1E40AF',
      secondary: '#64748B',
      danger: '#EF4444',
    },
    fontFamily: {
      sans: ['Inter', ...fontFamily.sans],
    },
  }
}
```

- Organizar por categorias, cores, tipografia, espaçamento, shadows ...

## Componentização

- Utilizando a lib ShadCn temos components acessíveis e minimalistas com base no Redix UI
- Adaptamos os components com variants utilizando Tailwind o que ajuda a reduzir o custo de desenvolvimento

## Documentacão

- Configuramos o storybook para documentar components, design, estados e variações (hover, disabled, loading), padrões de uso.

## Distribuição entre projetos

- Publicamos o design system como um pacote npm privado ou incluímos em um monorepo com Turborepo.
- Os projetos importam os components diretamente

## Adoção entre desenvolvedores

- DX: comandos simples como:
  ```npx shadcn-ui@latest add button````
- Tipagem com typeScript
- Autocomplete no VSCode
- Guia de utilização do README.md no root do projeto
- Controle das mudanças nos components passando pelo PR review
- Pareamento e mentoria para developers juniors e mid level
