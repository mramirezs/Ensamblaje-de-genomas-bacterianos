# Ensamblaje-de-genomas-bacterianos
Desde la obtención de las secuencias crudas hasta el control de calidad del ensamblado


## Instructor 👨‍🏫  
Manuel Alain Ramírez Sáenz --> Llámame `MaRS`

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
mkdir raw_data
cd raw_data
for file in $(cat sra_list.txt); do fastq-dump --split-files $file; done
```

## Estadística de los archivos fastq.gz

```
cd raw_data
seqkit stat *.fastq.gz # Usando el comando seqkit
```

El resultado de esa linea de comandos es:

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

```
cd .. # Regresamos a la carpeta de trabajo principal
```

## Control de calidad de lecturas 

```
fastqc raw_data/*.fastq.gz -o results/fastqc
```

### Crear reporte de calidad de lecturas

```
multiqc results/fastqc -o results/fastqc
```

### Reporte Multiqc

![Estadísticas generales](https://github.com/mramirezs/Ensamblaje-de-genomas-bacterianos/blob/main/fig/multiqc_general_statistics.png)

## Recorte de adaptadores y filtrado de calidad de lecturas

Para muestras con patron _L001_R1_001.fastq.gz, _L001_R2_001.fastq.gz:

```
cd raw_data
for file in $(ls *_L001_R1_001.fastq.gz | sed 's/_L001_R1_001.fastq.gz//'); do trimmomatic PE -threads 10 -phred33 ${file}_L001_R1_001.fastq.gz ${file}_L001_R2_001.fastq.gz ../results/trimmomatic/${file}_L001_R1_001.paired.fastq.gz ../results/trimmomatic/${file}_L001_R1_001.unpaired.fastq.gz ../results/trimmomatic/${file}_L001_R2_001.paired.fastq.gz ../results/trimmomatic/${file}_L001_R2_001.unpaired.fastq.gz ILLUMINACLIP:../adapters.fasta:2:30:10 LEADING:3 TRAILING:3 SLIDINGWINDOW:4:20 MINLEN:50;done
```

Para muestrsas con patron _1.fastq.gz, _2.fastq.gz: 

```
for file in $(ls *_1.fastq.gz | sed 's/_1.fastq.gz//'); do trimmomatic PE -threads 10 -phred33 ${file}_1.fastq.gz ${file}_2.fastq.gz ../results/trimmomatic/${file}_1.paired.fastq.gz ../results/trimmomatic/${file}_1.unpaired.fastq.gz ../results/trimmomatic/${file}_2.paired.fastq.gz ../results/trimmomatic/${file}_2.unpaired.fastq.gz ILLUMINACLIP:../adapters.fasta:2:30:10 LEADING:3 TRAILING:3 SLIDINGWINDOW:4:15 MINLEN:50;done
 ```

### Revisar la estadìstica y calidad de lecturas de las lecturas trimadas

```
seqkit stat results/trimmomatic/*.fastq.gz
```

Cuyo resultado es: 

```

```

De igual forma se realiza el anàlisis con fastqc y se obtiene su reporte por multiqc. 

```
mkdir trimmomatic/fastqc
fastqc results/trimmomatic/*.fastq.gz -o results/trimmomatic/fastqc
multiqc results/trimmomatic/fastqc -o results/trimmomatic/fastqc
```

## Identificación de especies 

Para muestrsas con patron 1.fastq.gz

```
for file in $(ls *_L001_R1_001.paired.fastq.gz | sed 's/_L001_R1_001.paired.fastq.gz//'); do kraken2 --db /media/olimpo/96e671b0-3d95-4c39-8527-47c7eb9c8b7a1/Databases/k2_standard_08gb_20220926  --threads 16 --report ../kraken2/${file}.kreport --paired ${file}_L001_R1_001.paired.fastq.gz ${file}_L001_R1_001.paired.fastq.gz > ../kraken2/${file}.trimmed.kraken2;done
```

Para muestras con patron L001_R1_001.fastq.gz

```
for file in $(ls *_1.paired.fastq.gz | sed 's/_1.paired.fastq.gz//'); do kraken2 --db /media/olimpo/96e671b0-3d95-4c39-8527-47c7eb9c8b7a1/Databases/k2_standard_20220926  --threads 16 --report ../kraken2/${file}.kreport --paired ${file}_1.paired.fastq.gz ${file}_2.paired.fastq.gz > ../kraken2/${file}.trimmed.kraken2;done 

```

### Visualización de las especies identificadas

```
cd kraken2
for file in $(ls *.kreport | sed 's/kreport//'); do cat ${file}.trimmed.kraken2 | cut -f 2,3 > ${file}.cut.trimmed.kraken2;done
```

#### Krona 

```
for file in $(ls *.kreport | sed 's/kreport//'); do ktImportTaxonomy -o ../krona/${file}.html ${file}.cut.trimmed.kraken2;done
```

## Ensamblaje de genoma

```
cd trimmmomatic
for file in $(ls *_L001_R1_001.paired.fastq.gz | sed 's/_L001_R1_001.paired.fastq.gz//'); do spades.py --careful -t 20 -o ../spades/${file} -1 ${file}_L001_R1_001.paired.fastq.gz -2 ${file}_L001_R2_001.paired.fastq.gz;done
```

```
for file in $(ls *_1.paired.fastq.gz | sed 's/_1.paired.fastq.gz//'); do spades.py --careful -t 20 -o ../spades/${file} -1 ${file}_1.paired.fastq.gz -2 ${file}_2.paired.fastq.gz;done
```

### Obtener secuencias de alta cobertura (cov >= 2, length >= 500)


```
for file in $(ls *_L001_R1_001.paired.fastq.gz | sed 's/_L001_R1_001.paired.fastq.gz//'); do grep -F '>' ../spades//${file}/contigs.fasta | sed -e 's/_/ /g' | sort -nrk 6 | awk '$6>=2.0 && $4>=500 {print $0}' | sed -e 's/ /_/g' | sed -e 's/>//g' > ../spades/${file}.contigs.txt;done
```

```
for file in $(ls *_L001_R1_001.paired.fastq.gz | sed 's/_L001_R1_001.paired.fastq.gz//'); do fastagrep.pl -f ../spades/${file}.contigs.txt ../spades/${file}/contigs.fasta > ../spades/${file}.HCov.contigs.fasta;done
```


```
for file in $(ls *_1.paired.fastq.gz | sed 's/_1.paired.fastq.gz//'); do grep -F '>' ../spades//${file}/contigs.fasta | sed -e 's/_/ /g' | sort -nrk 6 | awk '$6>=2.0 && $4>=500 {print $0}' | sed -e 's/ /_/g' | sed -e 's/>//g' > ../spades/${file}.contigs.txt;done


```
for file in $(ls *_1.paired.fastq.gz | sed 's/_1.paired.fastq.gz//'); do fastagrep.pl -f ../spades/${file}.contigs.txt ../spades/${file}/contigs.fasta > ../spades/${file}.HCov.contigs.fasta;done
```

```

## Control de ensamblaje

```
for i in $(ls *_L001_R1_001.paired.fastq.gz | sed 's/_L001_R1_001.paired.fastq.gz//');do quast.py --output-dir ../quast/${i}_ref -r ../../reference/NC_011274.fasta -t 8 ../spades/${i}.HCov.contigs.fasta;done
```

```
for i in $(ls *_1.paired.fastq.gz | sed 's/_1.paired.fastq.gz//'); do quast.py --output-dir ../quast/${i}_ref -r ../../reference/NC_011274.fasta -t 8 ../spades/${i}.HCov.contigs.fasta;done
```

### Anotar con PGAP

Primero crearemos los archivos de configuración yaml:

```
cd trimmomatic
for file in $(ls *_L001_R1_001.paired.fastq.gz | sed 's/_L001_R1_001.paired.fastq.gz//'); do touch ../pgap/$file.input.yaml && touch ../pgap/$file.submol.yaml; done
```

```
for file in $(ls *_1.paired.fastq.gz | sed 's/_1.paired.fastq.gz//'); do touch ../pgap/$file.input.yaml && touch ../pgap/$file.submol.yaml; done
```

Escribir en archivos submol.yaml
```
cd pgap
for file in $(ls *.submol.yaml | sed 's/.submol.yaml//'); do echo -e "topology: 'circular'\nlocation: 'chromosome'\norganism:\n  genus_species: 'Salmonella enterica'" > $id.submol.yaml; done
```

Escribir en archivos input.yaml
```
for file in $(ls *.submol.yaml | sed 's/.submol.yaml//'); do echo -e "fasta:\n  class: File\n  location: ../spades/$file.HCov.contigs.fasta\nsubmol:\n  class: File\n  location: $file.submol.yaml" > $file.input.yaml; done
```

Procedemos a anotar: 

```
cd pgap
for file in $(ls *.submol.yaml | sed 's/.submol.yaml//'); do pgap.py -D singularity -r --no-internet -d  $file.input.yaml -o $file; done
```
