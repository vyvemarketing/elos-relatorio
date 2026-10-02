# Guia de uso e manutenção do relatório ELOS

## Links oficiais

- Relatório ao vivo: https://vyvemarketing.github.io/elos-relatorio/
- Setembro: https://vyvemarketing.github.io/elos-relatorio/ELOS_Relatorio_1S2026.html#setembro
- Dados solicitados pelo cliente: https://vyvemarketing.github.io/elos-relatorio/ELOS_Relatorio_1S2026.html#dados-cliente
- Repositório: https://github.com/vyvemarketing/elos-relatorio

## Como usar o relatório

1. 📅 No topo, escolha um atalho de período ou preencha as datas **De** e **Até**.
2. ✅ Ao alterar uma data, o relatório aplica o intervalo automaticamente. O botão **Aplicar** confirma a seleção.
3. 🔎 Use o menu lateral para navegar. O atalho **★ Dados-chave** abre diretamente os números pedidos pelo cliente.
4. 🎯 O bloco **Resumo executivo** reúne a prioridade atual e os números mais recentes de mídia.
5. 📱 No celular, toque no botão **☰** para abrir ou fechar o menu.

### Cobertura atual dos dados

O calendário cobre **01/01/2026 a 30/09/2026**. O período completo e o preset **Setembro completo** usam consultas consolidadas exatas do GA4 (Google Analytics 4). A base diária para intervalos personalizados contém **01/01 a 22/08** e o recorte de **27/09**; os demais dias ainda não foram exportados individualmente.

Quando um intervalo personalizado contém uma lacuna, os cards mostram um asterisco e o aviso informa quantos dias estão cobertos. O relatório nunca converte um dia ausente em resultado zero. O bloco **Setembro** reúne o fechamento de Google Ads, LinkedIn, GA4 e Meta com a data de cada fonte.

### O que acompanha o filtro

- ⭐ **Dados-chave:** acessos ao site e origens solicitadas pelo cliente.
- 🌐 **Site:** sessões, novos visitantes, visualizações e interações.
- 📊 **Origem:** distribuição das sessões por canal.
- 🎯 **Leads:** leads, downloads, WhatsApp, cliques e buscas.

Os gráficos mensais, páginas e artigos do blog continuam mostrando a exportação detalhada do GA4 indicada em cada seção. Google Ads e LinkedIn têm períodos próprios identificados em cada bloco. O aviso de cobertura permanece no topo para deixar esse escopo explícito.

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

O período completo e setembro usam consultas consolidadas oficiais do GA4. Nos demais intervalos, o relatório soma somente as linhas diárias efetivamente exportadas e sinaliza a cobertura. Pequenas diferenças entre consultas consolidadas e leituras diárias podem ocorrer pelo processamento e pela granularidade do GA4; não distribua a diferença manualmente entre os dias.

## Manutenção técnica

### Arquivos principais

- `ELOS_Relatorio_1S2026.html`: relatório, estilos, scripts e base diária incorporada.
- `index.html`: redirecionamento para o relatório.
- `elos-logo-full.png`: marca exibida no cabeçalho.
- `GUIA_USO_RELATORIO.md`: este manual.

### Atualizar os dados do GA4

1. Exporte no GA4 os dados diários do novo intervalo.
2. Preserve os campos usados no objeto `GA4_PRECISE`: usuários ativos, novos usuários, visualizações, eventos, leads, downloads, WhatsApp, cliques, buscas, sessões e origens.
3. Atualize `start`, `end`, `consolidatedEnd`, `coverageRanges`, `totals`, `rangeTotals` e `daily` dentro de `ELOS_Relatorio_1S2026.html`.
4. Atualize os limites `min`, `max` e os atalhos do seletor de datas.
5. Confira se os totais consolidados fecham e se cada lacuna aparece como cobertura parcial.

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

Sempre informe **métrica + dimensão + intervalo + cobertura**. Exemplo correto: “45.721 sessões, agrupadas pelo canal da sessão, na consulta consolidada de 01/01/2026 a 30/09/2026”. Um mesmo período pode apresentar valores diferentes quando a métrica, a dimensão ou a cobertura muda.

## Situação das plataformas no fechamento de 30/09/2026

- 🔎 **Google Ads:** setembro fechou com R$ 2.756,63, 193.863 impressões e CPC médio de R$ 0,29. Entre 29–30/09, a Busca de marca teve CTR de 8,05% e CPC de R$ 11,49, sem novo lead comercial no recorte.
- 🎯 **Conversões Google:** formulário, ligação e mensagem são metas comerciais da Busca. Ações de YouTube ficam separadas e nunca são apresentadas como leads.
- 💼 **LinkedIn Ads:** 10.713 seguidores na base pública; setembro gerou 74 seguidores pagos. Em 29–30/09, foram 12 seguidores a R$ 4,09 cada, com CTR de 4,67%.
- ⏸️ **Meta Ads:** campanhas de Instagram e Facebook estão desativadas e devem permanecer OFF. Os dados exibidos são históricos.
- 📞 **Tracking:** telefone e WhatsApp oficiais usam (41) 3383-9290. O clique de WhatsApp foi validado com um único disparo no Tag Assistant.

## Plano de otimização sem aumento de preço

- 🎯 **LinkedIn:** preservar os criativos que elevaram o CTR recente para 4,67% e revisar novamente após uma janela mínima de sete dias.
- 👥 **Audiência:** acompanhar frequência, custo por seguidor e divisão entre seguidores patrocinados e orgânicos antes de ampliar o público.
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
