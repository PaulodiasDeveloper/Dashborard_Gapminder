# Dashboard Interativo Gapminder

Um aplicativo web interativo desenvolvido com **Dash** e **Plotly** que visualiza dados históricos do Gapminder, permitindo explorar a evolução da relação entre desenvolvimento econômico, saúde e população mundial de 1952 a 2007.

## 🎯 Funcionalidades

- **Visualização Interativa**: Gráfico de dispersão (scatter plot) que mostra a correlação entre PIB per capita e expectativa de vida
- **Controle Temporal**: Slider para navegar através dos anos (1952-2007)
- **Análise Multidimensional**: 
  - Tamanho das bolhas representa a população do país
  - Cores diferentes para cada continente
  - Escala logarítmica no eixo X para melhor visualização do PIB
- **Hover Dinâmico**: Informações detalhadas ao passar o mouse sobre cada país
- **Transições Suaves**: Animações de 500ms entre as mudanças de ano

## 📊 Sobre os Dados

O dataset utilizado contém informações históricas de diversos países com as seguintes variáveis:
- **country**: Nome do país
- **year**: Ano (1952-2007, intervalos de 5 anos)
- **pop**: População
- **continent**: Continente
- **lifeExp**: Expectativa de vida (anos)
- **gdpPercap**: PIB per capita (USD)

**Fonte**: [Gapminder Dataset - Plotly GitHub](https://raw.githubusercontent.com/plotly/datasets/master/gapminderDataFiveYear.csv)

## 🚀 Como Executar

### Pré-requisitos

```bash
pip install dash plotly pandas
```

### Instalação e Execução

1. **Clone ou baixe o arquivo `callback_app2.py`**

2. **Execute o aplicativo**:
```bash
python callback_app2.py
```

3. **Acesse no navegador**:
```
http://localhost:8050
```

## 🏗️ Estrutura do Código

### Componentes Principais

```python
# Layout da aplicação
app.layout = html.Div([
    dcc.Graph(id='graph-with-slider'),      # Gráfico principal
    dcc.Slider(id='year-slider', ...)       # Controle temporal
])

# Callback para interatividade
@app.callback(
    Output('graph-with-slider', 'figure'),
    [Input('year-slider', 'value')]
)
def update_figure(selected_year):
    # Lógica de filtragem e atualização do gráfico
```

### Fluxo de Funcionamento

1. **Carregamento**: Dados são importados do CSV online
2. **Renderização**: Layout inicial é exibido com o primeiro ano
3. **Interação**: Usuário move o slider
4. **Callback**: Função `update_figure()` é triggered
5. **Filtragem**: Dados são filtrados pelo ano selecionado
6. **Atualização**: Gráfico é re-renderizado com transição suave

## 📈 Insights Possíveis

Este dashboard permite identificar padrões como:

- **Crescimento Econômico**: Evolução do PIB per capita por região
- **Melhoria da Saúde**: Aumento da expectativa de vida ao longo do tempo
- **Disparidades Regionais**: Diferenças entre continentes
- **Correlação PIB-Saúde**: Relação entre desenvolvimento econômico e expectativa de vida
- **Crescimento Populacional**: Variação do tamanho das populações

## 🛠️ Tecnologias Utilizadas

- **[Dash](https://dash.plotly.com/)**: Framework web para aplicações analíticas
- **[Plotly Express](https://plotly.com/python/plotly-express/)**: Biblioteca de visualização
- **[Pandas](https://pandas.pydata.org/)**: Manipulação e análise de dados
- **HTML/CSS**: Interface e estilização

## 🔧 Possíveis Melhorias

- [ ] Adicionar filtros por continente/país
- [ ] Implementar análise de tendências
- [ ] Incluir mais métricas (IDH, inflação, etc.)
- [ ] Adicionar opções de exportação
- [ ] Implementar cache para melhor performance
- [ ] Adicionar testes unitários
- [ ] Criar dockerfile para deploy

## 📝 Notas Técnicas

- **Porto padrão**: 8050
- **Modo debug**: Habilitado (recarregamento automático)
- **Responsividade**: Layout adaptativo via CSS externo
- **Performance**: Dados carregados uma única vez na inicialização

## 🤝 Contribuições

Sinta-se à vontade para contribuir com melhorias, correções ou novas funcionalidades através de pull requests.

## 📄 Licença

Este projeto utiliza dados públicos do Gapminder e está disponível para uso educacional e de pesquisa.

