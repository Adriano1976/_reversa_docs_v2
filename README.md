# Documentação Interativa — analisador-genealogico

Mini-site HTML autocontido gerado pelo publisher do framework Reversa que transforma metadados e JSONs do pipeline de análise em uma documentação navegável e offline-first.

Última geração (nos artefatos): assets/js/data.js gerado em 2026-08-12T14:00:00Z; índice gerado em 2026-08-12T14:35:00Z.

## Visão rápida
Este repositório contém uma documentação estática e navegável para o projeto analisador-genealogico. O site principal é `index.html` e as páginas de features e visualizações (arquitetura, módulos, métricas, deck, glossário) estão disponíveis como HTML autocontido.

Principais páginas:
- `index.html` — home do mini-site, lista de features e cartões.
- `arquitetura.html` — visualização Code City da arquitetura.
- `modulos.html` — grafo de dependências entre módulos.
- `metricas.html` — dashboard com métricas (Highcharts).
- `deck.html` — apresentação com a história da reconstrução.
- `glossario.html` — termos e definições.
- `features/*.html` — páginas de cada feature documentada (upload-gedcom, busca-caminho, analise-dna).

Os dados e o índice do site são embutidos em `assets/js/data.js` e a navegação é construída por `assets/js/nav.js`.

## Como visualizar localmente
O site é estático — basta servir os arquivos localmente e abrir http://localhost:8000. Exemplos:

- Usando Python (qualquer 3.x):
  ```bash
  python3 -m http.server 8000
  # depois abrir http://localhost:8000 no navegador
  ```

- Usando Node (serve):
  ```bash
  npx serve -s .
  # ou
  npm install -g serve
  serve -s .
  ```

Observações:
- Não são necessárias variáveis de ambiente para visualização.
- Para testes rápidos no Windows, abra index.html diretamente no navegador; porém, alguns recursos (fetch relativo ou comportamento de caminhos) funcionam melhor via servidor HTTP.

## Como o site é gerado
- Fonte dos dados: `assets/data/*.json` (mantidos para regeneração granular).
- Arquivo gerado: `assets/js/data.js` (contém `window.RV_DATA` com índices, módulos, features e metas).
- Publisher: meta em `index.html` indica o produtor `reversa-docs-publisher`. Para regenerar a documentação, atualize os JSONs em `assets/data/` e execute o processo de publicação do Reversa (ou o script/publisher responsável no seu fluxo de CI).

Arquivos importantes:
- `assets/js/data.js` — dados embutidos; contém `generatedAt` e `project`.
- `assets/js/nav.js` — monta a navegação a partir de `window.RV_DATA.nav`.
- `features/*.html` — páginas independentes que usam os dados globais para marcar a navegação e renderizar conteúdo.

## Contribuindo
- Para corrigir texto ou imagens: edite as páginas HTML correspondentes ou os arquivos em `assets/img/`.
- Para adicionar/atualizar features no índice: atualize os JSONs em `assets/data/` e regenere `assets/js/data.js` via publisher.
- Se preferir que eu abra o PR com mudanças propostas (ex.: este README), posso criá-lo.

## Licença
Este repositório inclui um arquivo LICENSE com os termos de licenciamento. Consulte `LICENSE` para detalhes.
