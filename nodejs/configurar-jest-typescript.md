# Configurando Jest em Node.js com TypeScript

Adicionar dependências: `yarn add -D jest ts-jest @types/jest`

Criar arquivo de configuração do Jest no diretório raiz, `jest.config.js`

```jsx
const { resolve } = require('path');
const root = resolve(__dirname);
module.exports = {
  rootDir: root,
  displayName: 'root-tests',
  testMatch: ['<rootDir>/src/**/*.test.ts'],
  testEnvironment: 'node',
  clearMocks: true,
  preset: 'ts-jest',
  moduleNameMapper: {
    '@src/(.*)': '<rootDir>/src/$1',
    '@test/(.*)': '<rootDir>/test/$1',
  },
};
```

Adicionar supertest `yarn add -D supertest @types/supertest` para rodar os testes

Adicionar script no package.json

```json
"scripts": {
	"test:functional": "jest --projects ./test --runInBand",
}
```

[Configurando Jest em Node.js com Typescript](https://www.youtube.com/watch?v=NQ6NwofOx0Y&list=PLz_YTBuxtxt6_Zf1h-qzNsvVt46H8ziKh&index=5&frags=wn&ab_channel=WaldemarNetoDevLab)
