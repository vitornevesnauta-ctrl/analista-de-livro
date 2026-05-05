# Analista de Livros

Site minimalista que transforma qualquer livro em um relatório estratégico em PDF, gerado por IA.

O usuário digita o nome do livro (e opcionalmente o autor), a IA da Anthropic gera uma análise completa seguindo uma estrutura editorial fixa (visão geral, ideias-chave, melhores partes, aplicação prática, erros comuns, plano de ação) e o site entrega um PDF pronto para baixar.

## Demo

É um site 100% estático — basta abrir o `index.html` no navegador ou hospedar no GitHub Pages.

## Como subir no GitHub Pages

1. Crie um repositório no GitHub (ex.: `analista-de-livros`).
2. Faça upload do `index.html` e do `README.md`.
3. No repositório, vá em **Settings → Pages**.
4. Em **Source**, escolha a branch `main` e a pasta `/ (root)`.
5. Salve. Em alguns minutos seu site estará no ar em `https://seu-usuario.github.io/analista-de-livros/`.

## Como funciona

O site faz uma chamada direta para a API da Anthropic a partir do navegador. Cada usuário precisa ter sua própria chave da API.

### Por que o usuário precisa de uma chave?

O site é estático, sem servidor próprio — então não há onde esconder uma chave de API compartilhada. Cada visitante usa sua própria chave da Anthropic, que fica guardada apenas no navegador dele (em `localStorage`, se ele optar por "lembrar a chave"). Nenhum servidor seu vê ou armazena nada.

### Onde conseguir uma chave da Anthropic

1. Acesse [console.anthropic.com](https://console.anthropic.com/settings/keys).
2. Crie uma conta (ou faça login).
3. Vá em **API Keys → Create Key**.
4. Copie a chave que começa com `sk-ant-...`.
5. Cole no campo do site.

> O custo de cada relatório gerado é de centavos (uso da API Sonnet).

## Stack

- HTML, CSS e JavaScript puros (sem build, sem framework).
- [marked.js](https://github.com/markedjs/marked) para converter Markdown em HTML.
- [html2pdf.js](https://github.com/eKoopmans/html2pdf.js) para gerar o PDF no navegador.
- Fonts: Fraunces (display) e Inter (UI), via Google Fonts.

## Personalização

Tudo que você pode querer trocar está no topo do `<style>` em `index.html`, dentro de `:root`:

```css
--bg: #F7F4EE;          /* fundo cor creme */
--accent: #8B5E3C;      /* cor de destaque (sienna) */
--font-serif: 'Fraunces', ...;
--font-sans: 'Inter', ...;
```

O prompt da IA fica na constante `SYSTEM_PROMPT` no JavaScript — edite à vontade para ajustar o estilo das análises.

## Privacidade

A chave da API e os dados nunca passam por nenhum servidor terceiro. A comunicação acontece direta entre o navegador do usuário e a API da Anthropic.

## Licença

Use à vontade.
