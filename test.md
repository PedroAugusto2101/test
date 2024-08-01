# LEFT AND RIGHT JOINS

## Diagrama INNER JOIN

---

Diagrama para um **`INNER JOIN`** **`ON`** campo **`id`**

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/85a3a532-c493-4960-a731-a4822a0ccf8d/e57e426b-d92e-4716-9c6e-f9f7005e88e8/Untitled.png)

- **`OUTER JOINs`** podem obeter valoress de outras tabelas, mesmo se não forem encontrados no campo que está sendo juntado

## LEFT JOIN diagrama inicial

---

- LEFT JOIN retornará **todos os valores da tabela da esquerda**, e aqueles da tabela da direita que dão match com o campo inicial

Diagrama para um **`LEFT JOIN`** **`ON`** campo **`id`**

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/85a3a532-c493-4960-a731-a4822a0ccf8d/6f44674c-f627-4b7e-b0a1-4f35873d19aa/Untitled.png)

## Diagrama LEFT JOIN

---

Diagrama para um **`LEFT JOIN`** **`ON`** campo **`id`**

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/85a3a532-c493-4960-a731-a4822a0ccf8d/93be1f40-1412-410a-a83a-26b33395289e/Untitled.png)

## Sintaxe LEFT JOIN

---

```sql
SELECT p1.country, prime_minister, president
FROM prime_ministers AS p1
LEFT JOIN presidents AS p2
USING(country);
```

**Nota**. **`LEFT JOIN`** também pode ser escrito como **`LEFT OUTER JOIN`**

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/85a3a532-c493-4960-a731-a4822a0ccf8d/7dba987a-5aaf-4fab-b9eb-c5f7c01a4f50/Untitled.png)

## RIGHT JOIN

---

Diagrama para um **`RIGHT JOIN`** **`ON`** campo **`id`**

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/85a3a532-c493-4960-a731-a4822a0ccf8d/140e6941-6e6c-40d4-abd7-0436173ca316/Untitled.png)

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

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/85a3a532-c493-4960-a731-a4822a0ccf8d/cc3c9e83-8692-4daa-adda-adb9d24ed482/Untitled.png)

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

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/85a3a532-c493-4960-a731-a4822a0ccf8d/a674c5ca-37d2-4aac-b113-56d866256026/Untitled.png)

- **`FULL JOIN`** retornará todos os valores, independentemente se eles tiveram um match ou não

## FULL JOIN diagrama

---

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/85a3a532-c493-4960-a731-a4822a0ccf8d/1c13a17f-149f-4fb3-9bb8-15c5a0e34a68/Untitled.png)

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

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/85a3a532-c493-4960-a731-a4822a0ccf8d/4ce52e5f-3c34-4365-afee-e39b5d565107/Untitled.png)

- Depois do **`FULL JOIN`** sempre tem que ter o **`ON`**

# CROSSING INTO CROSS JOIN

## Diagrama CROSS JOIN

---

- **`CROSS JOIN`** permite todas as combinações possíveis entre duas tabelas.

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/85a3a532-c493-4960-a731-a4822a0ccf8d/fc1b7f5f-93f3-43ba-9f14-3c83b7a183ae/Untitled.png)

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

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/85a3a532-c493-4960-a731-a4822a0ccf8d/3f7505d5-e870-493e-873a-27195068fe48/Untitled.png)

# SELF JOINS

- **Self joins** são tabelas juntas com elas mesmas
- Podem ser usadas para comparar partes de uma mesma tabela
- Nomeação utilizando o `AS` é necessário no `SELF JOIN`

### Tabela `prime_ministers` **da base de dados dos líderes mundiais**

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/85a3a532-c493-4960-a731-a4822a0ccf8d/a0ce2701-bb0c-4796-b63d-eb6f0e372d91/Untitled.png)

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

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/85a3a532-c493-4960-a731-a4822a0ccf8d/d9130806-e907-40bb-8dfd-35d629108f61/Untitled.png)

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

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/85a3a532-c493-4960-a731-a4822a0ccf8d/a97f18a2-4fb0-4be7-aedb-c5c764716d5f/ff88cfa6-e272-421c-aa58-f78518498af5.png)
