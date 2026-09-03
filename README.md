# Portal do Cliente — mockup "dos sonhos"

Proposta visual e funcional do Portal do Cliente da Luminatti, construída a partir das críticas ao portal real
(SPS / SAP Business One) e dos quatro itens da proposta de melhorias V2 (CV 10542).

Mockup estático e autocontido: todo o HTML, CSS e JavaScript estão em [index.html](index.html),
sem dependências além da fonte Montserrat (Google Fonts). Não há backend. Os dados são fictícios,
gerados de forma determinística ao abrir a página, com as **notas fiscais como fonte única dos números**:
o gráfico, o placar, "por loja", os itens mais comprados, o histórico de preços e os boletos derivam delas,
então tudo fecha (clicar numa coluna do gráfico e somar as notas do mês dá exatamente o valor da coluna).

## Como visualizar

Abra o `index.html` direto no navegador, ou sirva a pasta localmente:

```bash
python -m http.server 8000
# depois acesse http://localhost:8000
```

Roteiro de demonstração:

- **Login**: e-mail já preenchido; qualquer senha entra. Senha vazia mostra o erro de campo; a senha `errada`
  mostra o erro de credencial. "Esqueci minha senha" tem o fluxo completo.
- **Seletor de loja** (topo): "Todas as lojas" soma as 3 lojas e marca "Consolidado"; escolher uma loja
  refaz todas as telas. Em consolidado, as tabelas ganham a coluna Loja e o toggle "Agrupar por loja".
- **Visão geral**: filtros de período (este mês, mês passado, 3/6/12 meses, este ano, ano passado,
  personalizado) e atalhos 2025 / 2026 / 2025 × 2026. Placar com variação, gráfico preto × amarelo,
  "Ver números", por loja, itens mais comprados e a zona "Hoje". Clique numa coluna abre as notas do mês.
- **O que falta chegar**: itens com quantidade pendente, por item ou por pedido, com previsão.
- **Itens e preços**: digite `dicroica` para ver o histórico de preços (último, médio ponderado, menor, maior).
- **Meus boletos**: clique em "Ver boleto" para a 2ª via com linha digitável, código de barras, Pix e valor
  atualizado. Títulos por transferência mostram os dados bancários.
- **Comunicações** (ou o sino): modelos de e-mail com o logo da Luminatti.
- `index.html?sessao=expirada` mostra o estado de sessão expirada. `Ctrl K` abre a busca global.

## Premissas adotadas (para validar com a diretoria)

- Nomenclatura na perspectiva de quem compra: "Notas fiscais de compra", "Meus pedidos",
  "O que falta chegar", "Meus boletos". Títulos em aberto e em atraso viraram uma página só.
- Sem ilustrações genéricas (astronauta): login, estados vazios e erros usam a identidade Luminatti.
- Cliente de exemplo com 3 lojas para provar que o dashboard soma.
- Valor atualizado do boleto = original + multa 2% + juros 1% a.m.; regra a confirmar com o financeiro.
- As caixas "Para a SPS" no fim de cada tela apontam a origem dos dados no SAP B1.

## Escopo

Este repositório contém apenas a camada de apresentação para validação de design.
Não é código de produção. A versão anterior do mockup (espelho do portal atual) está no histórico do git.
