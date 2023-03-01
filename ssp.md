# Secondary Structure Prediction

- Free energy minimization method
    ```
    nsp ssp_fe -seq <SEQUENCE>
    ```

- Combining free energy minimization method and DI value of the DCA prediction for secondary structure prediction
    ```
    nsp ssp_dca -seq <SEQUENCE> -di <DI_FILE> [-k <K>]
    ```

    *`<K>` value is used to set to read the first `K·L` DI values. If `K=1`, on behalf of the read before `L`; if `K=0.5`, on behalf of the read before `L/2`.*

- Show secondary structure tree
    ```
    nsp ss_tree -seq <SEQUENCE> -ss "<SS>"
    ```

    *`<SEQUENCE>` is the sequence, `<SS>` is the secondary structure.*

    Example:
    ```
    nsp ss_tree -seq AAAACCCCUUUU -ss "((((....))))"
    ```

- Calculate MCC
    ```
    nsp mcc "<SECONDARY_STRUCTURE_OF_NATIVE>" "<SECONDARY_STRUCTURE_OF_PREDICTION>"
    ```

- Calculate STY
    ```
    nsp sty "<SECONDARY_STRUCTURE_OF_NATIVE>" "<SECONDARY_STRUCTURE_OF_PREDICTION>"
    ```

- Calculate PPV
    ```
    nsp ppv "<SECONDARY_STRUCTURE_OF_NATIVE>" "<SECONDARY_STRUCTURE_OF_PREDICTION>"
    ```