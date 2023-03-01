# Tertiary Structure Prediction

1.	Use the “assemble” module of nsp to carry out assembly. The user needs to input the command below on the command line:
    - For linear RNA:
        ```

        YOUR_PATH_TO_NSP/RNA/nsp assemble -name <JOB_NAME> -seq <SEQUENCE> -ss "<SECONDARY_STRUCTURE>" -n <NUMBER_OF_PREDICTIONS>
        ```

    - For Circular RNA:
        ```

        YOUR_PATH_TO_NSP/cirRNA_and_DNA/nsp assemble -name <JOB_NAME> -seq <SEQUENCE> -ss "<SECONDARY_STRUCTURE>" -n <NUMBER_OF_PREDICTIONS> -circ 1
        ```
    - For DNA:
        ```

        YOUR_PATH_TO_NSP/cirRNA_and_DNA/nsp assemble -name <JOB_NAME> -seq <SEQUENCE> -ss "<SECONDARY_STRUCTURE>" -n <NUMBER_OF_PREDICTIONS> -circ 0 -t DNA
        ```
    
    *This will generate a set of structure files named `<JOB_NAME>.pred<N>.pdb`, where `<N>` represents the value from 1 to `<NUMBER_OF_PREDICTIONS>`. `<SEQUENCE>` is the sequence of RNA or DNA. `<SECONDARY_STRUCTURE>` is the dot-bracket notation of the 2D structure, and must be in quotes.*

2.	Use the “sample” module of NSP to carry on sampling. The user needs to input the command below on the command line:
    - For linear RNA:
        ```

        YOUR_PATH_TO_NSP/RNA/nsp sample -name <JOB_NAME> -seq <SEQUENCE> -ss "<SECONDARY_STRUCTURE>" -n <NUMBER_OF_PREDICTIONS> -num_samplings <NUMBER_OF_SAMPLING>
        ```

    - For Circular RNA:
        ```

        YOUR_PATH_TO_NSP/cirRNA_and_DNA/nsp sample -name <JOB_NAME> -seq <SEQUENCE> -ss "<SECONDARY_STRUCTURE>" -n <NUMBER_OF_PREDICTIONS> -num_samplings <NUMBER_OF_SAMPLING> -circ 1
        ```

    *This will sample `<NUMBER_OF_SAMPLING>` structural models and cluster them into `<NUMBER_OF_PREDICTIONS>` clusters. Then it will generate a structure file for each cluster named `<JOB_NAME>.pred<N>.pdb`, where `<N>` represents the value from 1 to `<NUMBER_OF_PREDICTIONS>`.*

3.	Use the “opt” module of NSP to carry out optimization. The user needs to input the command below on the command line:
    - For linear RNA:
        ```

        YOUR_PATH_TO_NSP/RNA/nsp opt -name <JOB_NAME> -seq <SEQUENCE> -ss "<SECONDARY_STRUCTURE>" -init <INITIAL_PDB_FILE>  [-dca <DCA_FILE>] / [-seed <SEED>] / [-<constraints|c> <CONSTRAINTS_FILE>] / [-queue <QUEUE>]
        ```

    - For Circular RNA:
        ```

        YOUR_PATH_TO_NSP/cirRNA_and_DNA/nsp opt -name <JOB_NAME> -seq <SEQUENCE> -ss "<SECONDARY_STRUCTURE>" -init <INITIAL_PDB_FILE>  [-dca <DCA_FILE>] / [-seed <SEED>] / [-<constraints|c> <CONSTRAINTS_FILE>] / [-queue <QUEUE>] -circ 1
        ```

    - For DNA:
        ```

        YOUR_PATH_TO_NSP/cirRNA_and_DNA/nsp opt -name <JOB_NAME> -seq <SEQUENCE> -ss "<SECONDARY_STRUCTURE>" -init <INITIAL_PDB_FILE>  [-dca <DCA_FILE>] / [-seed <SEED>] / [-<constraints|c> <CONSTRAINTS_FILE>] / [-queue <QUEUE>] -circ 0 -t DNA
        ```

    *The optimization is based on the simulated annealing Monte Carlo algorithm. For speed, we use the coarse-grained model that represents a residue by six pseudo atoms: P (representing the phosphate group), C1’, C4’ (representing the sugar ring), C2, C4, and C6 (representing the base). This will generate a structure file named `<JOB_NAME>.traj.p1.pdb`.*

    <table border="2" >
        <tr>
            <td width="25%" align=left>JOB_NAME</td>
            <td align=left>job name</td>
        </tr>
        <tr>
            <td width="25%" align=left>SEQUENCE</td>
            <td align=left>
                sequence<br>
                example: AAAAACCCCUUUUU<br>
            </td>
        </tr>
        <tr>
            <td width="25%" align=left>SECONDARY_STRUCTURE</td>
            <td align=left>
                secondary structure with dot-bracket notation<br>
                example: (((((....)))))<br>
            </td>
        </tr>
        <tr>
            <td width="25%" align=left>INITIAL_PDB_FILE</td>
            <td align=left>initial structure file with 'pdb' or 'cif' format</td>
        </tr>
        <tr>
            <td width="25%" align=left>CONSTRAINTS_FILE</td>
            <td align=left>
                constraints file<br>
                example:<br>
                8 23 10<br>
                9 22 10<br>
                10 21 10<br>
                The first two column represents the base sequence number, for example 8 represents the eighth base, 23 represents the twenty-third base, the last column is the minimum distance between the base.<br>
            </td>
        </tr>
        <tr>
            <td width="25%" align=left>DCA_FILE</td>
            <td align=left>dca file</td>
        </tr>
        <tr>
            <td width="25%" align=left>CONSTRAINTS_FILE</td>
            <td align=left>
                Queue of optimization actions.<br>
                Optimization action example:<br>
                <table border="2">
                    <tr>
                        <td width="70%" align=left>Simulated Annealing Monte Carlo simulation</td>
                        <td align=left>samc:200000:20-0.01</td>
                    </tr> 
                    <tr>
                        <td width="70%" align=left>Monte Carlo simulation by always heating</td>
                        <td align=left>
                            heat:100000:20<br>
                            heat:100000<br>
                        </td>
                    </tr> 
                    <tr>
                        <td width="70%" align=left>Monte Carlo simulation by always cooling</td>
                        <td align=left>
                            cool:100000:20<br>
                            cool:100000<br>
                        </td>
                    </tr> 
                    <tr>
                        <td width="70%" align=left>Monte Carlo simulation by always warming</td>
                        <td align=left>
                            warm:100000:20<br>
                            warm:100000<br>
                        </td>
                    </tr> 
                </table>
                Queue example: heat:30000+warm:100000+cool:1000000<br>
            </td>
        </tr>
        <tr>
            <td width="25%" align=left>SEED</td>
            <td align=left>default value of seed is 11</td>
        </tr>
    </table>
			
4.	Use the “traj cluster” module of NSP to cluster trajector. The user needs to input the command below on the command line:
    ```

    YOUR_PATH_TO_NSP/RNA/nsp traj cluster <JOB_NAME>.traj.p1.pdb -prefix <JOB_NAME>.cluster -k <NUMBER_OF_CLUSTERS> -aa -o clusters.out -bin <BIN_SIZE>
    ```

    *This will generate a set of structure files after cluster named `<JOB_NAME>.cluster.<N>.center.pdb` and `<JOB_NAME>.cluster.<N>.lowest.pdb`, where `<N>` represents the value from 1 to `<NUMBER_OF_CLUSTERS>`. `<JOB_NAME>`.traj.p1.pdb is the result of “opt” module. `<BIN_SIZE>` is the size of the step when reading the model of `<JOB_NAME>.traj.p1.pdb`. the default value of `<BIN_SIZE>` is 1.*

5.	Add a step “Default” to estimate whether the predicted nucleic acid molecule  structure need optimize. Firstly use “assemble” module of NSP, besides the structure file, it will also generate a log file named `<JOB_NAME>.p1.log`. Then the user needs to input the command below on the command line:

    - For linear RNA:
        ```

        python YOUR_PATH_TO_NSP/RNA/perfect_temp.py -i <JOB_NAME>.p1.log -p “YOUR_PATH_TO_NSP/Lib/”
        ```

    - For Circular RNA and DNA:
        ```

        python YOUR_PATH_TO_NSP/cirRNA_and_DNA/perfect_temp.py -i <JOB_NAME>.p1.log -p “YOUR_PATH_TO_NSP/Lib/”
        ```

    *If the answer is “True”, it means the predicted structure is already prefect. Otherwise, the user needs to use “opt” module of NSP to optimize the predicted structure.*

6.	Score a single structure by the “score” module of NSP. The user needs to input the command below on the command line:
    ```
    YOUR_PATH_TO_NSP/RNA/nsp score -s <PDB_FILE>
    ```
                
    *This module can only score RNA, it cannot be used for DNA.*

7.	Score multiple structures using the “score” module of NSP. The user needs to input the below command in the command line:
    ```
    YOUR_PATH_TO_NSP/RNA/nsp score -s:l <LIST_FILE>
    ```

    *The file in the list of <LIST_FILE> contains the name of the structure to cluster.*
