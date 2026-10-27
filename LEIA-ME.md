# SCP Stat · Polo Aquático — app instalável (PWA)

Esta pasta é a app completa. Depois de alojada num endereço **https://**, pode ser instalada em tablets, telemóveis e computadores como uma app normal (ícone no ecrã principal, ecrã inteiro e funcionamento **sem internet**).

## 1. Alojar a app (uma vez)

A instalação só funciona a partir de um endereço https. Aberta como ficheiro no dispositivo, a app funciona mas não se instala. A opção mais simples e gratuita é o **GitHub Pages**:

1. Criar uma conta em github.com (de preferência uma conta do clube/departamento).
2. Criar um repositório novo (por exemplo `scp-stat`).
3. Em **Add file › Upload files**, arrastar **todo o conteúdo desta pasta** (não a pasta em si) e confirmar com **Commit changes**.
4. Em **Settings › Pages**, em *Branch* escolher `main` e a pasta `/ (root)` e guardar.
5. Passado um ou dois minutos, a app fica disponível em `https://<conta>.github.io/scp-stat/`.

Notas:
- No plano gratuito do GitHub, o repositório do Pages é público: qualquer pessoa com o endereço vê a **app**, mas **não os dados**, que ficam apenas em cada dispositivo.
- Outras opções que também servem: Firebase Hosting, Netlify ou Cloudflare Pages. Se avançarem com o Firebase para a base de dados, faz sentido alojar lá também.

## 2. Instalar em cada dispositivo

- **Android (Chrome) e computador (Chrome/Edge):** abrir o endereço e carregar no botão **Instalar** da app (no topo ou em Início), ou no menu ⋮ › *Instalar app*.
- **iPhone / iPad (Safari):** abrir o endereço no Safari › botão **Partilhar** › **Adicionar ao ecrã principal**.
- No Android, um toque longo no ícone dá atalhos para Tempo de Jogo, Estatística Individual e Exclusões.

Importante no iPhone/iPad: os dados do Safari e os da app instalada ficam **separados**. Instala primeiro e regista os jogos já dentro da app. Para passar jogos antigos, usa *Início › Exportar jogo* e depois *Importar jogo*.

## 3. Atualizar a app

Para publicar uma versão nova, gera a pasta outra vez e volta a carregar os ficheiros no repositório (substituindo os anteriores). Nos dispositivos aparece o aviso **"Há uma versão nova da SCP Stat · Atualizar agora"**. Os dados registados mantêm-se.

O `sw.js` tem um número de versão gerado automaticamente. É ele que faz os dispositivos detetarem a atualização, por isso não deve ser editado à mão.

## Estrutura

| Página | HTML | JavaScript |
|---|---|---|
| Início | `index.html` | `javascript/inicio.js` |
| Estatística Individual | `estatistica_individual.html` | `javascript/estatistica_individual.js` |
| Remates | `remates.html` | `javascript/remates.js` |
| Jogadores | `jogadores.html` | `javascript/jogadores.js` |
| Guarda-Redes | `guarda_redes.html` | `javascript/guarda_redes.js` |
| Estatística Coletiva | `estatistica_coletiva.html` | `javascript/estatistica_coletiva.js` |
| Tempo de Jogo | `tabela_tempo_jogo.html` | `javascript/tabela_tempo_jogo.js` |
| Exclusões | `exclusoes.html` | `javascript/exclusoes.js` |
| Sugestão de Interpretação | `interpretacao.html` | `javascript/interpretacao.js` |
| Definições | `definicoes.html` | `javascript/definicoes.js` |

- `css/scp_stat.css` — estilos de todas as páginas.
- `javascript/core.js` — partilhado por todas as páginas: armazenamento, header, exportar/importar, listas de ações e jogadas, campo e baliza, relógio, instalação/atualização da app e jogo de exemplo.
- `manifest.webmanifest` — nome, ícones, cores e atalhos da app instalada.
- `sw.js` — service worker: guarda a app no dispositivo para funcionar sem internet.
- `icons/`, `screenshots/` — ícones da app e imagens do diálogo de instalação.
- `.nojekyll` — necessário para o GitHub Pages servir os ficheiros tal como estão.

## Dados

- Os dados ficam no armazenamento do browser/app de cada dispositivo (chave `scpStatPoloAquatico.v1`). Desinstalar a app ou limpar os dados do browser apaga os registos: exporta o jogo no fim de cada partida, ou faz uma cópia de segurança em *Definições*.
- As listas de ações, situações e jogadas estão em `javascript/core.js` (`ACTIONS`, `STD`, `EXCS`, `COL_OPTS`, `COL_TABLES`).
