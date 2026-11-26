# Clustering Research

> Por trás de cada tentativa, existe uma trajetória de aprendizagem. O desafio é encontrar os padrões que os números, sozinhos, não revelam.

A popularização da inteligência artificial generativa traz novas perguntas para o ensino de programação: **como os alunos constroem suas soluções e o que muda nesse processo ao longo do tempo?**

Este projeto de iniciação científica investiga registros de atividades de estudantes no CodeBench para explorar essas perguntas com ciência de dados. A proposta é utilizar **clustering** para identificar perfis de resolução de exercícios e investigar como sua frequência varia entre diferentes semestres, no contexto da disponibilidade de ferramentas de IA.

<p align="center">
  <img src="assets/clustering-nvidia.png" alt="Ilustração de clustering: pontos organizados em cinco grupos, com seus respectivos centros." width="760">
  <br>
  <sub>Ilustração de agrupamento de dados · Crédito: NVIDIA.</sub>
</p>

## Pergunta de pesquisa

**Quais perfis de resolução aparecem nos logs dos alunos e como eles se distribuem ao longo dos semestres?**

## Ponto de partida

O estudo começará com um recorte de exercícios e características como quantidade de submissões, tempo ativo estimado, edições e intervalos entre tentativas. Com **Python, pandas e scikit-learn**, serão exploradas a qualidade dos dados, a formação de grupos e sua interpretação no contexto educacional.

Os logs permitem observar comportamentos registrados, mas **não comprovam, isoladamente, o uso de IA ou seus efeitos sobre a aprendizagem**. Essa distinção orienta a interpretação dos resultados.

## Organização do projeto

A organização foi adaptada do **Cookiecutter Data Science v2**, projeto mantido pela **DrivenData**, com estrutura e princípios publicados em sua documentação oficial. Essa é nossa referência documentada de organização; trata-se de um modelo de projeto, e não de uma norma acadêmica obrigatória.

- [Estrutura oficial do Cookiecutter Data Science](https://cookiecutter-data-science.drivendata.org/#directory-structure)
- [Princípios de organização e adaptação](https://cookiecutter-data-science.drivendata.org/opinions/)

Mantivemos a separação entre dados, exploração, código reutilizável e resultados. Adaptamos os nomes dos notebooks e módulos para o estudo dos logs do CodeBench e acrescentamos espaço para a proposta e as reuniões. A estrutura foi criada manualmente com base na referência; o gerador do template não foi executado.

```text
Clustering-Research/
├── README.md
├── .gitignore
├── requirements.txt
├── pyproject.toml
├── assets/                         # Imagens de apresentação do projeto
├── data/
│   ├── raw/                        # Logs originais, preservados sem alterações
│   ├── interim/                    # Dados limpos e normalizados
│   └── processed/                  # Tabelas de características para análise
├── docs/
│   ├── proposta.md                 # Objetivo e definições pendentes do piloto
│   └── reunioes/                   # Pautas, decisões e próximos passos
├── references/
│   ├── dicionario-dados.md          # Significado e cálculo das variáveis
│   └── descricao-dos-logs.md        # Origem, formatos e limites dos registros
├── notebooks/
│   ├── 01_exploracao_dos_logs.ipynb
│   ├── 02_construcao_das_variaveis.ipynb
│   ├── 03_clustering_inicial.ipynb
│   └── 04_comparacao_entre_semestres.ipynb
├── clustering_research/
│   ├── __init__.py
│   ├── dataset.py                  # Carregamento e normalização
│   ├── features.py                 # Construção das características
│   ├── clustering.py               # Agrupamento e avaliação
│   └── plots.py                    # Visualizações
├── models/                         # Pipelines e modelos ajustados, locais
└── reports/
    ├── README.md                   # Informações a registrar por experimento
    ├── figures/                    # Gráficos para análise e comunicação
    └── tables/                     # Tabelas agregadas dos resultados
```

### Como trabalhar

O fluxo previsto é **logs originais → normalização → características → clustering → interpretação e comparação entre semestres**.

Os notebooks servem para explorar e explicar as análises. Funções que forem reutilizadas passam para o pacote `clustering_research`. Os notebooks iniciais contêm apenas o objetivo de cada etapa; os módulos Python ainda não implementam o processamento.

Os dados em `data/` e os artefatos em `models/` ficam fora do Git, exceto pelos arquivos `.gitkeep`, que preservam as pastas vazias. Os dados dos estudantes não acompanham este repositório público. Antes de publicar notebooks, gráficos ou tabelas, revisar também suas saídas para evitar exposição de registros individuais.

Cada experimento deve documentar o recorte dos dados, as variáveis, as transformações, os parâmetros, a semente aleatória e as versões do código e do ambiente. O roteiro está em [reports/README.md](reports/README.md).

## Ambiente de desenvolvimento

Com Python 3.10 ou superior, execute na raiz do projeto, usando PowerShell:

```powershell
python -m venv .venv
.\.venv\Scripts\python.exe -m pip install -r requirements.txt
.\.venv\Scripts\python.exe -m jupyterlab
```

O `pyproject.toml` configura o pacote local e declara as dependências iniciais: NumPy, pandas, scikit-learn, Matplotlib e JupyterLab. O `requirements.txt` instala esse pacote em modo editável. As versões ainda não estão fixadas; deverão ser registradas para reproduzir os experimentos.

---

**Status:** fase inicial de definição do escopo e estudo da metodologia.
