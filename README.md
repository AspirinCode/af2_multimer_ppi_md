# AlphaFold-Multimer_PPI_MD
Protein-Protein Complex Conformational Sampling via AlphaFold-Multimer and Molecular Dynamics


![gen by DALL.E](https://github.com/AspirinCode/af2_multimer_ppi_md/blob/main/figure/af2_multimer_ppi_md_figure.png)





## Requirements

*  biopython

https://github.com/biopython/biopython

*  Amber

https://ambermd.org

*  MDAnalysis

https://www.mdanalysis.org/

*  nglview

https://github.com/nglviewer/nglview

*  pytraj

https://github.com/Amber-MD/pytraj

*  mdtraj

https://github.com/mdtraj/mdtraj


## Molecular dynamics

### prpepare  topology and coordinate files
```python
pdb4amber -i A.pdb -o a.pdb -y -d

pdb4amber -i a.pdb -o inputA.pdb --reduce

pdb4amber -i B.pdb -o b.pdb -y -d

pdb4amber -i b.pdb -o inputB.pdb --reduce


************tleap.in**********************************************
source leaprc.protein.ff14SB #Source leaprc file for ff14SB protein force field
source leaprc.water.tip3p #Source leaprc file for TIP3P water model

ProA = loadpdb inputA.pdb #Load A PDB file for protein
ProB = loadpdb inputB.pdb #Load B PDB file for protein

mol = combine {ProA,ProB}

check mol
solvatebox mol TIP3PBOX 12.0 #Solvate the complex with a cubic water box
addions mol Cl- 0 #Add Cl- ions to neutralize the system
addions mol Na+ 0 #Add Na+ ions to neutralize the system
charge mol
savepdb mol ppcomplex_solv.pdb
saveamberparm mol ppcomplex_solv.prmtop ppcomplex_solv.inpcrd #Save AMBER topology and coordinate files
quit #Quit tleap program
**********************************************************************

tleap -s -f tleap.in > tleap.out

```

### Run molecular dynamics

```



```


## Model Metrics

### DockQ
DockQ: A Quality Measure for Protein-Protein Docking Models

https://github.com/bjornwallner/DockQ

*  Basu, S. and Wallner, B., 2016. DockQ: a quality measure for protein-protein docking models. PloS one, 11(8), p.e0161879.
*  Mirabello, C. and Wallner, B., 2024. DockQ v2: Improved automatic quality measure for protein multimers, nucleic acids, and small molecules. bioRxiv, pp.2024-05.  

## License
Code is released under GNU GENERAL PUBLIC LICENSE.


## Cite:
*  Jianmin Wang, Xun Wang, Yanyi Chu, Chunyan Li, Xue Li, Xiangyu Meng, Yitian Fang, Kyoung Tai No, Jiashun Mao, Xiangxiang Zeng. **"Exploring the conformational ensembles of protein-protein complex with transformer-based generative model."** Journal of Chemical Theory and Computation; doi: https://doi.org/10.1021/acs.jctc.4c00255



## Note




https://ambermd.org

https://github.com/sokrypton/ColabFold

https://github.com/steineggerlab/colabfold-protocol




