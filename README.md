<p style="margin:0; padding:0;"><img src="images/logo_infnet.png" alt="Logotipo do Instituto Infnet" style="height: 100px; width: auto; vertical-align: middle;"/></p>

# Projeto de Disciplina — Validação de Modelos de Clusterização
<img src="https://img.shields.io/badge/python-v._3.13.5-blue?style=flat-square&logo=python&logoColor=white" alt="python_logo" height="20"/>
<img src="https://img.shields.io/badge/jupyter-v._5.9.1-blue?style=flat-square&logo=jupyter&logoColor=white" alt="jupyter_logo" height="20"/>

- Fabio Ferreira Figueiredo <a href="https://github.com/fabioffigueiredo/pd_modelos_clusterizacao"><img src="https://img.shields.io/badge/Github-151b23?style=flat-square&logo=github" alt="github_logo" height="20"/></a>

# Projeto de Disciplina — Validação de Modelos de Clusterização

Resumo do projeto, como executar localmente, estrutura de pastas, decisões técnicas e próximos passos. Este README segue boas práticas: visão geral clara, requisitos, instalação, execução, troubleshooting e roadmap. Soluções simples e reprodutíveis, considerando dev/test/prod.

## Visão Geral
- Objetivo: agrupar países a partir de dados socioeconômicos e de saúde (K-Means/DBSCAN) e analisar similaridade em séries temporais.
- Abordagens: K‑Means (K‑Médias), Hierárquica (Ward) e DBSCAN, com comparação de métricas (Silhouette, Calinski-Harabasz). Inclui análise de Séries Temporais (Correlação Cruzada e DTW).
- Entregáveis principais:
  - Notebook completo: `Projeto_Clusterizacao_parte2.ipynb` (atende a todos os requisitos: infra, dados, clusterização e séries temporais).
  - Notebook base: `Projeto_Clusterizacao_parte1.ipynb`.

## Base de Dados
- Fonte: Kaggle — `rohan0301/unsupervised-learning-on-country-data`.
- Arquivos locais (pasta `data/`):
  - `Country-data.csv`: base principal.
  - `data-dictionary.csv`: dicionário de variáveis.

## Estrutura de Pastas
```
├── Projeto_Clusterizacao_parte1.ipynb
├── Projeto_Clusterizacao_parte2.ipynb
├── README.md
├── data/
│   ├── Country-data.csv
│   └── data-dictionary.csv
├── fabioferreirafigueiredo_algoritmosdeinteligenciaartificialparaclusterizacao_pd.pdf
├── images/
│   ├── boxplots_variaveis_numericas.png
│   ├── dendrograma_ward_truncado.png
│   ├── evidenciass.png
│   ├── histogramas_variaveis_numericas.png
│   ├── logo_infnet.png
│   ├── pca_2d_clusters.png
│   └── perfil_clusters_barras.png
├── pd_algoritimos_clusterizacao/
└── requirements.txt
```

## Requisitos
- Python 3.9+ (desenvolvido e testado com 3.13.5).
- Jupyter (versão usada: 5.9.1).
- Pacotes: `numpy`, `pandas`, `scikit-learn`, `scipy`, `matplotlib`, `seaborn`, `kaggle` (opcional para download).
- Navegador para visualizar os HTMLs.

## Instalação (dev/test/prod)
1) Crie e ative um ambiente virtual (recomendado):
```
python3 -m venv clusterizacao
source clusterizacao/bin/activate    # macOS/Linux
# No Windows (PowerShell):
# .\clusterizacao\Scripts\Activate.ps1
```

2) Instale as dependências:
```
pip install -r requirements.txt
```

3) Dados:
- Se usar Kaggle API, configure previamente suas credenciais. Caso prefira, copie `Country-data.csv` e `data-dictionary.csv` diretamente para `data/`.
- Base de dados - usadas para o PD parte 1 e parte 2: https://www.kaggle.com/datasets/rohan0301/unsupervised-learning-on-country-data

Observações de ambiente:
- Não sobrescreva arquivos `.env` sem confirmação (não são necessários para execução padrão deste projeto).
- Padronize `random_state` e caminhos em um único bloco de configuração quando estender o projeto para múltiplos ambientes.

## Git (repositório e clonagem)
- Repositório oficial: https://github.com/fabioffigueiredo/pd_modelos_clusterizacao

Como clonar e preparar o ambiente local:
```
git clone https://github.com/fabioffigueiredo/pd_modelos_clusterizacao.git
cd pd_modelos_clusterizacao

# (opcional) criar e ativar ambiente virtual
python3 -m venv clusterizacao
source clusterizacao/bin/activate    # macOS/Linux
# No Windows (PowerShell):
# .\clusterizacao\Scripts\Activate.ps1

# instalar dependências
pip install -r requirements.txt

## Quick Start (execução mínima)
```
python3 -m venv clusterizacao
source clusterizacao/bin/activate    # macOS/Linux
pip install -r requirements.txt


# Servir localmente
```
python3 -m http.server 8002
Acesse: http://localhost:8002/Projeto_Clusterizacao_parte2.html
```
Se preferir interação, rode `jupyter notebook` e execute `Projeto_Clusterizacao_parte2.ipynb` célula a célula.

## Como Executar
### A) Rodar os notebooks no Jupyter
1) Ative o venv e inicie o Jupyter:
```
jupyter notebook
```
2) Abra e execute:
- `Projeto_Clusterizacao_parte2.ipynb` (versão completa com Séries Temporais e DBSCAN).
- `Projeto_Clusterizacao_parte1.ipynb` (versão base).


### B) Gerar HTML a partir dos notebooks
Execute os comandos na raiz do projeto:
```
jupyter nbconvert --to html --execute Projeto_Clusterizacao_parte2.ipynb --output Projeto_Clusterizacao_parte2.html
jupyter nbconvert --to html --execute Projeto_Clusterizacao_executado.ipynb --output Projeto_Clusterizacao_executado.html
```

### C) Visualizar localmente os HTMLs
Inicie um servidor simples e abra no navegador:
```
python3 -m http.server 8002
```
### Navegue para:
http://localhost:8002/Projeto_Clusterizacao_parte2.html
Se a porta estiver ocupada, altere para 8001/8003.

### D) Gerar PDF
Você pode exportar o notebook para PDF:
```
jupyter nbconvert --to pdf Projeto_Clusterizacao_parte2.ipynb
```
Ou imprimir o HTML em PDF via navegador.


## Metodologia (resumo)
1) EDA: estatísticas descritivas, histogramas, boxplots, verificação de outliers.
2) Pré-processamento: padronização com `StandardScaler`.
3) Redução de dimensionalidade: `PCA` para visualização (2D) e análise de variância explicada.
4) Clusterização:
   - K‑Means (variação com centróides). Seleção de `k` com Elbow/Silhouette.
   - Hierárquica (Ward) com dendrograma truncado para inspeção dos agrupamentos.
5) Interpretação: perfis por cluster com médias normalizadas e gráficos de barras comparativos.
6) Validação e Comparação: Comparação direta entre K-Means e DBSCAN (vantagens/desvantagens) e índices de validação.
7) Séries Temporais: Estratégias de agrupamento usando Correlação Cruzada Máxima e DTW.

## Resultados e Evidências
- Gráficos e imagens em `images/` (PCA em 2D, dendrograma, perfil dos clusters, histogramas e boxplots).
- Interpretação detalhada dos clusters no corpo dos notebooks.
- HTMLs e PDF para consulta rápida.

## Troubleshooting
- Aviso de acessibilidade (alt text):
  - Nbconvert pode sinalizar imagens sem `alt`. A logo e os principais gráficos possuem/descrevem `alt`, mas se o aviso persistir, adicione `alt` às imagens renderizadas manualmente.
- Porta ocupada no servidor local:
  - Use outra porta: `python3 -m http.server 8001`.
- Pacotes faltando:
  - Reinstale: `pip install -r requirements.txt` e confira se o venv está ativo.
- Kaggle API:
  - Sem credenciais, copie os CSVs para `data/` e execute.
 - Logo grande/desproporcional:
   - O cabeçalho foi ajustado para não herdar estilos de H1. No primeiro bloco markdown do notebook, a imagem está fora do título e usa estilo inline:
     - `style="height: 100px; width: auto; vertical-align: middle;"`
     - Para alterar, ajuste apenas o `height` (ex.: 80px/120px) mantendo `width: auto` para preservar a proporção.

## Boas Práticas adotadas
- Preferência por soluções simples e sem duplicação de código.
- Consideração de ambientes (dev/test/prod); recomendação de centralizar configurações.
- Notebooks com interpretação clara e gráficos gerados de forma reprodutível.

## Roadmap e Próximos Passos
- Extrair rotinas de visualização para um módulo Python (ex.: `clusterizacao/viz.py`) e importar nos notebooks para reduzir duplicação e facilitar testes.
- Padronizar bloco de configuração (parâmetros de `k`, `random_state`, caminhos de saída) e permitir override por variável de ambiente (sem sobrescrever `.env`).
- Automatizar conversões (HTML/PDF) via `make html`/`make pdf` ou script `tasks.py`.
- Adicionar testes simples (ex.: validação de existência de colunas, shapes esperados e cálculo de médias por cluster).
- Incluir CI (ex.: GitHub Actions) para validar execução do notebook e geração de artefatos.

## Checklist de Submissão
- venv criado e ativado; dependências instaladas via `requirements.txt`.
- Notebook executado sem erros; gráficos gerados em `images/`.
- HTML gerado com `nbconvert` e validado no navegador.
- PDFs gerados (`Projeto_Clusterizacao.pdf` e/ou `Projeto_Clusterizacao2.pdf`) quando necessário.
- Avisos de acessibilidade (alt text) revisados; adicionar `alt` se aplicável.
- Commit das alterações com mensagem clara e organização da estrutura.

## Autor
- Fabio Ferreira Figueiredo — Repositório: `pd_modelos_clusterizacao`


