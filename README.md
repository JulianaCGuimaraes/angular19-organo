# 🅰️ Organo — Meu Primeiro Projeto Angular 19

> Este é o meu primeiro projetinho desenvolvido usando **Angular 19**, seguindo o curso **"Angular 19: Estruture Componentes com Signals e Controle de Fluxo"** da Alura.  
> O **Organo** é um aplicativo organizador de leituras que permite listar livros, mostrando título, autoria, imagem e gênero literário.

---

## 📖 Funcionalidades do Projeto

- **Listagem de livros:** Exibe uma lista de livros separados por gênero literário, com imagem, título, autor e gênero.  
- **Componentização:** Estrutura modular para reutilização e organização do código.  
- **Controle de fluxo moderno:** Utilização de `@if` e `@for` (Angular 17+) para controle de exibição e iteração de elementos no template.  
- **Inputs com Signals:** Comunicação entre componentes usando a API reativa de Signals.  
- **Estilização dinâmica:** Uso de `ngClass` para aplicar classes CSS conforme o estado da aplicação.  
- **Templates dinâmicos:** Bindings (interpolação e property binding) e event binding para criar interfaces reativas.

---

## ✔️ Técnicas e Tecnologias Utilizadas

| Tecnologia/Ferramenta  | Descrição |
| ---------------------- | --------- |
| Angular 19             | Framework utilizado para construir a aplicação |
| Angular CLI            | Ferramenta de linha de comando para criação e organização do projeto |
| Componentização        | Estrutura modular e reutilizável |
| ngClass                | Diretiva para aplicar classes CSS dinamicamente |
| Templates              | Bindings, interpolação e event binding |
| Controle de fluxo      | `@if` e `@for` para controle condicional e loops reativos |
| Signals                | Comunicação entre componentes de forma reativa e performática |

---

## 🛠️ Como Rodar o Projeto

Para executar o Organo localmente, siga os passos abaixo:

1. Instale **NodeJS** (versão 18 ou superior).  
2. Instale as dependências do projeto:

```bash
npm install
````

3. Execute o projeto em modo desenvolvimento:

```bash
ng serve
```

4. Acesse no navegador: [http://localhost:4200](http://localhost:4200)

---

## 🚀 Observações

* Este projeto foi desenvolvido **seguindo o passo a passo do curso da Alura**.
* O foco foi aprender **componentização, Signals, controle de fluxo moderno e integração de templates dinâmicos**.
* O código está organizado para servir como **referência pessoal de estudo** e consulta rápida sobre Angular 19.

---

## 📂 Estrutura do Projeto

```
organo/
│
├── public
│   ├── banner.png
│   ├── favicon.ico
│   ├── rodape.png
│   └── sem-livros.png
├── src
│   ├── app
│   │   ├── app.component.html
│   │   ├── app.component.scss
│   │   ├── app.component.spec.ts
│   │   ├── app.component.ts
│   │   ├── app.config.ts
│   │   ├── app.routes.ts
│   │   ├── componentes
│   │   │   ├── cabecalho
│   │   │   │   ├── cabecalho.component.html
│   │   │   │   ├── cabecalho.component.scss
│   │   │   │   ├── cabecalho.component.spec.ts
│   │   │   │   └── cabecalho.component.ts
│   │   │   ├── genero-literario
│   │   │   │   ├── genero-literario.component.html
│   │   │   │   ├── genero-literario.component.scss
│   │   │   │   ├── genero-literario.component.spec.ts
│   │   │   │   └── genero-literario.component.ts
│   │   │   ├── lista-livros
│   │   │   │   ├── lista-livros.component.html
│   │   │   │   ├── lista-livros.component.scss
│   │   │   │   ├── lista-livros.component.spec.ts
│   │   │   │   └── lista-livros.component.ts
│   │   │   ├── livro
│   │   │   │   ├── livro.component.html
│   │   │   │   ├── livro.component.scss
│   │   │   │   ├── livro.component.spec.ts
│   │   │   │   ├── livro.component.ts
│   │   │   │   └── livro.ts
│   │   │   └── rodape
│   │   │       ├── rodape.component.html
│   │   │       ├── rodape.component.scss
│   │   │       ├── rodape.component.spec.ts
│   │   │       └── rodape.component.ts
│   │   └── mock-livros.ts
│   ├── index.html
│   ├── main.ts
│   └── styles.scss
├── angular.json
├── notas.md
├── package-lock.json
├── package.json
├── README.md
├── tsconfig.app.json
├── tsconfig.json
└── tsconfig.spec.json
```

---

## 🧠 Aprendizados

* Entender o **ciclo de vida do Angular** (`ngOnInit`, `ngOnChanges`, etc.)
* Diferenciar **@Input()** e **inputSignal()**
* Aplicar **ngClass** para estilização condicional
* Usar **@for** e **@if** no lugar de `*ngFor` e `*ngIf` para maior performance e reatividade
* Componentizar de forma limpa e organizada

---

## 📌 Referências

* Curso utilizado: **Angular 19 — Estruture Componentes com Signals e Controle de Fluxo (Alura)**
* Documentação Angular: [https://angular.dev](https://angular.dev)

