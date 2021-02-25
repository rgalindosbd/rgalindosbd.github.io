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

./llamadorVariantes_HCgvcf.sh /home/umaelab/SolariaBiodata/testing/t_out/bySAMPLE/ "-Xmx4g" /home/umaelab/SolariaBiodata/produccion/hglft_genome_6ffb1_e12b90.bed 16
./genotipificadorPoblacional_gvcf.sh /home/umaelab/SolariaBiodata/testing/t_out/bySAMPLE/ /home/umaelab/SolariaBiodata/produccion/hglft_genome_6ffb1_e12b90.bed "-Xmx4g"

## Procesamiento de las variantes

./filtradorVariantes_HF.sh /home/umaelab/SolariaBiodata/testing/t_out/bySAMPLE/
./correctorFase.sh /home/umaelab/SolariaBiodata/testing/t_out/bySAMPLE/ 4
./maestro_varAnot.sh /home/umaelab/SolariaBiodata/testing/t_out/bySAMPLE/ GRCh38.p13.RefSeq

```

Más detalles en  [Solaria Biodata](http://solariabiodata.com.mx).
