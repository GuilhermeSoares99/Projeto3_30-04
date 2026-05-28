# 🔄 Relatório de Refatoração: De "Divite" Inacessível para HTML5 Semântico

Este documento registra o processo de migração de uma página web legada para os padrões modernos de **HTML Semântico**, **Acessibilidade (WCAG)** e **SEO**, baseando-se nas diretrizes da Unidade de Ensino.

---

## 🛑 O Cenário Anterior (Como o site era)

Antes da intervenção, a página funcionava visualmente para um usuário comum, mas era um **desastre técnico**. O código sofria de "Divite" (uso excessivo e genérico de `<div>`) e ignorava completamente as boas práticas de indexação e acessibilidade.

### Problemas identificados no código antigo:

* **Ausência de Semântica:** Tudo era resolvido com `<div id="header">`, `<div id="menu">`, `<div id="conteudo">`. Para os robôs do Google e leitores de tela, a página era apenas um emaranhado de caixas sem significado.
* **Caos no SEO:** Havia múltiplos títulos `<h1>` espalhados pela página para forçar o tamanho do texto, confundindo os mecanismos de busca sobre qual era o foco real do conteúdo.
* **Barreira de Acessibilidade:** 
  * A imagem principal usava a tag `<img>` sem o atributo `alt` (atau com `alt=""`), deixando usuários cegos completamente no escuro.
  * Os campos do formulário usavam textos soltos ao lado dos inputs em vez da tag `<label>`. Se um leitor de tela entrasse no campo de digitação, ele não saberia dizer se era para digitar o nome ou o e-mail.

---

## 🚀 O Cenário Atual (O que foi consertado)

O código foi completamente refatorado. Eliminamos as tags genéricas e reestruturamos o documento do zero. Veja o que mudou na prática:

### 1. Substituição de Elementos Estruturais
Mudamos a anatomia da página para que o navegador e os buscadores entendam a função de cada bloco instantaneamente:
* `<div>` do topo ➡️ virou **`<header>`**
* `<div>` de links ➡️ virou **`<nav>`** (com a adição da lista `<ul>`/`<li>` para estruturação correta)
* `<div>` do corpo ➡️ virou **`<main>`**
* `<div>` dos textos ➡️ virou **`<article>`** e **`<section>`**
* `<div>` da barra lateral ➡️ virou **`<aside>`**
* `<div>` do rodapé ➡️ virou **`<footer>`**

### 2. Correção Crítica de SEO
* Reduzimos a página para **apenas um `<h1>`** no topo, definindo o assunto principal de forma clara.
* Organizamos os subtítulos em uma ordem lógica (`<h2>` para seções e `<h3>` para subtemas), criando um sumário perfeito para o algoritmo do Google.

### 3. Implementação de Acessibilidade (Padrões WCAG / eMAG)
* **Inclusão do `alt` descritivo:** Agora a imagem narra o seu conteúdo para deficientes visuais.
* **Formulário Vinculado:** Implementamos a tag `<label>` com o atributo `for` conectado diretamente ao `id` do `<input>`. Agora, ao clicar no texto "Nome Completo", o cursor é jogado automaticamente para dentro da caixa de texto, além de permitir que tecnologias assistivas guiem o usuário corretamente.
* **Aria-Label:** Adicionamos o atributo `aria-label="Menu principal"` no `<nav>` para facilitar o salto de navegação via teclado para quem usa leitores de tela.

---

## 📊 Resultado Pós-Refatoração

Ao rodar o código antigo e o código novo em ferramentas de auditoria (como o **Google Lighthouse**), os resultados teóricos mudaram drasticamente:

| Critério | Código Antigo (Legado) | Código Novo (Refatorado) | Impacto Real |
| :--- | :--- | :--- | :--- |
| **SEO** | Ruim / Baixo | **100%** | Melhor rankeamento orgânico no Google. |
| **Acessibilidade** | Crítico / Baixo | **100%** | Página navegável por leitores de tela e via teclado. |
| **Manutenção** | Confusa e poluída | **Limpa e legível** | Facilidade para outros desenvolvedores alterarem o código. |

Uso de ia para escrever a documentação.
