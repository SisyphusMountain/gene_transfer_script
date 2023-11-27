# Introduction
This is a Rust program designed to quickly generate many gene trees from a given species tree.




# Installation
Building a project written in Rust is very easy.
1. Install the [Cargo package manager](https://doc.rust-lang.org/cargo/getting-started/installation.html).
2. Clone the repository.
3. Navigate inside the directory in the terminal.
4. Run the command ```cargo build --release```. This will automatically download all necessary dependencies and compile the binary inside a new target directory.

# Algorithm
This Rust script chooses a transfer uniformly along the branches of the trees, according to the model of gene transfers given by [ref].


# Usage
Input:
1. A .nwk file containing a newick tree with node lengths and optional internal node names like so:
```((a:1.0,b:1.0)c:1.0,d:2.0)e:0.0;```
The grammar for the parser, which you can easily modify to suit other formats of  is defined in the ```newick.pest``` file. The parser is [pest](https://pest.rs/book/grammars/syntax.html)
2. The output directory ```out_dir```.
3. The text file ```transfers_file``` containing the specified number of transfers to simulate for each gene tree, separated by commas and no blank spaces like ```1,2,3,5```.

```Usage: ./gene_transfer_script <path_to_nwk_file> <output_directory> <path_to_transfers_file>```

Output:
A new folder ```out_dir/tree_0``` will be created, as well as ```out_dir/tree_0/genes``` and ```out_dir/tree_0/transfers```, containing respectively the gene trees generated in newick format, and .csv files indicating the donor and receivers of simulated transfers, as well as the time of the transfers (starting from the root of the species tree). A gene tree ```out_dir/tree_0/genes/gene_{i}.nwk``` is created for each value in ```transfers_file```, along with the csv file ```out_dir/tree_0/transfers/transfers_{i}.csv```.
