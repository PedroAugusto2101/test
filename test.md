# Outer Joins, Cross Joins e Self Joins

# LEFT AND RIGHT JOINS

## Diagrama INNER JOIN

---

Diagrama para um **`INNER JOIN`** **`ON`** campo **`id`**

![Untitled](Outer%20Joins,%20Cross%20Joins%20e%20Self%20Joins%207c895988a89340cdae6e68096d9d8fe1/Untitled.png)

- **`OUTER JOINs`** podem obeter valoress de outras tabelas, mesmo se não forem encontrados no campo que está sendo juntado

## LEFT JOIN diagrama inicial

---

- LEFT JOIN retornará **todos os valores da tabela da esquerda**, e aqueles da tabela da direita que dão match com o campo inicial

Diagrama para um **`LEFT JOIN`** **`ON`** campo **`id`**

![Untitled](Outer%20Joins,%20Cross%20Joins%20e%20Self%20Joins%207c895988a89340cdae6e68096d9d8fe1/Untitled%201.png)

## Diagrama LEFT JOIN

---

Diagrama para um **`LEFT JOIN`** **`ON`** campo **`id`**

![Untitled](Outer%20Joins,%20Cross%20Joins%20e%20Self%20Joins%207c895988a89340cdae6e68096d9d8fe1/Untitled%202.png)

## Sintaxe LEFT JOIN

---

```sql
SELECT p1.country, prime_minister, president
FROM prime_ministers AS p1
LEFT JOIN presidents AS p2
USING(country);
```

**Nota**. **`LEFT JOIN`** também pode ser escrito como **`LEFT OUTER JOIN`**

![Untitled](Outer%20Joins,%20Cross%20Joins%20e%20Self%20Joins%207c895988a89340cdae6e68096d9d8fe1/Untitled%203.png)

## RIGHT JOIN

---

Diagrama para um **`RIGHT JOIN`** **`ON`** campo **`id`**

![Untitled](Outer%20Joins,%20Cross%20Joins%20e%20Self%20Joins%207c895988a89340cdae6e68096d9d8fe1/Untitled%204.png)

- Menos comum que o **`LEFT JOIN`**
- Faz o papel reverso do **`LEFT JOIN`**

## Sintaxe RIGHT JOIN

---

```sql
SELECT *
FROM left_table
RIGHT JOIN right_table
ON left_table.id = right_table.id;
```

**Note**. **`RIGHT JOIN`** também pode ser escrito como **`RIGHT OUTER JOIN`**

## RIGHT JOIN com os presidentes e primeiros ministros

---

```sql
SELECT p1.country, prime_minister, president
FROM prime_ministers AS p1
RIGHT JOIN presidents AS p2
USING(country);
```

![Untitled](Outer%20Joins,%20Cross%20Joins%20e%20Self%20Joins%207c895988a89340cdae6e68096d9d8fe1/Untitled%205.png)

## LEFT JOIN ou RIGHT JOIN?

---

- **`RIGHT JOIN`** é menos comum do que o **`LEFT JOIN`**
- Qualquer **`RIGHT JOIN`** pode ser escrito usando o **`LEFT JOIN`**
- **`LEFT JOIN`** é mais intuitivo para usuários quando escrevendo da esquerda para a direita

# FULL JOINS

## FULL JOIN diagrama inicial

---

- **`FULL JOIN`** combina o **`LEFT JOIN`** e o **`RIGHT JOIN`**

Diagrama para um **`FULL JOIN`** **`ON`** campo **`id`**

![Untitled](Outer%20Joins,%20Cross%20Joins%20e%20Self%20Joins%207c895988a89340cdae6e68096d9d8fe1/Untitled%206.png)

- **`FULL JOIN`** retornará todos os valores, independentemente se eles tiveram um match ou não

## FULL JOIN diagrama

---

![Untitled](Outer%20Joins,%20Cross%20Joins%20e%20Self%20Joins%207c895988a89340cdae6e68096d9d8fe1/Untitled%207.png)

## FULL JOIN sintaxe

---

```sql
SELECT left_table.id AS L_id,
			 right_table.id AS R_id,
			 left_table.val AS L_val,
			 right_table.val AS R_val
FROM left_table
FULL JOIN right_table
USING(id);
```

**Nota**. A palavra chave **`FULL OUTER JOIN`** também pode ser usada.

## FULL JOIN exemplo usando banco de dados líderes

---

```sql
SELECT p1.country AS country, prime_minister, president
FROM prime_ministers AS p1
FULL JOIN presidents AS p2
ON p1.country = p2.country
LIMIT 10;
```

![Untitled](Outer%20Joins,%20Cross%20Joins%20e%20Self%20Joins%207c895988a89340cdae6e68096d9d8fe1/Untitled%208.png)

- Depois do **`FULL JOIN`** sempre tem que ter o **`ON`**

# CROSSING INTO CROSS JOIN

## Diagrama CROSS JOIN

---

- **`CROSS JOIN`** permite todas as combinações possíveis entre duas tabelas.

![Untitled](Outer%20Joins,%20Cross%20Joins%20e%20Self%20Joins%207c895988a89340cdae6e68096d9d8fe1/Untitled%209.png)

## Sintaxe do CROSS JOIN

---

```sql
SELECT id1, id2
FROM table1
CROSS JOIN table2;
```

## Relacionando primeiros ministros com presidentes

---

```sql
SELECT prime_minister, president
FROM prime_ministers AS p1
CROSS JOIN presidents AS p2
WHERE p1.continent IN ('Asia')
	AND p2.continent IN ('South America');
```

![Untitled](Outer%20Joins,%20Cross%20Joins%20e%20Self%20Joins%207c895988a89340cdae6e68096d9d8fe1/Untitled%2010.png)

# SELF JOINS

- **Self joins** são tabelas juntas com elas mesmas
- Podem ser usadas para comparar partes de uma mesma tabela
- Nomeação utilizando o `AS` é necessário no `SELF JOIN`

### Tabela `prime_ministers` **da base de dados dos líderes mundiais**

![Untitled](Outer%20Joins,%20Cross%20Joins%20e%20Self%20Joins%207c895988a89340cdae6e68096d9d8fe1/Untitled%2011.png)

## Primeiro ministro encontra primeiro ministro

---

```sql
SELECT
	p1.country AS country1,
	p2.country AS country2,
	p1.continent
FROM prime_ministers AS p1
INNER JOIN prime_ministers AS p2
ON p1.continent = p2.continent
LIMIT 10;
```

![Untitled](Outer%20Joins,%20Cross%20Joins%20e%20Self%20Joins%207c895988a89340cdae6e68096d9d8fe1/Untitled%2012.png)

```sql
SELECT
	p1.country AS country1,
	p2.country AS country2,
	p1.continent
FROM prime_ministers AS p1
INNER JOIN prime_ministers AS p2
ON p1.continent = p2.continent
	AND p1.country <> p2.country;
```

![Untitled](Outer%20Joins,%20Cross%20Joins%20e%20Self%20Joins%207c895988a89340cdae6e68096d9d8fe1/ff88cfa6-e272-421c-aa58-f78518498af5.png)
