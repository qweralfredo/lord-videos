## DuckDB não é santo milagreiro

DuckDB é excelente na leitura de dados, e isso precisa ficar bem claro!

**Por quê?** Porque o DuckDB é um OLAP (Online Analytical Processing). Logo:

* Ele é ótimo para ler dados!!! Fato!!!
* Para gravar dados, vai depender...

**Gravação de Dados:**

Não existe bala de prata para gravação. Você precisará dimensionar os dados considerando alguns cenários:

* **Evite particionamento (Parquet):** Se o seu ambiente não for compatível com o volume de dados.
* **Utilize bibliotecas:**  Python (pandas, ibis, pyarrow, etc) podem ser muito úteis.
* **"Seek and Destroy":**  Divida o volume dos dados em partes menores, se possível.  Não seja preguiçoso!

**Leitura de Dados:**

Entenda a natureza dos bancos de dados e o plano de execução. Complexidade custa caro para sua aplicação.

* **Queries complexas:** Consultas como `select * from tabela order by campo limit 1%` ou qualquer outra que precise processar os dados em memória podem trazer os mesmos desafios que existiam antes do processamento distribuído com commodities como Hadoop, Spark, etc.

**Conselho de Pai:**

Mensure o volume dos dados *antes* de fazer besteira e culpar o patinho! Se estourou a memória com 32GB é porque a mensuração foi errada. Siga as boas práticas para ambientes DuckDB também!

**Links Úteis:**

* [Como ajustar workloads](https://duckdb.org/docs/guides/performance/how_to_tune_workloads.html)
* [Meu workload está lento](https://duckdb.org/docs/guides/performance/my_workload_is_slow)
