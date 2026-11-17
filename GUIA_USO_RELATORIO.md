# Guia de uso e manutenção do relatório ELOS

## Links oficiais

- Relatório ao vivo: https://vyvemarketing.github.io/elos-relatorio/
- Novembro: https://vyvemarketing.github.io/elos-relatorio/ELOS_Relatorio_1S2026.html#novembro
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

O calendário cobre **01/01/2026 a 15/11/2026**. O período completo e os presets **Setembro completo**, **Outubro completo** e **Novembro (1–15)** usam consultas consolidadas exatas do GA4 (Google Analytics 4). O fechamento anterior de 01/01–30/09 também permanece disponível ao selecionar essas datas. A base diária contém **01/01 a 22/08** e o recorte de **27/09**; os demais dias ainda não foram exportados individualmente.

Quando um intervalo contém lacunas, os cards mostram um asterisco e o aviso informa quantos dias estão cobertos. Se nenhum dia foi exportado, mostram **Sem dados**, não zero. O bloco **Novembro** reúne os recortes recentes com a data de cada fonte; **Setembro** preserva o histórico. Não se pode obter qualquer janela diária exata a partir de um total mensal: é necessário exportar esses dias no GA4.

### O que acompanha o filtro

- ⭐ **Dados-chave:** acessos ao site e origens solicitadas pelo cliente.
- 🌐 **Site:** sessões, novos visitantes, visualizações e interações.
- 📊 **Origem:** distribuição das sessões por canal.
- 🎯 **Leads:** leads, downloads, WhatsApp, cliques e buscas.

Os gráficos mensais incluem outubro e novembro parcial. Páginas usam 01/01–15/11. Blog mostra leituras recentes e mantém o histórico de janeiro–junho identificado. Esses quadros não acompanham o filtro de acessos. Google Ads e LinkedIn têm períodos próprios em cada bloco; o filtro não troca o período deles.

## Definições das métricas

- **Visitas ao site:** sessões atribuídas pelo GA4. Uma pessoa pode gerar mais de uma sessão.
- **Novos visitantes:** novos usuários informados pela consulta do GA4; nos intervalos diários cobertos, soma das linhas disponíveis.
- **Retorno de visitas:** usuários recorrentes, métrica nativa do GA4. No total até 15/11: 4.421; em outubro: 461; em 01–15/11: 255. Onde não houve consulta, exibimos N/D. O antigo cálculo `sessões - novos usuários` foi retirado por não medir retorno real.
- **Leads captados:** contagem do evento `generate_lead`. Não significa quantidade de leads únicos ou qualificados. Ausência do evento não prova ausência de contatos.
- **Cliques no WhatsApp:** intenção de contato; não confirma mensagem enviada, conversa iniciada ou lead comercial.
- **Tempo de página/artigo:** engajamento médio por usuário ativo, não duração média de sessão. São métricas diferentes.
- **Propriedade GA4:** reúne site e loja; caminhos iguais podem ser agrupados se não houver a dimensão de hostname (nome do domínio).
- **Orgânico:** Organic Search + Organic Shopping + Organic Video.
- **Direto:** canal Direct.
- **Social:** Paid Social + Organic Social.
- **Referência:** canal Referral.
- **Outros canais:** diferença necessária para fechar o total de sessões; inclui Google Ads/Paid Search, Cross-network, Email, Display, AI Assistant e origens não atribuídas.

## Por que os números antigos divergiam

O quadro antigo de origem mostrava **novos usuários pela primeira origem do usuário**. O quadro Dados-chave mostrava **sessões pela origem da sessão**. As duas leituras existem no GA4, mas não podem ser comparadas diretamente.

O relatório foi padronizado em **sessões pela origem da sessão**. O quadro **De onde vieram as sessões** e o quadro **Dados-chave** agora usam a mesma base, o mesmo intervalo e os mesmos agrupamentos. Não use capturas antigas como referência.

O período completo, setembro, outubro e novembro parcial usam consultas consolidadas oficiais do GA4. Nos demais intervalos, o relatório soma somente as linhas diárias efetivamente exportadas e sinaliza a cobertura. Diferenças entre consultas podem ocorrer por processamento, atribuição ou granularidade; não distribua diferenças manualmente entre os dias nem trate resíduos como um canal identificado.

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

Os indicadores abaixo foram conferidos em 16/11; a auditoria operacional de 17/11 está separada logo depois:

- GA4 de 01/01–15/11: 52.397 sessões, 40.002 novos usuários, 82.799 visualizações e 2.429 cliques no WhatsApp.
- GA4 de 01–15/11: 2.220 sessões, 1.691 novos usuários, 126 cliques de WhatsApp e nenhum `generate_lead` na lista de eventos.
- Google Ads em 10–15/11: R$ 518,22, 27.820 impressões e 2.925 interações. As 768 ações de YouTube não são leads. Colunas Contato/Lead telefônico da Busca: zero; outras ações precisam ser conciliadas.
- LinkedIn Campaign Manager em 10–15/11: R$ 279,94, 30.769 impressões, 570 cliques, CTR de 1,85% e CPC de R$ 0,49.
- LinkedIn página: 11.139 seguidores até 13/11; em 15/10–13/11, 149 patrocinados e 167 orgânicos. Não calcular custo por seguidor usando o gasto de outro período.
- GTM da loja: tag `sign_up` salva no contêiner `GTM-P3BRCVBJ`, ainda não publicado/instalado. A loja carregou `GTM-TR6XKKBB` no teste. Detecção de tag não é prova de rastreamento validado.
- Meta Ads não foi reativado; o estado atual não foi reconsultado.

### Auditoria operacional de 17/11

- LinkedIn, conjunto de seguidores, **19/10–17/11, último dia parcial**: 140 seguidores atribuídos, aproximadamente R$ 680,61 e R$ 4,86 por seguidor. Os cases Pirapora e montagem somaram 128 seguidores. Esse recorte não substitui o fechamento até 15/11.
- Pausados somente **Ad4_RedesSubterraneas (760670163)** e **Ad5_SubtCeara (1170186303)**: zero seguidores no mesmo intervalo, com gastos de R$ 49,52 e R$ 36,51. Status confirmado após recarregar. Orçamentos e lances preservados; efeito futuro ainda não medido.
- Google Ads: ação legada **Contato**, criada em 2023, com configuração incorreta e diagnóstico de que nunca recebeu dados. Isso não prova ausência de contatos. Nenhuma conversão, lance ou orçamento foi alterado nesta auditoria.
- GTM: cadastro e WhatsApp salvos em `GTM-P3BRCVBJ`, mas o novo contêiner continua ausente na home testada em 17/11. Instalação, prévia, teste de sucesso/erro e publicação continuam pendentes. Não declarar rastreamento validado.
- Promoção: **R$ 2.400**, resgatada em 13/11, ativa, vencimento em **12/01/2027**, para futuros gastos de campanhas de visualizações de vídeo. Créditos gastos/saldo restante ainda indisponíveis; não presumir elegibilidade da atual Geração de demanda.
- Novas campanhas: dois rascunhos salvos no Google, sem ativação. Loja inicialmente focada em muflas: R$ 32,89/dia, aproximadamente R$ 1.000/mês, teto de R$ 3 por clique. YouTube: três vídeos de 16/11, R$ 2.400 totais propostos, 18/11–01/01, meta de R$ 0,02 por visualização. A autenticação foi concluída pelo usuário e o salvamento foi conferido. Revalidar metas comerciais, rastreamento, recursos e saldo promocional antes de qualquer ativação.
- A seção **Ações, Comentários e Próxima Revisão** contém esse registro e não acompanha o filtro GA4.

### Histórico de setembro

- 🔎 **Google Ads:** setembro fechou com R$ 2.756,63, 193.863 impressões e CPC médio de R$ 0,29. Entre 29–30/09, a Busca de marca teve CTR de 8,05% e CPC de R$ 11,49, sem novo lead comercial no recorte.
- 🎯 **Conversões Google:** formulário, ligação e mensagem são metas comerciais da Busca. Ações de YouTube ficam separadas e nunca são apresentadas como leads.
- 💼 **LinkedIn Ads:** 10.713 seguidores na base pública; setembro gerou 74 seguidores pagos. Em 29–30/09, foram 12 seguidores a R$ 4,09 cada, com CTR de 4,67%.
- ⏸️ **Meta Ads:** campanhas de Instagram e Facebook estão desativadas e devem permanecer OFF. Os dados exibidos são históricos.
- 📞 **Tracking:** telefone e WhatsApp oficiais usam (41) 3383-9290. O clique de WhatsApp foi validado com um único disparo no Tag Assistant.

## Plano de otimização sem aumento de preço

- 🎯 **LinkedIn:** preservar os cases que trouxeram 128 dos 140 seguidores no recorte auditado e revisar as duas pausas após sete a 14 dias. Priorizar custo por seguidor, não apenas taxa de cliques.
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
