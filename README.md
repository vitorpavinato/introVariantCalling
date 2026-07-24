# Introdução ao *Variant Calling*

Material de aula prática sobre **chamada de variantes** (*variant calling*), adaptado do
[Data Carpentry — Wrangling Genomics](https://datacarpentry.github.io/wrangling-genomics/),
episódios 4 e 5. O material foi convertido em **notebooks Jupyter** para rodar no
[Binder](https://mybinder.org), permitindo que os alunos executem os comandos ou acompanhem
a demonstração diretamente no navegador, sem instalar nada.

[![Binder](https://mybinder.org/badge_logo.svg)](https://mybinder.org/v2/gh/vitorpavinato/introVariantCalling/HEAD?labpath=notebooks%2Fvariant-calling.ipynb)

## Notebooks

| Notebook | Conteúdo |
|----------|----------|
| `notebooks/variant-calling.ipynb` | Chamada de variantes a partir de um alinhamento pronto: inspeção e indexação do BAM, `bcftools mpileup`/`call`, filtragem, e visualização com `samtools tview` + IGV-Web |
| `notebooks/05-....ipynb`          | Lição 5 — *(a definir)* |

### Visualização no IGV-Web

A última seção usa o [IGV-Web](https://igv.org/app/) — roda no navegador, sem instalação.
Para isso, três arquivos pequenos são versionados: a referência `ecoli_rel606.fasta`,
seu índice `.fai` (exigido pelo IGV) e o VCF filtrado `SRR2584866_final_variants.vcf`.

## Ferramentas

Definidas em [`environment.yml`](environment.yml):

- **samtools** — manipulação de arquivos SAM/BAM
- **bcftools** — chamada e filtragem de variantes (VCF)

> O alinhamento (`bwa`) foi feito na etapa de preparação; a aula parte de um BAM já
> ordenado, então `bwa` não faz parte do ambiente do Binder.
- **Jupyter + bash_kernel** — células executadas em Bash, idênticas ao terminal

## Dados

O layout segue o do episódio do Data Carpentry: entradas em `data/`, saídas em `results/`.

```
data/
├── ref_genome/            # genoma de referência (versionado)
└── trimmed_fastq_small/   # reads trimmed (não versionados; só usados na preparação)

results/
├── bam/                   # alinhamentos — o BAM ordenado inicial é versionado
├── sam/, bcf/, vcf/       # saídas geradas durante a aula (não versionadas)
```

**Genoma de referência:** *Escherichia coli* B str. **REL606** (`NC_012967.1` / `CP000819.1`),
4.629.812 bp, obtido do [dataset oficial do Data Carpentry no figshare](https://figshare.com/articles/dataset/Data_Carpentry_Genomics_beta_2_0/7726454).

> ⚠️ Duas armadilhas conhecidas: o link do NCBI citado na página do episódio
> (`GCA_000017985.1_ASM1798v1`) baixa um arquivo corrompido; e **não** se deve usar
> o genoma de *E. coli* K-12 MG1655 (ASM584v2, 4.641.652 bp) — os *reads* são da
> linhagem B/REL606, e mapeá-los contra K-12 gera ~31.000 variantes (divergência
> entre linhagens) em vez das ~800 esperadas.

Com a referência correta, o pipeline produz **792 variantes brutas → 775 após filtragem**.

## Estrutura

```
introVariantCalling/
├── environment.yml   # ambiente conda (bioconda)
├── postBuild         # registra o kernel Bash no Binder
├── notebooks/        # notebooks das lições
├── data/             # dados de entrada
└── results/          # saídas da aula
```
