# Guia de uso e manutenção do relatório ELOS

## Links oficiais

- Relatório ao vivo: https://vyvemarketing.github.io/elos-relatorio/
- Dados solicitados pelo cliente: https://vyvemarketing.github.io/elos-relatorio/ELOS_Relatorio_1S2026.html#dados-cliente
- Repositório: https://github.com/vyvemarketing/elos-relatorio

## Como usar o relatório

1. 📅 No topo, escolha um atalho de período ou preencha as datas **De** e **Até**.
2. ✅ Ao alterar uma data, o relatório aplica o intervalo automaticamente. O botão **Aplicar** confirma a seleção.
3. 🔎 Use o menu lateral para navegar. O atalho **★ Dados-chave** abre diretamente os números pedidos pelo cliente.
4. 🎯 O bloco **Resumo executivo** reúne a prioridade atual e os números mais recentes de mídia.
5. 📱 No celular, toque no botão **☰** para abrir ou fechar o menu.

### Limite atual dos dados

A base precisa do GA4 (Google Analytics 4) cobre **01/01/2026 a 08/08/2026**. O seletor não permite datas fora desse intervalo até que uma nova exportação seja incorporada ao relatório.

### O que acompanha o filtro

- ⭐ **Dados-chave:** acessos ao site e origens solicitadas pelo cliente.
- 🌐 **Site:** sessões, novos visitantes, visualizações e interações.
- 📊 **Origem:** distribuição das sessões por canal.
- 🎯 **Leads:** leads, downloads, WhatsApp, cliques e buscas.

Os gráficos mensais, páginas, artigos do blog e leads continuam mostrando a exportação detalhada do GA4 indicada em cada seção. Google Ads e LinkedIn têm períodos próprios identificados em cada bloco. Quando o filtro está fora do período completo, um aviso aparece no topo para deixar esse escopo explícito.

## Definições das métricas

- **Visitas ao site:** sessões atribuídas pelo GA4. Uma pessoa pode gerar mais de uma sessão.
- **Novos visitantes:** soma de novos usuários identificados pelo GA4 no intervalo.
- **Retorno de visitas:** cálculo operacional `sessões - novos visitantes`. Não é a dimensão nativa de usuários recorrentes do GA4.
- **Leads captados:** evento `generate_lead` registrado no GA4.
- **Orgânico:** Organic Search + Organic Shopping + Organic Video.
- **Direto:** canal Direct.
- **Social:** Paid Social + Organic Social.
- **Referência:** canal Referral.
- **Outros canais:** diferença necessária para fechar o total de sessões; inclui Google Ads/Paid Search, Cross-network, Email, Display, AI Assistant e origens não atribuídas.

## Por que os números antigos divergiam

O quadro antigo de origem mostrava **novos usuários pela primeira origem do usuário**. O quadro Dados-chave mostrava **sessões pela origem da sessão**. As duas leituras existem no GA4, mas não podem ser comparadas diretamente.

O relatório foi padronizado em **sessões pela origem da sessão**. O quadro **De onde vieram as sessões** e o quadro **Dados-chave** agora usam a mesma base, o mesmo intervalo e os mesmos agrupamentos. Não use capturas antigas como referência.

No período completo, os cards usam a consulta consolidada oficial do GA4. Nos intervalos personalizados, o relatório soma as linhas diárias exportadas. Pequenas diferenças entre essas duas leituras podem ocorrer pelo processamento e pela granularidade das consultas do GA4; não distribua a diferença manualmente entre os dias.

## Manutenção técnica

### Arquivos principais

- `ELOS_Relatorio_1S2026.html`: relatório, estilos, scripts e base diária incorporada.
- `index.html`: redirecionamento para o relatório.
- `elos-logo-full.png`: marca exibida no cabeçalho.
- `GUIA_USO_RELATORIO.md`: este manual.

### Atualizar os dados do GA4

1. Exporte no GA4 os dados diários do novo intervalo.
2. Preserve os campos usados no objeto `GA4_PRECISE`: usuários ativos, novos usuários, visualizações, eventos, leads, downloads, WhatsApp, cliques, buscas, sessões e origens.
3. Atualize `start`, `end`, `totals` e `daily` dentro de `ELOS_Relatorio_1S2026.html`.
4. Atualize os limites `min`, `max` e os atalhos do seletor de datas.
5. Confira se os totais do período completo fecham com a exportação do GA4.

### Checklist obrigatório antes de publicar

- [ ] 🔢 Dados-chave e Origem exibem os mesmos valores para Direto, Orgânico, Social e Referência.
- [ ] ➕ Direto + Orgânico + Social + Referência + Outros = total de sessões.
- [ ] 📅 Todos os atalhos de período funcionam.
- [ ] ↔️ Um intervalo personalizado **De/Até** funciona e não aceita data final anterior à inicial.
- [ ] 📱 O relatório não apresenta sobreposição ou texto cortado no celular.
- [ ] 🖥️ O relatório funciona no desktop.
- [ ] 🧭 Os links do menu abrem a seção correta.
- [ ] 🧪 O console do navegador não apresenta erros.

### Publicar no GitHub Pages

```bash
git pull origin main
git add ELOS_Relatorio_1S2026.html GUIA_USO_RELATORIO.md README.md
git commit -m "Atualiza relatorio ELOS"
git push origin main
```

O GitHub Pages publica automaticamente a branch `main`. Após o envio, aguarde a conclusão do workflow e valide o link oficial em uma janela anônima.

## Regra para evitar novas divergências

Sempre informe **métrica + dimensão + intervalo**. Exemplo correto: “36.066 sessões, agrupadas pelo canal da sessão, de 01/01/2026 a 08/08/2026”. Um mesmo período pode apresentar valores diferentes quando a métrica ou a dimensão muda.

## Situação das plataformas na revisão de 28/09/2026

- 🔎 **Google Ads:** acumulado até 25/09 preservado no painel. A exportação de 01 a 26/09 registrou R$ 2.339,03, 175.781 impressões e 8.680 cliques; a captura do painel incluindo 27/09 registrou R$ 2.501,57 e 9.013 cliques. Orçamentos seguem em R$ 44/dia por campanha.
- 🎯 **Conversões Google:** formulário, ligação e mensagem são metas comerciais da Busca. Ações de YouTube ficam separadas e nunca são apresentadas como leads.
- 💼 **LinkedIn Ads:** 10.487 seguidores na última base pública validada; 18 seguidores pagos nos 7 dias verificados em 26/09, a R$ 8,49 cada. A campanha segue em R$ 22/dia.
- ⏸️ **Meta Ads:** campanhas de Instagram e Facebook estão desativadas e devem permanecer OFF. A tela de 01 a 27/09 mostrou 0 campanha ativa.
- 📞 **Tracking:** telefone e WhatsApp oficiais usam (41) 3383-9290. O clique de WhatsApp foi validado com um único disparo no Tag Assistant.

## Plano de otimização sem aumento de preço

- 🎯 **LinkedIn:** preservar os dois criativos com CTR de 4,57% e 3,61%; substituir a peça com CTR de 0,30% e CPC de R$ 2,35.
- 👥 **Audiência:** priorizar cargos elétricos e setores Utilities, Construção, Energia e fabricantes elétricos; separar o teste para medir qualidade sem misturar públicos.
- 📐 **Google:** manter metas de vídeo separadas das metas comerciais. Formulário, ligação e WhatsApp orientam campanhas de Busca; inscrições e engajamentos do YouTube ficam fora da contagem de leads.
- 🔗 **Rastreamento:** padronizar UTMs com fonte, meio, campanha e anúncio em todos os links.
- 💰 **Verba:** não alterar orçamento diário, lance ou investimento total sem nova autorização.

## Reutilizar para futuros clientes

1. Duplique `ELOS_Relatorio_1S2026.html` e renomeie o arquivo com o cliente e o período.
2. No objeto `REPORT_CONFIG`, altere nome, ano, data de atualização e cor principal.
3. Troque o arquivo de logo e mantenha a mesma proporção do cabeçalho lateral.
4. Substitua os números somente com exportações identificadas por fonte e período.
5. Oculte canais que não fazem parte do contrato, mas preserve Site, Leads, Páginas, Blog/SEO e Comentários quando existirem dados.
6. Atualize `GA4_PRECISE` para habilitar o filtro diário do novo cliente.
7. Valide desktop, celular, todos os atalhos do filtro e o fechamento das origens antes de publicar.

O modelo não depende do Looker Studio para abrir. Ele é um arquivo estático publicado no GitHub Pages, com dados incorporados e configuração visual centralizada.

## Orientação para a informática

1. Não editar manualmente os números visíveis sem atualizar também `GA4_PRECISE`.
2. Ao incorporar uma nova exportação, conferir os totais consolidados do GA4 e as 5 origens do relatório.
3. Publicar somente depois de testar período completo, um mês, últimos 7 dias e um intervalo personalizado.
4. Não inserir credenciais, tokens ou links de sessão no repositório.
5. O GitHub Pages publica a branch `main`; validar o workflow antes de enviar o link ao cliente.
6. No rodapé e nas seções de mídia, manter visíveis as datas diferentes de GA4, Google Ads, LinkedIn e Meta para evitar que o cliente compare períodos incompatíveis.
