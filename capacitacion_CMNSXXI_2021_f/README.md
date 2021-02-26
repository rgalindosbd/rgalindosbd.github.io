# Capacitación 

## Sesión 1

A continuación se presenta una guía rápida para usar los comandos vistos en la capacitación

```Shell
## Acomodo de los archivos 

for i in $(ls /home/labseq/SolariaBiodata/testing/reads202012/); do ln -s /home/labseq/SolariaBiodata/testing/reads202012/$i $i; done
for i in $(ls | cut -d "_" -f-2 | uniq); do mkdir $i; mv ${i}*gz $i; done

## Preprocesamiento de las lecturas

./filtradorLecturas_mismaMuestra.sh /home/umaelab/SolariaBiodata/testing/input/ /home/umaelab/SolariaBiodata/testing/t_out/ 12 30 50
```

## Sesión 2

```Shell
## Ensamble guiado por referencia

./ensamblador.sh /home/umaelab/SolariaBiodata/testing/t_out/ 16 HY2TMBGXF 20200216 NS500707
./combinaEnsamble_porMuestra.sh /home/umaelab/SolariaBiodata/testing/t_out/

## Procesamiento del alineamiento

./realineadorLecturas_shotgun.sh /home/umaelab/SolariaBiodata/testing/t_out/bySAMPLE/ 16 /home/umaelab/SolariaBiodata/produccion/hglft_genome_6ffb1_e12b90.bed
./recalibradorCalidadBases.sh /home/umaelab/SolariaBiodata/testing/t_out/bySAMPLE/ 16

```

## Sesión 3


```Shell
## Llamado de variantes

./llamadorVariantes_HCgvcf.sh /home/umaelab/SolariaBiodata/testing/t_out/bySAMPLE/ "-Xmx4g" /home/umaelab/SolariaBiodata/produccion/hglft_genome_6ffb1_e12b90.bed
./genotipificadorPoblacional_gvcf.sh /home/umaelab/SolariaBiodata/testing/t_out/bySAMPLE/ /home/umaelab/SolariaBiodata/produccion/hglft_genome_6ffb1_e12b90.bed "-Xmx4g"

## Procesamiento de las variantes

./filtradorVariantes_HF.sh /home/umaelab/SolariaBiodata/testing/t_out/bySAMPLE/
./correctorFase.sh /home/umaelab/SolariaBiodata/testing/t_out/bySAMPLE/ 4
./maestro_varAnot.sh /home/umaelab/SolariaBiodata/testing/t_out/bySAMPLE/ GRCh38.p13.RefSeq

```

## Sesión 04


```Shell

## Ancestria

./ancestria.sh /home/umaelab/SolariaBiodata/testing/t_out/bySAMPLE/ /home/umaelab/SolariaBiodata/databases/1kg/peds/interval_AIMS_dbsnp.txt /home/umaelab/SolariaBiodata/databases/1kg/peds/integrated_call_samples_v3.20130502.ALL.panel test

## Analisis de metilacion

cd /ruta/de/archivos/bicycle
/opt/bin/bicycle-1.8.2/cmd/bicycle create-project -p bicycle-case-study-project -r referenceGenome -f raw_data --paired-mate1-regexp _1.fastq
/opt/bin/bicycle-1.8.2/cmd/bicycle align -p bicycle-case-study-project -t 4 --bowtie2-quals phred33 --bowtie2-I 0 --bowtie2-X 500
/opt/bin/bicycle-1.8.2/cmd/bicycle analyze-methylation -p bicycle-case-study-project  -c SRR2052487,SRR2052488,SRR2052489,SRR2052490,SRR2052491 -t 4 -b target_regions.bed

```


Más detalles en  [Solaria Biodata](http://solariabiodata.com.mx).
