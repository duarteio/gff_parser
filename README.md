# gff_parser
Python parser to add external gene calls and functional annotation from Prokka, IMG
or Bakta to Anvi'o.  
Uses Python3, Biopython and gffutils package (https://github.com/daler/gffutils).  
Install `gffutils` using conda: `conda install -c bioconda gffutils`

Annotate your genome/metagenome with Prokka/Bakta or download annotations from the IMG
database.
Use the script to get two files needed for external gene calls and annotations for Anvi'o.   
With the `--source` flag you can specify where the annotations are coming from.
Amino acid sequences can also be added to the gene calls file using the flags `--include-aa-sequences` and `--faa_file`.
This functionality has, however, only been tested with Bakta annotation files.

Basic usage:
```
gff_parser.py GFF3_file --gene-calls gene_calls.txt --annotation gene_annot.txt --source Prokka
```

This might or might not work for your files. But I hope it works for you too.

But at least you can try it out with the test files provided in the `test` folder (Thanks to [Andrew Morris](https://github.com/amorris28) for the test files for Prokka and IMC).

__PROKKA__ annotations:
```
python gff_parser.py test/PROKKA.gff --gene-calls Prokka_gene_calls.txt --annotation Prokka_annotation.txt --process-all --source Prokka
```
__IMG__ annotations:
```
python gff_parser.py test/IMG.gff --gene-calls IMG_gene_calls.txt --annotation IMG_annotation.txt --process-all --source IMG
```
__BAKTA__ annotations:
```
python gff_parser.py test/BAKTA.gff --gene-calls BAKTA_gene_calls.txt --annotation BAKTA_annotation.txt --process-all --source Bakta
```

Additionally, these flags can be used to include amino acid sequences in the gene calls:
```
python gff_parser.py test/BAKTA.gff --gene-calls BAKTA_gene_calls.txt --annotation BAKTA_annotation.txt --process-all --source Bakta --include-aa-sequences --faa_file test/BAKTA.faa
```
