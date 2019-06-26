# SIV_to_HIV-1
Analysis of variants arising during passage of SIVs in humanized mice


#### Overall workflow for quantifying frequencies of particular amino acids in SIV & HIV sequences available from the [HIV Sequence Database Compendium](https://www.hiv.lanl.gov/content/sequence/HIV/COMPENDIUM/compendium.html)

1. Download multiple protein sequence alignments for each HIV/SIV protein from the [Alignments tab](https://www.hiv.lanl.gov/content/sequence/NEWALIGN/align.html).  When I retreived sequences in April 2019, the most recent alignments available were for the 2017 compendium.
2. Extract subsets of these alignments containing only HIV-1 sequences or only SIV sequences. [split_seqs](./split_seqs)
3. Create a position probability matrix: For each position of the alignment, tabulate the number of observations of each amino acid (or gap). Do this separately for HIV & SIV sequences. [create_ppm](./create_ppm)
4. For each protein of each of the 3 viruses we were studying, create a mapping of the amino acid position in each protein to the position in the multiple sequence alignment. This works because we are experimentally working with viruses whose sequences are already contained in the compendium alignments. [generate_mapping](./generate_mapping)
5. Validate this mapping. [check_all_mapping](./validate/check_all_mapping)
6. The PPM plus mapping information allows us to retreive the frequency in these sets of HIV and SIV sequences of any variant that arise during the passage experiments. This is done in the [viral_variant_explorer](https://github.com/stenglein-lab/viral_variant_explorer) Shiny app.
