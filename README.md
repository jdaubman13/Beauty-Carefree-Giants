# Beauty-Carefree-Giants
## Step 3 
### Which commands caused errors, and why?

CREATE OR REPLACE VIEW WORD_REL (word, syn_col, ant_col) AS <br>
SELECT s.word_term, s.syn_word, a.ant_word <br>
FROM WORD_SYNONYMS s, WORD_ANTONYMS a <br>
WHERE a.word_id = s.word_id <br>
WITH READ ONLY; <br>
Resulted in an error saying <br> <br>
Error at line 2/5: ORA-42399: cannot perform a DML operation on a read-only view 1. UPDATE WORD_REL 2. SET SYN_COL = 'blithe' 3. WHERE WORD = 'insouciant'; <br> <br>
Because I was trying to update a view that was set to read only. 

### Why are DML operations restricted in some views?
DML operations are resturcted in some views because they violate constraints, are set to read only, or when a join or group function is included. This is because the database can't apply changes to the base tables.

### How is a materialized view different from a regular view?
A materialized view physically stores query results which leads to faster performance but must be refreshed often. A regular view is virtual and it shows live data from base tables each time it’s queried.
