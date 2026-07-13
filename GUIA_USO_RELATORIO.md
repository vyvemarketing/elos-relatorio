# Guia de uso e manutenção do relatório ELOS

## Links oficiais

- Relatório ao vivo: https://vyvemarketing.github.io/elos-relatorio/
- Dados solicitados pelo cliente: https://vyvemarketing.github.io/elos-relatorio/ELOS_Relatorio_1S2026.html#dados-cliente
- Repositório: https://github.com/vyvemarketing/elos-relatorio

## Como usar o relatório

1. 📅 No topo, escolha um atalho de período ou preencha as datas **De** e **Até**.
2. ✅ Ao alterar uma data, o relatório aplica o intervalo automaticamente. O botão **Aplicar** confirma a seleção.
3. 🔎 Use o menu para navegar. O atalho **★ Dados-chave** abre diretamente os números pedidos pelo cliente.
4. 📱 No celular, deslize horizontalmente o menu superior quando algum atalho não estiver visível.

### Limite atual dos dados

A base precisa do GA4 (Google Analytics 4) cobre **01/01/2026 a 12/07/2026**. O seletor não permite datas fora desse intervalo até que uma nova exportação seja incorporada ao relatório.

### O que acompanha o filtro

- ⭐ **Dados-chave:** acessos ao site e origens solicitadas pelo cliente.
- 🌐 **Site:** visitantes, novos visitantes, visualizações e interações.
- 📊 **Origem:** distribuição das sessões por canal.
- 🎯 **Leads:** leads, downloads, WhatsApp, cliques e buscas.

Os gráficos mensais, campanhas de Ads, páginas, artigos do blog, LinkedIn e planejamento continuam mostrando a base geral indicada em cada seção. Quando o filtro está fora do período completo, um aviso aparece no topo para deixar esse escopo explícito.

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

## Manutenção técnica

### Arquivos principais

- `ELOS_Relatorio_1S2026.html`: relatório, estilos, scripts e base diária incorporada.
- `index.html`: redirecionamento para o relatório.
- `elos-logo-full.png`: marca exibida no cabeçalho.
- `GUIA_USO_RELATORIO.md`: este manual.

### Atualizar os dados do GA4

1. Exporte no GA4 os dados diários do novo intervalo.
2. Preserve os campos usados no objeto `GA4_PRECISE`: usuários ativos, novos usuários, visualizações, eventos, leads, downloads, WhatsApp, cliques, buscas, sessões e origens.
3. Atualize `start`, `end`, `daily` e `activeRanges` dentro de `ELOS_Relatorio_1S2026.html`.
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

Sempre informe **métrica + dimensão + intervalo**. Exemplo correto: “31.771 sessões, agrupadas pelo canal da sessão, de 01/01/2026 a 12/07/2026”. Um mesmo período pode apresentar valores diferentes quando a métrica ou a dimensão muda.
