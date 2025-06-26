# Testes e qualidade de código

## Estrutura da pipeline CI/CD

- Utilizando o Github actions para configurar as etapas principais da pipeline
  - Lint e formatação
  - Testes unitários
  - Coverage de 80% nos testes
  - Testes E2E
  - Build
  - Deploy automático para Staging e Prod

## Teste unitário exemplo

```
import React from 'react';
import {fireEvent, render, screen} from '@testing-library/react';
import {Teams} from 'types';
import Card from '..';

const mockUseNavigate = jest.fn();

jest.mock('react-router-dom', () => ({
    ...jest.requireActual('react-router-dom'),
    useNavigate: () => mockUseNavigate,
}));

describe('Card', () => {
    it('should render card with single column', () => {
        var columns = [{key: 'columnKey', value: 'columnValue'}];
        render(<Card columns={columns} />);

        expect(screen.getByText('columnKey')).toBeInTheDocument();
        expect(screen.getByText('columnValue')).toBeInTheDocument();
    });

    it('should render card with multiple columns', () => {
        var columns = [
            {key: 'columnKey1', value: 'columnValue1'},
            {key: 'columnKey2', value: 'columnValue2'},
            {key: 'columnKey3', value: 'columnValue3'},
            {key: 'columnKey4', value: ''},
        ];
        render(<Card columns={columns} />);

        expect(screen.getByText('columnKey1')).toBeInTheDocument();
        expect(screen.getByText('columnValue1')).toBeInTheDocument();
        expect(screen.getByText('columnKey2')).toBeInTheDocument();
        expect(screen.getByText('columnValue2')).toBeInTheDocument();
        expect(screen.getByText('columnKey3')).toBeInTheDocument();
        expect(screen.getByText('columnValue3')).toBeInTheDocument();
        expect(screen.getByText('columnKey4')).toBeInTheDocument();
    });

    it('should navigate when card is clicked and navigation is enabled', () => {
        const navProps = {
            id: '1',
            name: 'Team 1',
        } as Teams;
        render(
            <Card
                columns={[{key: 'columnKey', value: 'columnValue'}]}
                url="path"
                navigationProps={navProps}
            />
        );

        fireEvent.click(screen.getByText('columnKey'));

        expect(mockUseNavigate).toHaveBeenCalledWith('path', {state: navProps});
    });

    it('should not navigate when card is clicked and navigation is disabled', () => {
        render(<Card columns={[{key: 'columnKey', value: 'columnValue'}]} hasNavigation={false} />);

        fireEvent.click(screen.getByText('columnKey'));

        expect(mockUseNavigate).not.toHaveBeenCalled();
    });
});

```

## Teste E2E example

```
describe('Checkout Flow', () => {
  it('Deve completar o fluxo de compra com sucesso', () => {
    cy.visit('/produto/1');
    cy.get('[data-cy=add-to-cart]').click();
    cy.get('[data-cy=go-to-cart]').click();
    cy.get('[data-cy=checkout-button]').click();
    cy.get('[data-cy=success-message]').should('contain', 'Pedido realizado!');
  });
});
```

## Github pipeline exemplo

```
# .github/workflows/ci.yml
name: CI

on: [push, pull_request]

jobs:
  test:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
      - name: Instalar dependências
        run: pnpm install
      - name: Lint
        run: pnpm lint
      - name: Testes Unitários
        run: pnpm test -- --coverage
      - name: Build
        run: pnpm build

```

## CD processo

- Para o CD da aplicação podemos utilizar Amplify da AWS que fornece uma boa integração
  com o Github e nos fornece o controle do build e environment com mínimo esforço
  - Custom domain + HTTPS
  - Environment variables
  - Deploy history
  - Analitics e monitoramento, podemos usar CloudWatch
    Exemplo de build:

```
version: 1
frontend:
  phases:
    preBuild:
      commands:
        - curl -fsSL https://get.pnpm.io/install.sh | sh -
        - export PATH="$HOME/.local/share/pnpm:$PATH"
        - corepack enable
        - pnpm install
    build:
      commands:
        - pnpm build
  artifacts:
    baseDirectory: .next
    files:
      - '**/*'
  cache:
    paths:
      - .next/cache/**/*
      - node_modules/**/*
      - .pnpm-store/**/*

```
