---
title: "Obtener las \"chains\" separadas de un simple PDB"
date: "2017-09-25"
categories: 
  - "bioinformatics"
  - "scripts"
tags: 
  - "bioinformatics"
  - "chain"
  - "pdb"
---

El otro día peleándome con TM-align para conseguir alineaciones de distintos pdbs que parecieran razonables me di cuenta que dicho programa tiene problemas con las proteínas multi-dominio. La solución que le encontré fue en bajarme los PDBs y luego separar las chains. [Aquí os dejo el script](https://github.com/rocreguant/I-have-time/blob/master/get_chains.py).

\[code language="python"\]

import re import os

#Idea: https://www.biostars.org/p/59715/

list\_path = 'list-DLG4\_HUMAN.txt' db\_path = '/n/scratch2/rr191/databases/pdb2/'

with open(list\_path, 'r') as f\_pdb: for pdb in f\_pdb:

#Getting the info from the pdb to download structure = pdb.split(':')\[0\].lower() chain = pdb.split(':')\[1\].upper()\[0\]

#downloading the pdbs if(not os.path.isfile(db\_path+structure+'.pdb') or True): \_ = os.popen('wget -O '+db\_path+structure+'.pdb https://files.rcsb.org/download/'+structure+'.pdb > /dev/null 2>&1').read()

with open(db\_path+structure+'.pdb', 'r') as f: with open(db\_path+'chains/'+structure+'\_'+chain+'.pdb', 'w') as fo: for line in f: #selecting the atoms from the desired chain and writing them in a new file if 'ATOM' in line and ' '+chain+' ' in line: fo.write(line)

\[/code\]
