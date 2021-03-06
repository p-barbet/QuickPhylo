README
======
Authors: Pauline Barbet, Arnaud Felten

Affiliation: [Food Safety Laboratory - ANSES Maisons Alfort (France)](https://www.anses.fr/en/content/laboratory-food-safety-maisons-alfort-and-boulogne-sur-mer)

You can find the latest version of the tool at [https://github.com/afelten-Anses/QuickPhylo](https://github.com/afelten-Anses/QuickPhylo)


Workflow
========
This workflow aims to fastly build a root tree with Mash and dendropy. To make the root tree, two methods are available: UPGMA and Neighbourg-Joining (NJ).

The script takes in input assembly, reads (compressed or not) and sketch files.

The Mash sketch function, sketch each fasta and fastq files into msh files.

Then, the Mash dist function create a distance matrix based on jaccard index at tsv format with previous sketch files and files already sketch.

Finally dendropy produce in output a newick file with the root tree. 

![](workflow.JPG?raw=true "script workflow")

Dependencies
============

The script has been developed with python 2.7 (tested with 2.7.12)

## External dependencies

* [Mash](https://github.com/marbl/Mash/blob/master/INSTALL.txt) tested with 2.0
* [Dendropy](https://www.dendropy.org/) tested with 4.3.0


Parameters
==========

## Parameters

* -i : tsv file containing paths to reads, asssembly or/and sketched files, more than 2 (REQUIRED)
* -o : output tsv matrix name (default:output)
* -T : maximum number of threads to use (default:1)
* -k : k-mer size for sketching (default:15)
* -s : sketch size = number of k-mer (default:1000)
* -e : output newick tree name (default:output)

## Options

* --S : suppress sketch files (default:False)
* --UPGMA : use UPGMA algorithm (default:NJ)

Test
====

After installing Mash and dendropy you can test the script with the command lines:

	mkdir test
	cd test
	python FasTosh -T nbThreads -i input.tsv -o matrix_name -e tree_name

	