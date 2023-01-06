# PARB-Phage-interactions

Files explanation:

The folder 'MAGs' contained all the MAGs

MAGs.list was the name of the MAGs

MAG.quality included assessment for the selected MAGs

MAG.taxonomy included labels for the MAGs

pahge_contig_test.fa was the phage prediction results from the PhaMer. 

Phamer:

```bash
python PhaMer_preprocessing.py --contigs /data/guest/software/PathoFact/jinghu.fna --midfolder jinghu_phamer --threads 48
python PhaMer.py --midfolder jinghu_phamer --threads 48 --out phage_prediction.csv
# organized the result
cat jinghu_phage_prediction.csv | awk -F ',' '$2=="phage"&&$3>0.7' | cut -d ',' -f1 | while read line; do grep -w -A 1 "${line}" jinghu.fa ; done > phage_prediction.fa
```

