## SQL and Relational Databases

In this checkpoint you will be exploring a Pokemon dataset that has been put into SQL tables. Pokemon are fictional creatures from the [Nintendo franchise](https://en.wikipedia.org/wiki/Pok%C3%A9mon) of the same name.

Some Pokemon facts that might be useful:
* The word "pokemon" is both singular and plural. You may refer to "one pokemon" or "many pokemon".
* Pokemon have attributes such as a name, weight, and height.
* Pokemon have one or multiple "types". A type is something like "electric", "water", "ghost", or "normal" that indicates the abilities that pokemon may possess.
* The humans who collect pokemon are called "trainers".

The schema of `pokemon.db` is as follows:

<img src="data/pokemon_db.png" alt="db schema" style="width:500px;"/>

### How to fill out answers in this checkpoint

Assign your SQL queries as strings to the variables `q1`, `q2`, etc. 

We provide starter code to copy and paste in your answer cell.  
For example, for question 2, the starter code looks like this:
```
q2 = '' 
pd.read_sql(q2, cnx)
```

- for each question, save your sql query as a string assigned to a variable named `q`+`the numeral of the question` 
   - for example, for question 2: ```q2 = 'your sql query as a string here' ```
   - if your query runs multiple lines, use the world-famous "triple ticks", as below:
       ``` 
       q2 = 
       '''
       a query
       that runs
       multiple lines
       '''
       ```
       
   
   
- we also provide starter code to call that sql query string and convert the data into a pandas dataframe so you can check your work
   - for example, also for quesiton 2: `pd.read_sql(q2, cnx)`
   - you **do not alter** this part; run as-is to check your work!
   
   
**What you need to do:**
- Copy/paste both lines of the starter code into your answer cell
- Figure out your sql query, write it as a string, and assign it to the `q` variable in the starter code
- Run the `pd.read_sql` starter code at the bottom of your answer cell without altering it in order to check your work


**Important note on syntax**: 
- use `double quotes ""` when quoting strings **within** your query 
- wrap the entire query in `single quotes ''` (if the query is on one line) or `triple ticks ''' '''` (if the query is on multiple lines).


```python
# Run this cell without changes
import pandas as pd
import sqlite3
```


```python
# Run this cell without changes
cnx = sqlite3.connect('data/pokemon.db')
```

### Question 1: Find all the pokemon on the `pokemon` table. 
### Display all columns.


```python
# Copy / paste this starter code into your answer cell
# Put your query into a string and assign it to q1
# pd.read_sql(q1, cnx) will pull the data and print a dataframe so you can check your work

q1 = ''
pd.read_sql(q1, cnx)
```


```python
### BEGIN SOLUTION

from test_scripts.test_class import Test
test = Test()

q1 = 'SELECT * FROM pokemon'
df1 = pd.read_sql(q1, cnx)

test.save(df1.columns, 'df1_columns')
test.save(df1, 'df1')

df1.head()

### END SOLUTION
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>id</th>
      <th>name</th>
      <th>base_experience</th>
      <th>weight</th>
      <th>height</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>0</td>
      <td>1</td>
      <td>bulbasaur</td>
      <td>64</td>
      <td>69</td>
      <td>7</td>
    </tr>
    <tr>
      <td>1</td>
      <td>2</td>
      <td>ivysaur</td>
      <td>142</td>
      <td>130</td>
      <td>10</td>
    </tr>
    <tr>
      <td>2</td>
      <td>3</td>
      <td>venusaur</td>
      <td>236</td>
      <td>1000</td>
      <td>20</td>
    </tr>
    <tr>
      <td>3</td>
      <td>4</td>
      <td>charmander</td>
      <td>62</td>
      <td>85</td>
      <td>6</td>
    </tr>
    <tr>
      <td>4</td>
      <td>5</td>
      <td>charmeleon</td>
      <td>142</td>
      <td>190</td>
      <td>11</td>
    </tr>
  </tbody>
</table>
</div>




```python
# PUT ALL WORK FOR THE ABOVE QUESTION ABOVE THIS CELL
# THIS UNALTERABLE CELL CONTAINS HIDDEN TESTS

### BEGIN HIDDEN TESTS


from test_scripts.test_class import Test
test = Test()

test.run_test(pd.read_sql(q1, cnx).columns, 
              'df1_columns',
              "Looks like you didn't have the right columns?"
             )

test.run_test(pd.read_sql(q1, cnx), 
              'df1',
              "Looks like you didn't have the right rows?"
             )


### END HIDDEN TESTS
```

### Question 2: Find all the rows from the "pokemon_types" table where the `type_id` is 3.
### Display `id`, `pokemon_id`, `type_id`


```python
# Copy / paste this starter code into your answer cell
# Put your query into a string and assign it to q2
# pd.read_sql(q2, cnx) will pull the data and print a dataframe so you can check your work

q2 = ''
pd.read_sql(q2, cnx)
```


```python
### BEGIN SOLUTION

from test_scripts.test_class import Test
test = Test()
    
q2 = 'SELECT * FROM pokemon_types WHERE type_id = 3'
df2 = pd.read_sql(q2, cnx)

test.save(df2.columns, 'df2_columns')
test.save(df2, 'df2')

df2.head()

### END SOLUTION
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>id</th>
      <th>pokemon_id</th>
      <th>type_id</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>0</td>
      <td>10</td>
      <td>6</td>
      <td>3</td>
    </tr>
    <tr>
      <td>1</td>
      <td>17</td>
      <td>12</td>
      <td>3</td>
    </tr>
    <tr>
      <td>2</td>
      <td>25</td>
      <td>16</td>
      <td>3</td>
    </tr>
    <tr>
      <td>3</td>
      <td>27</td>
      <td>17</td>
      <td>3</td>
    </tr>
    <tr>
      <td>4</td>
      <td>29</td>
      <td>18</td>
      <td>3</td>
    </tr>
  </tbody>
</table>
</div>




```python
# PUT ALL WORK FOR THE ABOVE QUESTION ABOVE THIS CELL
# THIS UNALTERABLE CELL CONTAINS HIDDEN TESTS

### BEGIN HIDDEN TESTS


from test_scripts.test_class import Test
test = Test()

test.run_test(pd.read_sql(q2, cnx).columns,
              'df2_columns',
              'looks like you didn"t include id, pokemon_id, and type_id?'
)

test.run_test(pd.read_sql(q2, cnx),
              'df2',
              "looks like you didn't have the right rows?"
)


### END HIDDEN TESTS
```

### Question 3: Find all the rows from the "pokemon_types" table where the associated type is "water". 

- Do so **without** hard-coding the id of the "water" type.  Use only the `name` field in the `types` table.

- Include `id`, `pokemon_id` and `type_id` in the view of the data.  IOW, as the columns of the printed-out dataframe. 


```python
# Copy / paste this starter code into your answer cell
# Put your query into a string and assign it to q3
# pd.read_sql(q3, cnx) will pull the data and print a dataframe so you can check your work

q3 = ''
pd.read_sql(q3, cnx)
```


```python
### BEGIN SOLUTION


from test_scripts.test_class import Test
test = Test()

q3 = '''
SELECT pokemon_types.*
FROM pokemon_types
INNER JOIN types 
    ON types.id = pokemon_types.type_id
WHERE types.name = "water"
'''
df3 = pd.read_sql(q3, cnx)

test.save(len(df3), 'df3_length')
test.save(df3.columns, 'df3_columns')
test.save(df3, 'df3')

df3.head()

### END SOLUTION
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>id</th>
      <th>pokemon_id</th>
      <th>type_id</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>0</td>
      <td>11</td>
      <td>7</td>
      <td>11</td>
    </tr>
    <tr>
      <td>1</td>
      <td>12</td>
      <td>8</td>
      <td>11</td>
    </tr>
    <tr>
      <td>2</td>
      <td>13</td>
      <td>9</td>
      <td>11</td>
    </tr>
    <tr>
      <td>3</td>
      <td>80</td>
      <td>54</td>
      <td>11</td>
    </tr>
    <tr>
      <td>4</td>
      <td>81</td>
      <td>55</td>
      <td>11</td>
    </tr>
  </tbody>
</table>
</div>




```python
# PUT ALL WORK FOR THE ABOVE QUESTION ABOVE THIS CELL
# THIS UNALTERABLE CELL CONTAINS HIDDEN TESTS

### BEGIN HIDDEN TESTS


from test_scripts.test_class import Test
test = Test()

test.run_test(len(pd.read_sql(q3, cnx)),
              'df3_length',
              "looks like you didn't have the right number of rows?"
)

test.run_test(pd.read_sql(q3, cnx).columns,
              'df3_columns',
              "looks like you didn't have `id`, `pokemon_id` and `type_id` as the columns?"
             )

test.run_test(pd.read_sql(q3, cnx),
              'df3',
              "looks like you had the wrong values?"
             )


### END HIDDEN TESTS
```

### Question 4: Find the names of all pokemon that have the "psychic" type.


```python
# Copy / paste this starter code into your answer cell
# Put your query into a string and assign it to q4
# pd.read_sql(q4, cnx) will pull the data and print a dataframe so you can check your work

q4 = ''
pd.read_sql(q4, cnx)
```


```python
### BEGIN SOLUTION


from test_scripts.test_class import Test
test = Test()

q4 = '''
SELECT pokemon.name
FROM pokemon
INNER JOIN pokemon_types
    ON pokemon_types.pokemon_id = pokemon.id
INNER JOIN types
    ON types.id = pokemon_types.type_id
WHERE types.name = "psychic"
'''
df4 = pd.read_sql(q4, cnx)

test.save(len(df4), 'df4_length')
test.save(df4, 'df4')



### END SOLUTION
```


```python
# PUT ALL WORK FOR THE ABOVE QUESTION ABOVE THIS CELL
# THIS UNALTERABLE CELL CONTAINS HIDDEN TESTS

### BEGIN HIDDEN TESTS


from test_scripts.test_class import Test
test = Test()

test.run_test(len(pd.read_sql(q4, cnx)),
              'df4_length',
              'looks like you had the wrong number of names?'
             )

test.run_test(pd.read_sql(q4, cnx),
              'df4',
              'looks like you had the wrong names?'
             )


### END HIDDEN TESTS
```

### Question 5: Find the average weight for each type. 

#### Order the results from highest weight to lowest weight. 

#### Display average weight as `AVG(weight)` and each type as `name`.  
IOW, the columns in the dataframe should be `AVG(weight)` and `name`


```python
# Copy / paste this starter code into your answer cell
# Put your query into a string and assign it to q5
# pd.read_sql(q5, cnx) will pull the data and print a dataframe so you can check your work

q5 = ''
pd.read_sql(q5, cnx)
```


```python
### BEGIN SOLUTION


from test_scripts.test_class import Test
test = Test()

q5 = '''
SELECT AVG(weight), types.name
FROM pokemon
INNER JOIN pokemon_types
    ON pokemon_types.pokemon_id = pokemon.id
INNER JOIN types
    ON types.id = pokemon_types.type_id
GROUP BY types.name
ORDER BY AVG(weight) DESC
'''
df5 = pd.read_sql(q5, cnx)

test.save(len(df5), 'df5_length')
test.save(df5.columns, 'df5_columns')
test.save(df5, 'df5')



### END SOLUTION
```


```python
# PUT ALL WORK FOR THE ABOVE QUESTION ABOVE THIS CELL
# THIS UNALTERABLE CELL CONTAINS HIDDEN TESTS

### BEGIN HIDDEN TESTS


from test_scripts.test_class import Test
test = Test()

test.run_test(len(pd.read_sql(q5, cnx)),
              'df5_length',
              "looks like you had the wrong number of rows?"
             )

test.run_test(pd.read_sql(q5, cnx).columns,
              'df5_columns',
              "looks like you named the columns incorrectly?"
             )

test.run_test(pd.read_sql(q5, cnx),
              'df5',
              "looks like you had the wrong values?"
             )


### END HIDDEN TESTS
```

### Question 6: Find the names and ids of all the pokemon that have more than 1 type. 

#### The two columns in the view of the data should be `id` and `name`


```python
# Copy / paste this starter code into your answer cell
# Put your query into a string and assign it to q6
# pd.read_sql(q6, cnx) will pull the data and print a dataframe so you can check your work

q6 = ''
pd.read_sql(q6, cnx)
```


```python
### BEGIN SOLUTION


from test_scripts.test_class import Test
test = Test()

q6 = '''
SELECT pokemon.id, pokemon.name
FROM pokemon
INNER JOIN pokemon_types
    ON pokemon.id = pokemon_types.pokemon_id
GROUP BY pokemon_id
HAVING COUNT(pokemon_id) > 1
'''
df6 = pd.read_sql(q6, cnx)

test.save(len(df6), 'len_df6')
test.save(df6.columns, 'col_df6')
test.save(df6, 'df6')


df6.head()
### END SOLUTION
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>id</th>
      <th>name</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>0</td>
      <td>1</td>
      <td>bulbasaur</td>
    </tr>
    <tr>
      <td>1</td>
      <td>2</td>
      <td>ivysaur</td>
    </tr>
    <tr>
      <td>2</td>
      <td>3</td>
      <td>venusaur</td>
    </tr>
    <tr>
      <td>3</td>
      <td>6</td>
      <td>charizard</td>
    </tr>
    <tr>
      <td>4</td>
      <td>12</td>
      <td>butterfree</td>
    </tr>
  </tbody>
</table>
</div>




```python
# PUT ALL WORK FOR THE ABOVE QUESTION ABOVE THIS CELL
# THIS UNALTERABLE CELL CONTAINS HIDDEN TESTS

### BEGIN HIDDEN TESTS


from test_scripts.test_class import Test
test = Test()

test.run_test(len(pd.read_sql(q6, cnx)),
              'len_df6',
              "looks like you had the wrong number of rows?"
             )

test.run_test(pd.read_sql(q6, cnx).columns,
              'col_df6',
              "looks like you had the wrong columns?"
             )

test.run_test(pd.read_sql(q6, cnx),
              'df6',
              "looks like you had the wrong values?"
             )

### END HIDDEN TESTS
```

### Question 7: Find the id of the type that has the most pokemon. 

#### The view of the data should have the columns `num_pokemon` and `type_id`


```python
# Copy / paste this starter code into your answer cell
# Put your query into a string and assign it to q7
# pd.read_sql(q7, cnx) will pull the data and print a dataframe so you can check your work

q7 = ''
pd.read_sql(q7, cnx)
```


```python
### BEGIN SOLUTION


from test_scripts.test_class import Test
test = Test()

q7 = '''
SELECT COUNT(pokemon_id) AS num_pokemon, type_id
FROM pokemon_types
GROUP BY type_id
ORDER BY num_pokemon DESC
LIMIT 1'''

df7 = pd.read_sql(q7, cnx)

test.save(len(df7), 'len_df7')
test.save(df7.columns, 'col_df7')
test.save(df7, 'df7')

df7.head()

### END SOLUTION
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>num_pokemon</th>
      <th>type_id</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>0</td>
      <td>33</td>
      <td>4</td>
    </tr>
  </tbody>
</table>
</div>




```python
# PUT ALL WORK FOR THE ABOVE QUESTION ABOVE THIS CELL
# THIS UNALTERABLE CELL CONTAINS HIDDEN TESTS

### BEGIN HIDDEN TESTS


from test_scripts.test_class import Test
test = Test()

test.run_test(len(pd.read_sql(q7, cnx)), 
              'len_df7', 
              "looks like you had the wrong length?"
             )

test.run_test(pd.read_sql(q7, cnx).columns, 
              'col_df7', 
              "looks like you had the wrong column names?"
             )

test.run_test(pd.read_sql(q7, cnx), 
              'df7', 
              "looks like you had the wrong values?"
             )


### END HIDDEN TESTS
```
