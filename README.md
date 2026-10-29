# Uma stack, duas audiências: Grafana para a Engenharia e para o Negócio

Slides da palestra de **Milton Camara** no **DEVPIRA Grafana Day 2026**, realizado em 31 de outubro de 2026 na Faculdade Anhanguera em Piracicaba-SP, em parceria entre as comunidades DEVPIRA e Grafana & Friends São Paulo.

**[Ver os slides online](https://miltoncamara.github.io/2026-10-31-devpira-grafana-day-uma-stack-duas-audiencias/)** · [Página do evento no Meetup](https://www.meetup.com/pt-br/grafana-and-friends-sao-paulo/events/316746700/)

## Resumo

Infraestrutura e negócio fazem perguntas diferentes sobre o mesmo sistema. A engenharia quer saber se o pod reiniciou, se a fila represou, se o disco vai encher. A operação quer saber se as mensagens do cliente saíram, se o SLA foi cumprido, se a campanha rodou.

A palestra mostra como unificar as duas visões num único Grafana e, principalmente, o que esse Grafana esconde quando está mal configurado. O centro da apresentação são oito casos reais em que o dashboard estava verde e o sistema não estava bem.

## Estrutura

1. Abertura: as duas perguntas que o mesmo sistema recebe
2. A stack: nove datasources, seis tecnologias e um painel só
3. Camada técnica (Azure Monitor, Prometheus, Loki) e camada de negócio (SQL na réplica)
4. O dashboard estava verde: oito casos reais
5. Como validar que o monitoramento mede de verdade
6. Fechamento: questionar a própria fonte de dados

## Como rodar

Requer Node.js 20 ou superior.

```bash
npm install
npm run dev
```

O Slidev abre em `http://localhost:3030`. O modo apresentador, com as notas de cada slide, fica em `http://localhost:3030/presenter`.

## Exportar

```bash
npm run export        # PDF em dist/
npm run export-pptx   # PowerPoint em dist/
```

Na primeira exportação pode ser necessário baixar o navegador usado pelo Playwright:

```bash
npx playwright install chromium
```

## Publicar no GitHub Pages

O workflow em `.github/workflows/deploy.yml` gera o build a cada push na `main` e publica no GitHub Pages. Para ativar, vá em **Settings > Pages** no repositório e escolha **GitHub Actions** como fonte.

## Estrutura do repositório

```
slides.md           conteúdo dos slides e notas do palestrante
styles/index.css    paleta e estilos
images/             foto e QR Code do LinkedIn
.github/workflows/  publicação no GitHub Pages
```

## Contato

[linkedin.com/in/miltoncamara](https://www.linkedin.com/in/miltoncamara/)
