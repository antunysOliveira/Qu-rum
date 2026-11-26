# Quórum — Presença de Raid

Livro de chamada da guild em uma página só. Marque as raids em bolinhas coloridas, acompanhe quem está faltando e exporte o relatório pro Discord em poucos cliques.

![Status](https://img.shields.io/badge/status-ativo-brightgreen) ![HTML](https://img.shields.io/badge/HTML5-E34F26?logo=html5&logoColor=white) ![CSS](https://img.shields.io/badge/CSS3-1572B6?logo=css3&logoColor=white) ![JS](https://img.shields.io/badge/JavaScript-F7DF1E?logo=javascript&logoColor=black)

## O que faz

Um controle de presença de raid para guild, pensado para o oficial que faz a chamada toda semana. Cada jogador vira uma linha com bolinhas por dia — cada bolinha é uma raid. Clica, marca, pronto.

- **Grade de bolinhas por jogador**, pintada com a cor da classe
- **Agrupamento por classe** com média de presença de cada grupo
- **Alertas de "baixo"** por dia, com contador por jogador
- **KPIs no topo**: presença geral, total de jogadores, quantos fecharam 100%, quantos têm alerta
- **Análise lateral**: presença por dia, presença por classe, top faltas, top alertas
- **Múltiplas semanas**, com opção de copiar o elenco da anterior
- **Busca e filtros** (por classe, só com alertas, só com faltas, só 100%)
- **Undo/Redo** com `Ctrl+Z` / `Ctrl+Shift+Z`
- **Importa texto** no formato do relatório (`* Nome: Seg 6/6 | Ter 6/6 → Baixo: 0x`)
- **Exporta** para texto (copiar/colar no Discord), CSV (planilha) ou JSON (backup)
- **Salvamento automático** no navegador (localStorage)
- **Responsivo** e com suporte a tema claro/escuro automático
- **Acessível**: navegação por teclado, foco visível, `aria-*` corretos, alvos de toque de 44px

## Como usar

Não tem build, não tem dependência. É um arquivo só.

1. Baixe o `index.html`
2. Abra no navegador (duplo clique resolve)
3. Marque as presenças e exporte quando terminar

Se preferir, hospede como GitHub Page e compartilhe o link com os oficiais da guild.

## Atalhos

| Ação | Atalho |
|---|---|
| Salvar | `Ctrl+S` |
| Desfazer | `Ctrl+Z` |
| Refazer | `Ctrl+Shift+Z` ou `Ctrl+Y` |
| Fechar diálogo | `Esc` |
| Confirmar edição de nome | `Enter` |

## Formato do texto para importar

```
BRUXO
* Solaron: Seg 6/6 | Ter 6/6 | Qua 4/4 → Baixo: 0x
* Clowgirl: Seg 0/6 | Ter 4/6 | Qua 0/4 → ⚠️ Baixo: 1x (Ter 1x)

CACIQUE
* Crasique: Seg 6/6 | Ter 6/6 | Qua 4/4 → Baixo: 0x
```

A classe fica numa linha sozinha (maiúsculas ou não). Cada jogador começa com `*` ou `-`, seguido do nome, dois pontos, os dias no formato `Nome N/M` separados por `|`, e opcionalmente `→ Baixo: Nx (Dia Nx, Dia Nx)`.

## Stack

- HTML + CSS + JavaScript vanilla, zero dependências
- Fontes: Chakra Petch (títulos) e Inter (texto)
- Paleta: faixa carmesim de estandarte, cores por classe
- Integração opcional com o runtime de artifacts do Claude (save remoto e download)

## Estrutura

```
Qu-rum/
├── index.html    # app completo (HTML + CSS + JS + estado inicial)
└── vercel.json   # config pra servir estático na Vercel
```

Tudo mora no mesmo arquivo. O estado inicial vai num `<script type="application/json">` para sobreviver a reloads e facilitar o compartilhamento.
