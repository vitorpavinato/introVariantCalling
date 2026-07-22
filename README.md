# Introdução ao *Variant Calling*

Material de aula prática sobre **chamada de variantes** (*variant calling*), adaptado do
[Data Carpentry — Wrangling Genomics](https://datacarpentry.github.io/wrangling-genomics/),
episódios 4 e 5. O material foi convertido em **notebooks Jupyter** para rodar no
[Binder](https://mybinder.org), permitindo que os alunos executem os comandos ou acompanhem
a demonstração diretamente no navegador, sem instalar nada.

<!-- Substitua USUARIO/REPO pelo caminho do seu repositório no GitHub após o push -->
[![Binder](https://mybinder.org/badge_logo.svg)](https://mybinder.org/v2/gh/USUARIO/REPO/HEAD?labpath=notebooks)

## Notebooks

| Notebook | Conteúdo |
|----------|----------|
| `notebooks/04-variant-calling.ipynb` | Lição 4 — Alinhamento e chamada de variantes (`bwa`, `samtools`, `bcftools`) |
| `notebooks/05-....ipynb`             | Lição 5 — *(a definir)* |

## Ferramentas

Definidas em [`environment.yml`](environment.yml):

- **bwa** — alinhamento de *reads* ao genoma de referência
- **samtools** — manipulação de arquivos SAM/BAM
- **bcftools** — chamada e filtragem de variantes (VCF)
- **Jupyter + bash_kernel** — células executadas em Bash, idênticas ao terminal

## Dados

Os dados ficam em `data/`:

```
data/
├── ref_genome/            # genoma de referência de E. coli
├── trimmed_fastq_small/   # reads (subconjunto para caber no Binder)
└── results/               # saídas geradas durante a aula (não versionadas)
```

## Estrutura

```
introVariantCalling/
├── environment.yml   # ambiente conda (bioconda)
├── postBuild         # registra o kernel Bash no Binder
├── notebooks/        # notebooks das lições
└── data/             # dados de entrada e resultados
```
