# Implantação rápida

## O que já ficou pronto

- `index.html`: app de campo principal do ACE.
- `painel.html`: painel analítico principal.
- `cartao.html`: cartão virtual acessível por `?codigo=`.
- `index_alternativo.html`, `painel_alternativo.html`, `cartao_alternativo.html`: versão alternativa visual.
- `assets/runtime-config.js`: ponto único para colar a URL do Web App.
- `api_google_apps_script.txt`: API completa para Google Apps Script.
- `assets/carmo-territorios-data.js`: camada territorial extraída do `CARMO.kmz` para o mapa.

## Configuração da API

1. Crie uma planilha no Google Sheets.
2. Abra `Extensões > Apps Script`.
3. Apague o conteúdo padrão e cole o arquivo [api_google_apps_script.txt](/D:/CODEX/api_google_apps_script.txt).
4. Salve o projeto.
5. Publique em `Implantar > Nova implantação > Aplicativo da web`.
6. Permita acesso de quem usar o sistema.
7. Copie a URL do Web App publicado.
8. Cole a URL em [runtime-config.js](/D:/CODEX/assets/runtime-config.js).

## Estrutura da planilha

A API cria automaticamente as abas abaixo na primeira execução:

- `Agentes`
- `Imoveis`
- `Visitas`
- `Metrics_Diarias`
- `Config`

## Fotos, PDFs e cartão virtual

- A API cria a pasta `FOTOS_ACE_CAMPO`.
- As fotos das visitas são enviadas para essa pasta.
- O link público da foto fica salvo apenas na aba `Visitas`.
- A API cria a pasta `RELATORIOS_ACE_VISITAS`.
- Cada visita sincronizada gera um PDF com dados da visita, assinatura do morador e link do cartão virtual.
- O link do PDF fica salvo na aba `Visitas`.
- O QR impresso deve apontar para `cartao.html?codigo=...`.

## Território e mapa

- O painel já carrega a camada territorial convertida do `CARMO.kmz`.
- Os quarteirões do KMZ podem ser ligados e desligados no mapa.
- As visitas GPS são cruzadas com os polígonos para leitura territorial e destaque por recorte.
- `microarea` e `quarteirao` aceitam formato livre/codificado, como `M02`, `Centro 23`, `9/01`, `13/1` e similares.

## Limitações externas desta sessão

- A criação automática da planilha pelo conector Google ficou bloqueada por reautenticação da conta nesta sessão.
- O sistema está pronto localmente, mas a publicação final no Google Sheets/Drive depende da URL válida do Apps Script e da autenticação da conta Google.
