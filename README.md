# Treino do Mikael

App de treino pessoal (PWA) — rotina **Full Body A / B / C** para hipertrofia com **máquinas guiadas**, halteres e polias.

100% estático, sem servidor, sem custo. Roda direto no navegador e instala como app na tela inicial.

## 🚀 Publicar (GitHub Pages)

1. Repositório → **Settings** → **Pages**
2. Em **Build and deployment** → Source: `Deploy from a branch`
3. Branch: `main` · Pasta: `/ (root)` → **Save**
4. Aguarde 1–5 minutos

O app fica disponível em:

```
https://caiofabio893.github.io/app-treino-Mikael/
```

> O repositório precisa ser **público** (plano gratuito do GitHub só publica Pages de repositórios públicos).

## 📲 Como o aluno acessa

O Mikael **não precisa de conta no GitHub**. Basta mandar o link e ele:

1. Abrir o link no Chrome/Safari do celular
2. **Adicionar à tela de início** (no iOS: botão Compartilhar → "Adicionar à Tela de Início"; no Android: menu ⋮ → "Instalar app")
3. Usar como um app normal — inclusive **sem internet**, depois da primeira visita

Os dados (cargas, séries, PRs) ficam salvos **no próprio aparelho dele** via `localStorage`. Ninguém mais vê.

## ⚠️ Ao atualizar o app

Sempre que alterar o `index.html`, **mude a `VERSION` no `sw.js`**:

```js
const VERSION = 'v2';   // → 'v3', 'v4'...
```

Sem isso o celular do aluno pode continuar vendo a versão antiga (o service worker guarda uma cópia para uso offline).

## 🗂️ Arquivos

| Arquivo | Função |
|---|---|
| `index.html` | App completo (HTML + CSS + JS em um arquivo só) |
| `manifest.json` | Configuração do PWA (nome, ícones, cores) |
| `sw.js` | Service worker — cache offline e atualização |
| `.nojekyll` | Necessário para o GitHub Pages não processar os arquivos |
| `icon-192.png` / `icon-512.png` | Ícones do app |
| `treino.md` | A rotina completa em Markdown, com os exercícios, séries, reps e vídeos |

## 📖 A rotina

Ver [`treino.md`](./treino.md) para a rotina completa.

**Regras de segurança (regra de ouro):**

- Treino **Full Body** — apenas máquinas guiadas, halteres e polias
- **Proibido** Agachamento Livre, Supino com Barra Livre e Levantamento Terra
- Cardio somente como caminhada na passadeira/esteira
- Mobilidade e alongamento **sempre** (encurtamento muscular)

| Treino | Foco |
|---|---|
| **A** | Leg Press e Peitoral |
| **B** | Extensora, Flexora e Remadas |
| **C** | Máquinas Inversas e variações |

## 🎬 Vídeos de execução

O Mikael é iniciante, então **todo exercício tem vídeo**: um botão `▶` no canto do card (abre direto, sem precisar abrir o card) e, dentro do card, de 2 a 4 opções com o título de cada vídeo.

São **34 vídeos** no total (15 exercícios + mobilidade e alongamento), todos em português e **verificados um a um**.

### Como trocar ou adicionar um vídeo

Edite o objeto `VIDS` no `index.html`. A chave é o nome **exato** do exercício:

```js
'Leg Press Horizontal (Máquina)':[
  {u:'https://www.youtube.com/watch?v=OUXR0S2MiRo', t:'Leg press horizontal — como fazer?'},
  {u:'https://www.youtube.com/watch?v=xC5lzosZrR4', t:'Leg press: forma correta'}
]
```

### Como conferir se um link está vivo

```powershell
$u = [uri]::EscapeDataString("https://www.youtube.com/watch?v=SEU_ID")
Invoke-RestMethod "https://www.youtube.com/oembed?url=$u&format=json"
```

Se voltar com o **título** = o vídeo existe. Se der **404** = o link morreu, basta trocar a URL.
