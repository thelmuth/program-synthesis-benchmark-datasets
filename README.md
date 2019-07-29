# General Program Synthesis Benchmark Suite Datasets

Version 1.0

This repository contains datasets for the 29 problems described in the paper [General Program Synthesis Benchmark Suite](http://thelmuth.github.io/GECCO_2015_Benchmarks_Materials/). These problems come from introductory programming textbooks, and require a range of programming constructs and datatypes to solve. These datasets are designed to be usable for any method of performing general program synthesis, including and not limited to inductive program synthesis and evolutionary methods such as genetic programming.

## Use

Each problem in the benchmark suite is located in a separate directory in the `datasets` directory. All data files are compressed with `gzip`. To unzip the datasets, you can unzip individual files, or run the `decompress` script to unzip them all at once.

For each problem, we provide a set of `edge` cases and a set of `random` cases. The `edge` cases are those given in the [technical report](https://web.cs.umass.edu/publication/docs/2015/UM-CS-2015-006.pdf) describing the benchmark problems. The `random` cases are all generated from the recommended data domains from the technical report, and appear in the same proportions as recommended. For each problem, we included up to 1 million `random` cases, unless the range of problem inputs is smaller than 1 million or the resulting file size was over 100MB, in which case we included as many as we could.

A typical use of these datasets for a set of runs of program synthesis would be:

- For each run, use every `edge` case in the training set
- For each run, use a different, randomly-sampled set of `random` cases in the training set.
- Use a larger set of `random` cases as an unseen test set.

We have provided typical sizes of training and test sets in each problems README.md.

## Dataset format

Each edge and random dataset is provided in three formats: CSV, JSON, and EDN, with all three formats containing identical data. Each data file has the following:

- The first row of the file is the column names.
- Each following row corresponds to one set of program inputs and expected outputs.
- Input columns are labeled `input1`, `input2`, etc., and output columns are labeled `output1`, `output2`, etc.
- In CSVs, string inputs and outputs are double quoted when necessary, but not if not necessary. Newlines within strings are escaped. JSON and EDN formats require all strings to be double quoted.
- Columns in CSV files are comma-separated. JSON and EDN formats follow standard separation.

## Citation

If you use these datasets in a publication, please cite the paper [General Program Synthesis Benchmark Suite](http://thelmuth.github.io/GECCO_2015_Benchmarks_Materials/) and include a link to this repository.

BibTeX entry for paper:

```bibtex
@InProceedings{Helmuth:2015:GECCO,
  author =	"Thomas Helmuth and Lee Spector",
  title =	"General Program Synthesis Benchmark Suite",
  booktitle =	"GECCO '15: Proceedings of the 2015 Annual Conference
		 on Genetic and Evolutionary Computation",
  year = 	"2015",
  isbn13 =	"978-1-4503-3472-3",
  pages =	"1039--1046",
  organisation = "SIGEVO",
  address =	"Madrid, Spain",
  URL =  	"http://doi.acm.org/10.1145/2739480.2754769",
  DOI =  	"10.1145/2739480.2754769",
  publisher =	"ACM",
  publisher_address = "New York, NY, USA",
}
```

## Generation Source Code

The datasets here were generated using [this function call](https://github.com/thelmuth/Clojush/blob/develop/2019-benchmark-datasets/src/clojush/problems/software/test_case_data_generators.clj#L180-L181) in Clojush, the Clojure version of PushGP. This code is admittedly messy, and should only be used if absolutely necessary.
