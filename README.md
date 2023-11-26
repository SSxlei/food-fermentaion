# food-fermentaion
1.Upstream and downstream sequence extraction of BGC

```
#Extracting the basic information of each BGC from the output file of the BGC
python touch_new.py #Extracting the information of BGC into an excel table
python excel.py #Remove thousand-bit separators from the start and stop sequences of BGC in the excel table
python excel-1.py #The start and stop sequences of BGC in the excel table were subtracted by 1
python excel2BED.py #The excel file was converted into BED file containing the contig, start position and end position of BGC
samtools faidx M1.fa > M1.fai
cut -f 1,2 M1.fai > genome.len #Preparing the length of each contig in the MAG
bedtools flank -i M1.bed -g genome.len -l 5000 -r 0 -s > up.bed
bedtools flank -i M1.bed -g genome.len -l 0 -r 5000 -s > down.bed
bedtools getfasta -s -fi M1.fa -bed up.bed -fo M1up.fa -name 
bedtools getfasta -s -fi M1.fa -bed down.bed -fo M1down.fa -name 
```
