# Capacitación 

## Sesión 1

A continuación se presenta una guía rápida para usar los comandos vistos en la capacitación

```markdown
## Acomodo de los archivos 

for i in $(ls **/home/labseq/SolariaBiodata/testing/reads202012/**); do ln -s **/home/labseq/SolariaBiodata/testing/reads202012/**$i $i; done
for i in $(ls | cut -d "_" -f-2 | uniq); do mkdir $i; mv ${i}*gz $i; done

## Preprocesamiento de las lecturas

./filtradorLecturas_mismaMuestra.sh **/home/umaelab/SolariaBiodata/testing/input/** **/home/umaelab/SolariaBiodata/testing/t_out/** 12 30 50
```

## Sesión 2

```markdown
## Ensamble guiado por referencia

./ensamblador.sh **/home/umaelab/SolariaBiodata/testing/t_out/** 16 HY2TMBGXF 20200216 NS500707
./combinaEnsamble_porMuestra.sh **/home/umaelab/SolariaBiodata/testing/t_out/**

## Procesamiento del alineamiento

./realineadorLecturas_shotgun.sh **/home/umaelab/SolariaBiodata/testing/t_out/bySAMPLE/** 16 **/home/umaelab/SolariaBiodata/produccion/hglft_genome_6ffb1_e12b90.bed**
./recalibradorCalidadBases.sh **/home/umaelab/SolariaBiodata/testing/t_out/bySAMPLE/** 16

```

Más detalles en  [Solaria Biodata](http://solariabiodata.com.mx).
