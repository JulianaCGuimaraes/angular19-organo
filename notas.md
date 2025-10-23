# 🅰️ Angular 19 — Instalação, Configuração e Conceitos Modernos

> Notas de estudo baseadas no curso **"Angular 19: Estruture Componentes com Signals e Controle de Fluxo" — Alura**
> Inclui instalação, criação de projeto, componentes, binding, Signals, `@for`, `@if` e `ngClass`.

---

## 📚 Sumário

1. [Instalação e Configuração Inicial](#1-instalação-e-configuração-inicial)

   * [Instalando o Angular CLI](#11-instalando-o-angular-cli)
   * [Criando o Projeto Angular](#12-criando-o-projeto-angular)
   * [Criando Componentes de Cabeçalho e Rodapé](#13-criando-os-componentes-de-cabeçalho-e-rodapé)
   * [Codificando HTML e CSS](#14-codificando-o-html-e-css-dos-componentes)
   * [Renderizando Componentes na Aplicação](#15-renderizando-os-componentes-na-aplicação)
   * [CSS Global](#16-css-global)
2. [Data Binding](#2-data-binding)

   * [Interpolação](#21-interpolação)
   * [Property Binding](#22-property-binding)
   * [Event Binding](#23-event-binding)
3. [Inputs e Signals](#3-inputs-e-signals)

   * [`@Input()`](#31-input)
   * [`inputSignal()`](#32-inputsignal)
   * [Zone.js vs Signals](#33-zonejs-vs-signals)
4. [Hooks do Ciclo de Vida](#4-hooks-do-ciclo-de-vida)

   * [`ngOnInit()`](#41-ngoninit)
   * [Outros hooks](#42-outros-hooks)
5. [Map e Estruturas de Dados](#5-map-e-estruturas-de-dados)
6. [Controle de Fluxo Moderno](#6-controle-de-fluxo-moderno)

   * [`@for`](#61-for)
   * [`@if`](#62-if)
7. [Classes Dinâmicas](#7-classes-dinâmicas-ngclass)
8. [Resumo e Comparações](#8-resumo-e-comparações)

---

## 1. Instalação e Configuração Inicial

### 1.1 Instalando o Angular CLI

```bash
npm install -g @angular/cli
```

> Permite criar e gerenciar projetos Angular globalmente.

---

### 1.2 Criando o Projeto Angular

```bash
ng new organo
cd organo
ng serve
```

* **Estilo:** CSS
* **SSR:** Não
* Abra [http://localhost:4200](http://localhost:4200) para ver a aplicação.

---

### 1.3 Criando os Componentes de Cabeçalho e Rodapé

```bash
ng g c componentes/cabecalho
ng g c componentes/rodape
```

> Cria arquivos `.ts`, `.html`, `.css` e `.spec.ts`.

---

### 1.4 Codificando o HTML e CSS dos Componentes

#### Cabeçalho (`cabecalho.component.html`)

```html
<header class="banner">
  <img src="banner.png" alt="Banner principal da página do Organo" />
</header>
```

```css
.banner img {
  width: 100%;
}
```

#### Rodapé (`rodape.component.html`)

```html
<footer class="banner-rodape">
  <img src="rodape.png" alt="Rodapé da aplicação" />
</footer>
```

```css
.banner-rodape img {
  width: 100%;
  margin-top: 120px;
  display: block;
}
```

---

### 1.5 Renderizando os Componentes na Aplicação

```html
<app-cabecalho></app-cabecalho>

<!-- Conteúdo principal da aplicação -->

<app-rodape></app-rodape>
```

---

### 1.6 CSS Global

```css
body, html {
  margin: 0;
  padding: 0;
}
```

---

## 2. Data Binding

### 2.1 Interpolação

```html
<p>{{ titulo }}</p>
```

* Fluxo: **Classe → Template**

---

### 2.2 Property Binding

```html
<h1 [innerText]="titulo"></h1>
<img [src]="imagem" />
<button [disabled]="desabilitado">Enviar</button>
```

* `[prop]` → conecta propriedade do componente a HTML.

---

### 2.3 Event Binding

```html
<button (click)="mostrarMensagem()">Clique aqui</button>
<p>{{ mensagem }}</p>
```

* `(evento)` → Template → Componente
* Pode passar parâmetros: `(click)="mostrarMensagem('Olá')"`

---

## 3. Inputs e Signals

### 3.1 `@Input()`

```typescript
@Input() livro!: Livro;
```

* Decorador tradicional, baseado em `zone.js`
* Recebe dados do **componente pai**

---

### 3.2 `inputSignal()`

```typescript
livro = input<Livro>();
```

* API reativa moderna (Angular 16+)
* Baseada em **Signals**, elimina `zone.js`
* Atualizações reativas e performáticas

---

### 3.3 Zone.js vs Signals

| Aspecto      | zone.js             | Signals                |
| ------------ | ------------------- | ---------------------- |
| Função       | Detecta mudanças    | Reatividade explícita  |
| Performance  | Pode ser mais lento | Mais leve e previsível |
| Atualizações | Automáticas         | Reativas e controladas |
| Angular      | 2–15                | 16+                    |

---

## 4. Hooks do Ciclo de Vida

### 4.1 `ngOnInit()`

```typescript
ngOnInit(): void {
  this.livrosPorGenero.set('Ficção', ['1984', 'Admirável Mundo Novo']);
}
```

* Executado **após o construtor**, antes da renderização

---

### 4.2 Outros hooks

| Hook                | Momento de execução            |
| ------------------- | ------------------------------ |
| `ngOnChanges()`     | Quando `@Input()` muda         |
| `ngAfterViewInit()` | Após renderizar a view         |
| `ngOnDestroy()`     | Antes de destruir o componente |

---

## 5. Map e Estruturas de Dados

```typescript
const livros = new Map();
livros.set('Ficção', ['1984', 'Admirável Mundo Novo']);
livros.set('Fantasia', ['O Hobbit', 'Harry Potter']);
```

* Permite **chaves únicas de qualquer tipo**
* Mantém **ordem de inserção**
* Métodos: `set()`, `get()`, `has()`, `delete()`, `clear()`

---

## 6. Controle de Fluxo Moderno

### 6.1 `@for` (Angular 17+)

```html
@for (livro of livros; track livro; let i = $index; empty) {
<p>{{ i + 1 }} - {{ livro }}</p>
} @empty {
<p>Nenhum livro encontrado.</p>
}
```

* Substitui `*ngFor`
* Integrado com Signals, mais performático
* `track` → rastreia item para re-renderização
* `@empty` → bloco alternativo se lista vazia

---

### 6.2 `@if` (Angular 17+)

```html
@if (usuario) {
<p>Bem-vindo, {{ usuario.nome }}!</p>
} @else if (carregando) {
<p>Carregando...</p>
} @else {
<p>Faça login</p>
}
```

* Substitui `*ngIf`
* Permite `@else if` e `@else`
* Sintaxe limpa e declarativa

---

### 6.3 Exemplo combinando `Map` e `@for`

```typescript
livrosPorGenero = new Map<string, string[]>();

ngOnInit() {
  this.livrosPorGenero.set('Ficção', ['1984', 'Admirável Mundo Novo']);
  this.livrosPorGenero.set('Fantasia', ['O Hobbit', 'Harry Potter']);
}

generos() {
  return Array.from(this.livrosPorGenero.entries());
}
```

```html
@for (genero of generos(); track genero[0]) {
<h3>{{ genero[0] }}</h3>
<ul>
  @for (livro of genero[1]; track livro) {
  <li>{{ livro }}</li>
  }
</ul>
}
```

---

## 7. Classes Dinâmicas `ngClass`

```html
<p [ngClass]="{ 'ativo': estaAtivo, 'erro': temErro }">Status dinâmico!</p>
```

```typescript
estaAtivo = true;
temErro = false;
```

```css
.ativo { color: green; }
.erro { color: red; }
```

* Aplica classes condicionalmente com base em variáveis do componente
* Alternativa ao atributo `class` estático

---

## 8. Resumo e Comparações

| Conceito          | Angular 2–15               | Angular 16–19                 |
| ----------------- | -------------------------- | ----------------------------- |
| Data Binding      | `{{ }}`, `[prop]`, `(evt)` | Mesma sintaxe + Signals       |
| Input             | `@Input()`                 | `@Input()` ou `inputSignal()` |
| Change Detection  | Zone.js                    | Signals, reativo              |
| Loop              | `*ngFor`                   | `@for`                        |
| Condicional       | `*ngIf`                    | `@if`                         |
| Classes dinâmicas | `[ngClass]`                | `[ngClass]`                   |


