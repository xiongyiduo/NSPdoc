# Utilities

- Clustering
    ```
    nsp cluster -list <LIST_FILE> -k <NUMBER_OF_CLUSTERS>
    ```
    *Set the structures that need to cluster with `-list` and set the amount with `-k`.*
    *After a period of operation, the structure of the cluster will be printed out on the screen.*
    *The `<LIST_FILE>` file contains the name of the structure to cluster.*

- Calculating RMSD
    ```
    nsp rmsd <PDB_FILE_1> <PDB_FILE_2>
    ```

- Get the sequence of the molecule
    ```
    nsp seq <PDB_FILE>
    ```

- Get the secondary structure of the molecule
    ```
    nsp ss <PDB_FILE>
    ```

- Get the number of residues in the molecule
    ```
    nsp len <PDB_FILE>
    ```

- Get of specified residues in the molecul
    ```
    nsp sub <PDB_FILE> -num <FRAG1> <FRAG2> <FRAG3> <FRAG4> ...
    ```

    *Each frag refers to a base segment, the format is a single residue number n or the specified starting point and end point of the fragment begin-end. for example, 1 represents the first residue, and 4-11 represents a fragment of fourth to eleventh bases.*

- Only residues A, U, G and C are retained
    ```
    nsp rna <PDB_FILE>
    ```

- Only residues A, U, G and C containing the complete atoms are retained
    ```
    nsp rna <PDB_FILE> -format
    ```