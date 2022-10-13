# Ensamblaje-de-genomas-bacterianos
Desde la obtención de las secuencias hasta el control de calidad del ensamblado


## Instructor 👨‍🏫  
Manuel Alain Ramírez Sáenz --> Llámame `MARS`

## Obtención de códigos SRA
Para desarrollar el proyecto trabajaremos con un conjunto de códigos ya submitidos a la base de datos del SRA-NCBI

* SRR17885111        
* SRR7628929
* SRR6927292
* SRR5155664
* SRR7284658
* SRR8177016
* SRR8177043
* SRR8177011
* SRR8177031
* SRR8177048
* SRR8177054
* SRR8177052
* SRR8177071
* SRR8544154
* SRR8544173
* SRR8544157
* SRR8177075
* SRR8177018
* SRR8177023

## Descargar archivos fastq usando for y fastq-dump

```
for sra in $(cat sra_lit_SG_brasil.txt); do fastq-dump --split-list $sra; done
```

## Estadística de los archivos fastq.gz

```
seqkit stat *.gz
```

Resultado

```
file                                      format  type   num_seqs      sum_len  min_len  avg_len  max_len
171024112201-1-1_S3_L001_R1_001.fastq.gz  FASTQ   DNA     638,458  194,729,690      305      305      305
171024112201-1-1_S3_L001_R2_001.fastq.gz  FASTQ   DNA     638,458  130,883,890      205      205      205
171024112202-1-1_S4_L001_R1_001.fastq.gz  FASTQ   DNA     681,614  207,892,270      305      305      305
171024112202-1-1_S4_L001_R2_001.fastq.gz  FASTQ   DNA     681,614  139,730,870      205      205      205
171024112203-1-1_S5_L001_R1_001.fastq.gz  FASTQ   DNA     831,386  253,572,730      305      305      305
171024112203-1-1_S5_L001_R2_001.fastq.gz  FASTQ   DNA     831,386  170,434,130      205      205      205
171024112204-1-1_S6_L001_R1_001.fastq.gz  FASTQ   DNA     627,177  191,288,985      305      305      305
171024112204-1-1_S6_L001_R2_001.fastq.gz  FASTQ   DNA     627,177  128,571,285      205      205      205
171024112205-1-1_S7_L001_R1_001.fastq.gz  FASTQ   DNA     636,584  194,158,120      305      305      305
171024112205-1-1_S7_L001_R2_001.fastq.gz  FASTQ   DNA     636,584  130,499,720      205      205      205
SRR17885111_1.fastq.gz                    FASTQ   DNA     590,700  145,666,060       35    246.6      301
SRR17885111_2.fastq.gz                    FASTQ   DNA     590,700  147,558,229       35    249.8      301
SRR5155664_1.fastq.gz                     FASTQ   DNA     730,859  172,793,817       35    236.4      251
SRR5155664_2.fastq.gz                     FASTQ   DNA     730,859  172,856,365       35    236.5      251
SRR6927292_1.fastq.gz                     FASTQ   DNA     939,422  229,738,545       35    244.6      251
SRR6927292_2.fastq.gz                     FASTQ   DNA     939,422  229,863,344       35    244.7      251
SRR7284658_1.fastq.gz                     FASTQ   DNA     850,351  127,583,982       35      150      151
SRR7284658_2.fastq.gz                     FASTQ   DNA     850,351  127,576,448       35      150      151
SRR7628929_1.fastq.gz                     FASTQ   DNA     658,096  162,621,531       35    247.1      251
SRR7628929_2.fastq.gz                     FASTQ   DNA     658,096  162,619,276       35    247.1      251
SRR8177011_1.fastq.gz                     FASTQ   DNA     960,517  143,538,094       35    149.4      151
SRR8177011_2.fastq.gz                     FASTQ   DNA     960,517  143,544,572       35    149.4      151
SRR8177016_1.fastq.gz                     FASTQ   DNA     743,142  109,655,441       35    147.6      151
SRR8177016_2.fastq.gz                     FASTQ   DNA     743,142  109,672,271       35    147.6      151
SRR8177018_1.fastq.gz                     FASTQ   DNA     754,109  112,743,488       35    149.5      151
SRR8177018_2.fastq.gz                     FASTQ   DNA     754,109  112,751,290       35    149.5      151
SRR8177023_1.fastq.gz                     FASTQ   DNA   1,451,329  215,602,291       35    148.6      151
SRR8177023_2.fastq.gz                     FASTQ   DNA   1,451,329  215,625,905       35    148.6      151
SRR8177031_1.fastq.gz                     FASTQ   DNA     924,852  138,260,940       35    149.5      151
SRR8177031_2.fastq.gz                     FASTQ   DNA     924,852  138,264,167       35    149.5      151
SRR8177043_1.fastq.gz                     FASTQ   DNA   1,421,929  212,486,416       35    149.4      151
SRR8177043_2.fastq.gz                     FASTQ   DNA   1,421,929  212,491,399       35    149.4      151
SRR8177048_1.fastq.gz                     FASTQ   DNA   1,681,927  247,196,846       35      147      151
SRR8177048_2.fastq.gz                     FASTQ   DNA   1,681,927  247,230,959       35      147      151
SRR8177052_1.fastq.gz                     FASTQ   DNA   1,274,977  190,386,902       35    149.3      151
SRR8177052_2.fastq.gz                     FASTQ   DNA   1,274,977  190,400,767       35    149.3      151
SRR8177054_1.fastq.gz                     FASTQ   DNA     983,608  147,358,919       35    149.8      151
SRR8177054_2.fastq.gz                     FASTQ   DNA     983,608  147,368,345       35    149.8      151
SRR8177071_1.fastq.gz                     FASTQ   DNA   1,076,073  155,750,827       35    144.7      151
SRR8177071_2.fastq.gz                     FASTQ   DNA   1,076,073  155,790,820       35    144.8      151
SRR8177075_1.fastq.gz                     FASTQ   DNA   1,060,242  156,924,593       35      148      151
SRR8177075_2.fastq.gz                     FASTQ   DNA   1,060,242  156,948,175       35      148      151
SRR8544154_1.fastq.gz                     FASTQ   DNA   1,392,525  207,820,102       35    149.2      151
SRR8544154_2.fastq.gz                     FASTQ   DNA   1,392,525  207,834,823       35    149.3      151
SRR8544157_1.fastq.gz                     FASTQ   DNA   1,323,724  196,586,326       35    148.5      151
SRR8544157_2.fastq.gz                     FASTQ   DNA   1,323,724  196,602,628       35    148.5      151
SRR8544173_1.fastq.gz                     FASTQ   DNA   1,516,384  226,176,882       35    149.2      151
SRR8544173_2.fastq.gz                     FASTQ   DNA   1,516,384  226,192,730       35    149.2      151
```

## Control de calidad de lecturas 

```
fastqc raw_data/*.fastq.gz -o results/fastqc
```

### Crear reporte de calidad de lecturas

```
cd results/fastqc
multiqc .
```
