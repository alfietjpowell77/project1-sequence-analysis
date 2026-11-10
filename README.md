# project1-sequence-analysis
Mutation detection in NGS reads using Python

This project is to analyse next-generations sequencing (NGS) from fission yeast (S.pombe) using a known 200-nucleotide reference sequence to identify differences and mismatches in nucleotides. The purpose of the project is to see how untreated controls compare to samples treated with a genotoxic agent.

To open and run the project in Colab, click the .ipynb file in GitHub, run the set up cells to import the data files and click run all. Summary of results will print below Final Analysis.

The program expects 2 files for input, a reference sequence file (reference.txt) which contains a 200-nucleotide DNA sequence along with a sequencing reads file (reads.csv) which contains 6000 sequencing reads. It returns validated reads combined with details on mutations along with a summary table on mismatch percentages and in the final analysis section it shows top positions for mutations alongside their p-values.

In Step 4, I used a helper function (get_top_positions) containing a nested "sort_helper" which returns "(-frequency, pos_num)" to sort positions. So instead of writing a long, complicated "for" loop to handle ties, the negative frequency allowed pythons "sorted()", to rank the highest counts first and when counts were tied, it would automatically pick the lower position number.

In validate_read, I looped through "upper_seq" and used "break" so that when the first invalid character was found it saved time by not having to go through the entire 200-letter read and stops "invalid_characrters" from being added to "errors[]" over and over again.

I used "assert" tests across each step to check my codes robustness, they checked edge, normal and invalid inputs. In validate_read, I used "("ATN", reference)" to confirm a read failing both valid characters and valid length, then for find_mutations I used an extreme test (find_mutations("GCTA", "ATCG")) where all 4 bases in the read were mutated. I also tested empty lists "[]" in analyse_reads to check it still ran clearly and didn't crash.
