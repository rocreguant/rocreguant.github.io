---
title: "Script en python para convertir secuencias de proteínas de Stockholm a fasta"
date: "2017-05-15"
categories: 
  - "scripts"
tags: 
  - "fasta"
  - "python"
  - "secuencias-de-proteinas"
  - "stockholm"
---

[Aquí os dejo un pequeño python script](https://github.com/rocreguant/I-have-time/blob/master/sto-to-fasta.py) que convierte "multiple sequence alignments" del formato Stockholm a Fasta de una forma sencilla y rápida.

\[code language="python"\] import sys from Bio import SeqIO from Bio.Seq import Seq from Bio.SeqRecord import SeqRecord

if(len(sys.argv) &lt;3): print('two arguments needed: input path, output path') exit(2)

with open(sys.argv\[1\],'r') as inFile: with open(sys.argv\[2\], "w") as output\_handle: SeqIO.write(list(SeqIO.parse(inFile,'stockholm')), output\_handle, "fasta")

\[/code\]
