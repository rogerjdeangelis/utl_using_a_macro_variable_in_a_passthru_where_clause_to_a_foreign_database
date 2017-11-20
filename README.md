# utl_using_a_macro_variable_in_a_passthru_where_clause_to_a_foreign_database
Using a macro variable in a passthru where clause to a foreign database

    ```  Using a macro variable in a passthru where clause to a foreign database                                                                                      ```
    ```                                                                                                                                                               ```
    ```                                                                                                                                                               ```
    ```  INPUTS                                                                                                                                                       ```
    ```  ======                                                                                                                                                       ```
    ```                                                                                                                                                               ```
    ```     %let sexAge= %str(sex='M' and age=15);                                                                                                                    ```
    ```                                                                                                                                                               ```
    ```                                                                                                                                                               ```
    ```     Input workbook d:/xls/class.xlsx with sheet class (you can use [sheet1])                                                                                  ```
    ```                                                                                                                                                               ```
    ```       d:/xls/class.xlsx                                                                                                                                       ```
    ```                                                                                                                                                               ```
    ```        +----------------------------------------------------------------+                                                                                     ```
    ```        |     A      |    B       |     C      |    D       |    E       |                                                                                     ```
    ```        +----------------------------------------------------------------+                                                                                     ```
    ```     1  | NAME       |   SEX      |    AGE     |  HEIGHT    |  WEIGHT    |                                                                                     ```
    ```        +------------+------------+------------+------------+------------+                                                                                     ```
    ```     2  | ALFRED     |    M       |    14      |    69      |  112.5     |                                                                                     ```
    ```        +------------+------------+------------+------------+------------+                                                                                     ```
    ```     3  | BARBARA    |    F       |    13      |    58      |  101.5     |                                                                                     ```
    ```        +------------+------------+------------+------------+------------+                                                                                     ```
    ```         ...                                                                                                                                                   ```
    ```        +------------+------------+------------+------------+------------+                                                                                     ```
    ```     20 | WILLIAM    |    M       |    15      |   66.5     |  112       |                                                                                     ```
    ```        +------------+------------+------------+------------+------------+                                                                                     ```
    ```     [CLASS]                                                                                                                                                   ```
    ```                                                                                                                                                               ```
    ```  PROCESS ( all of it)                                                                                                                                         ```
    ```  ====================                                                                                                                                         ```
    ```                                                                                                                                                               ```
    ```    proc sql dquote=ansi;                                                                                                                                      ```
    ```     connect to excel (Path='d:/xls/class.xlsx' );                                                                                                             ```
    ```       create                                                                                                                                                  ```
    ```           table want as                                                                                                                                       ```
    ```       select                                                                                                                                                  ```
    ```           *                                                                                                                                                   ```
    ```           from                                                                                                                                                ```
    ```             connection to Excel                                                                                                                               ```
    ```           (                                                                                                                                                   ```
    ```            Select                                                                                                                                             ```
    ```                *                                                                                                                                              ```
    ```            from                                                                                                                                               ```
    ```               class                                                                                                                                           ```
    ```            where                                                                                                                                              ```
    ```               &sexAge                                                                                                                                         ```
    ```           );                                                                                                                                                  ```
    ```      disconnect from Excel                                                                                                                                    ```
    ```     ;Quit;                                                                                                                                                    ```
    ```                                                                                                                                                               ```
    ```                                                                                                                                                               ```
    ```  OUTPUT                                                                                                                                                       ```
    ```  ======                                                                                                                                                       ```
    ```                                                                                                                                                               ```
    ```   Up to 40 obs from want total obs=2                                                                                                                          ```
    ```                                                                                                                                                               ```
    ```   Obs     NAME      SEX    AGE    HEIGHT    WEIGHT                                                                                                            ```
    ```                                                                                                                                                               ```
    ```    1     Ronald      M      15     67.0       133                                                                                                             ```
    ```    2     William     M      15     66.5       112                                                                                                             ```
    ```                                                                                                                                                               ```
    ```  *                _              _       _                                                                                                                    ```
    ```   _ __ ___   __ _| | _____    __| | __ _| |_ __ _                                                                                                             ```
    ```  | '_ ` _ \ / _` | |/ / _ \  / _` |/ _` | __/ _` |                                                                                                            ```
    ```  | | | | | | (_| |   <  __/ | (_| | (_| | || (_| |                                                                                                            ```
    ```  |_| |_| |_|\__,_|_|\_\___|  \__,_|\__,_|\__\__,_|                                                                                                            ```
    ```                                                                                                                                                               ```
    ```  ;                                                                                                                                                            ```
    ```                                                                                                                                                               ```
    ```  libname xel "d:/xls/class.xlsx";                                                                                                                             ```
    ```  data xel.class;                                                                                                                                              ```
    ```    set sashelp.class;                                                                                                                                         ```
    ```  run;quit;                                                                                                                                                    ```
    ```  libname xel clear;                                                                                                                                           ```
    ```                                                                                                                                                               ```
    ```  *          _       _   _                                                                                                                                     ```
    ```   ___  ___ | |_   _| |_(_) ___  _ __                                                                                                                          ```
    ```  / __|/ _ \| | | | | __| |/ _ \| '_ \                                                                                                                         ```
    ```  \__ \ (_) | | |_| | |_| | (_) | | | |                                                                                                                        ```
    ```  |___/\___/|_|\__,_|\__|_|\___/|_| |_|                                                                                                                        ```
    ```                                                                                                                                                               ```
    ```  ;                                                                                                                                                            ```
    ```                                                                                                                                                               ```
    ```    proc sql dquote=ansi;                                                                                                                                      ```
    ```     connect to excel (Path='d:/xls/class.xlsx' );                                                                                                             ```
    ```       create                                                                                                                                                  ```
    ```           table want as                                                                                                                                       ```
    ```       select                                                                                                                                                  ```
    ```           *                                                                                                                                                   ```
    ```           from                                                                                                                                                ```
    ```             connection to Excel                                                                                                                               ```
    ```           (                                                                                                                                                   ```
    ```            Select                                                                                                                                             ```
    ```                *                                                                                                                                              ```
    ```            from                                                                                                                                               ```
    ```               class                                                                                                                                           ```
    ```            where                                                                                                                                              ```
    ```               &sexAge                                                                                                                                         ```
    ```           );                                                                                                                                                  ```
    ```      disconnect from Excel                                                                                                                                    ```
    ```     ;Quit;                                                                                                                                                    ```

