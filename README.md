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
for sra in $(cat sra_lit_SG_brasil.txt);
do
  fastq-dump --split-list $sra
done
```
