# DCA

<a herf=http://biophy.hust.edu.cn/new/DCA>Click here to visit DCA web server</a>

Direct Coupling Analysis (DCA) is a statistical inference framework used to infer direct co-evolutionary couplings among residue pairs in multiple sequence alignments, which aims at disentangling direct from indirect correlations.

Users only need to provide the necessary input and submitted on it.

- Input
    The input of this web server can be a single-line-sequence, a fasta formatted single sequence, and Multiple Sequence Alignment(MSA) or raw DCA results.

    - Single-line-sequence
        The single sequence is in one line, without any addtional spaces and new line characters.
            
        ```
        CGCUUCAUAUAAUCCUAAUGAUAUGGUUUGGGAGUUUCUACCAAGAGCCUUAAACUCUUGAUUAUGAAGUG
        ```

    - Single sequence in fasta format
        The single sequence can have a label, which is prepended before the sequence.
        ```
        >sample sequence
        CGCUUCAUAUAAUCCUAAUGAUAUGGUUUGGGAGUUUCUACCAAGAGCCUUAAACUCUUGAUUAUGAAGUG
        ```
        
    - MSA
        A fasta formatted MSA file can also be the input. It's like this:
            
        ```
        >CP000851.1/4146892-4146991
        -UAAUAUUUACCGUUAACACUUCGUAUAAUCUCAAUGAUAUGGU-UUGAGAGUUUCUACC
        AAG-AGCCC--UAAACU-CUUGAUUAU--GAAGACUUUACUUUAUGUA-
        >AANE01000012.1/71437-71536
        -AAUUUAGCCGCGAAAUUGCUUCGUAUAAUCCCAAUGAUAUGGU-UUGGGAGUUUCUACC
        AAG-AACCU--UAAAUU-CUUGAUUAU--GAAGUCUGUAACUUUAUGG-
        >ABCQ01000013.1/101307-101406
        -AACUACGUCAUUAAAUCACUUCGUAUAAUCCCAAUAAUAUGGU-UUGGGAGUUUCUACC
        AAG-AUCCU--UAAACU-CUUGAUUAU--GAAGUCUGUAACUUUAAAA-
        >MSA-TARGET
        -----------------CGCUUCAUAUAAUCCUAAUGAUAUGGU-UUCCGAGUUUCUACC
        AAG-AGCCU--UAAACU-CUUGAUUAU--GAAGUG--------------
        >CP000961.1/1440820-1440919
        -GCCUCCACAAAACUUAAGCUUCGUAUAAUCCCAAUGAUAUGGU-UUGGGAGUUUCUACC
        AAG-AGCCU--UAAAUU-CUUGAUUAU--GAAGUCUGUAGCUUUAUAU-
        >CR378679.1/147737-147638
        -UAAUAAUGGGUAAAGUUACUUCGUAUAACCCCACUUAUAGGGU-GUGGGGGUCUCUACC
        AGA-AUCCG--UAAAAU-UCUGAUUAC--GAAGAGUUGAGUGAUUGAU-
        >AAPS01000004.1/87369-87468
        -UAUAAUCCCUCUCGUUUGCUUCGUAUAACCCCAAUGAUAUGGU-UUGGGGGUCUCUACC
        AGU-UCCCG--CAAAGU-GCUGAUUAC--GAAGAGUUGAGAUCAUCGU-
        >AAWP01000021.1/27378-27279
        -GUAUAAUCGCGCCGUUUGCUUCGUAUAACCCCAAUGAUAUGGU-UUGGGGGUCUCUACC
        -AGCUCCCG--CAAAGUGCU-GAUUAC--GAAGAGUUGAGAUCACUGU-
        ```    
        
    - Raw DCA results
        Our web server can remove some of the false positive values in DCA values, the raw DCA values is like this:
        ```
        1 2 0.0222606
        1 3 0.0244218
        1 4 0.00404876
        1 5 0.0106655
        1 6 0.00497574
        1 7 0.00536148
        1 8 0.00113751
        1 9 0.000536608
        1 10 0.00113748
        1 11 0.00113745
        ```
                
- Output
    The DCA web server will do computations according to your inputs, the main routines are as below.
    ```
    Seq -> Rfam -> MSA -> DI -> DI*
    ```
    In the above procedures, we use RNA falimiy(Rfam) to get a seed for each single sequence(Seq), and then a MSA method(infernal, MUSCLE or HMMER) is utilized to get the aligned fasta file. Then, we get the raw DI values by plmDCA or mfDCA. Finnaly, a simple routine is used to remove the obvious false positive values of DI values and the clean DI values are obtained(DI*).

    After the task is finished, the MSA(if the input is single sequence), DCA(if the input is sequence or MSA), and clean DI values will be provided to you.