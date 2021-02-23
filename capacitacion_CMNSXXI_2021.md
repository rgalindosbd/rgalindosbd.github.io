## Capacitación módulos variantes

A continucación se encuentran líneas de código útiles


```Lo que sea
for i in $(ls /home/labseq/SolariaBiodata/testing/reads202012/); do ln -s /home/labseq/SolariaBiodata/testing/reads202012/$i $i; done

for i in $(ls | cut -d "_" -f-2 | uniq); do mkdir $i; mv ${i}*gz $i; done

```
