### Explicação SQL

```sql
select t1.num_nota, t1.nome_consumidor, t2.quantidade,t2.valor_unitario, (t2.quantidade*t2.valor_unitario) as total from nota t1
join item_nota t2
on t1.num_nota = t2.num_nota
where t1.num_nota = 234;
```
O código a cima faz um join entre duas tabelas, "_nota_" e "_item_nota_".
Onde deveremos unir as duas tabelas, mostrando as seguintes colunas de cada tabela:

|nota|item_nota|
|-----|-----|
|num_nota|quantidade|
|nome_consumidor|valor_unitario|
| |total(quantidade*valor_unitario)|

Utilizando uma espécie de filtro, iremos juntar essas duas tabelas, **enquanto**(where) "_num_nota_ (pertencente a tabela nota)" for igual a 234.


```sql
select t1.num_nota, t1.nome_consumidor, t2.quantidade,t2.valor_unitario, (t2.quantidade*t2.valor_unitario) as total from nota t1
```
Em "_select_" é pedido ao código para que ele selecione, ou mostre as seguintes colunas:
num_nota, nome_consumidor, quantidade, valor_unitario. Porém percebemos que existem dois nomes diferentes no código "_t1_" e "_t2_". Esses dois nomes ainda não foram definidos no código, mas o significado é que demos um apelido as tabelas "_nota_" e "_item_nota_", sendo "_nota_" o "_t1_" e _"item_nota_" o "_t2_".<br>
Ao digitar ```t1.num_nota```, estamos especificando ao código que ele deve pegar a coluna "_num_nota_" da tabela "_t1_" ou seja da tabela "_nota_".
A mesma coisa ocorre nos outros parametros.
Depois disso teremos o trecho de código ``` (t2.quantidade*t2.valor_unitario) as total ```
Nesse trecho estamos dizendo ao SQL que ele deverá criar uma coluna nova, definindo ela como a multiplicação da coluna quantidade com a coluna "_valor_unitario_", ambas da tabela "_item_nota_" . No final teremos ```as total```, esse trecho da um apelido a tabela criada, multiplicando as colunas citadas anteriormente.<br>
Por ultimo teremos o ``` from nota t1``` onde diremos que queremos essas informações vindas de "_nota_" e dando um apelido a ela, como "_t1_".<br>
Esse tipo de prática pode parecer muita estranha no começo e provavelmente você deve estar se perguntando o por que de fazermos isso. Na verdade, dar apelidos a tabelas só nos ajuda a não precisar ficar escrevendo o nome da tabela em si. Existem diversas tabelas e normalmente elas tem nomes grandes e cheios de siglas. No momento em que realizamos uma consulta, esse tipo de prática pode poupar muito tempo.<br>

Ao começar com os estudos em SQL, temos algumas dificuldades com os famosos **join**.
A forma mais simples de explicarmos esse tipo de função é utilizando o Diagrama de Venn, que consiste em simbolizar graficamente a junção de determinados objetos.
Para o SQL, o Diagrama de Venn irá simplificar o entendimento da junção de duas ou mais tabelas. Veremos um exemplo a baixo:

![](http://sqlhints.com/wp-content/uploads/2016/10/LEFT-OUTER-JOIN-Venn-Diagram.jpg)

Nesse exemplo iremos dizer ao código que queremos tudo da tabela "_Orders_" que for igual a tabela "_Customers_" passando os parâmetros necessários para ligar uma coluna a outra. Resumindo de forma clara o código dirá: Selecione para mim todas as colunas (de ambas tabelas), apelidando a tabela "_CustomersId_" como "_C_" e realizando uma junção com a tabela "_Orders_", apelidada como "_O_". Por ultimo, diremos ao código que ele deve fazer isso juntando as informações pelas colunas "_CustomersId_" de ambas tabelas. Dessa forma, toda linha que contiver um valor atrelado a coluna "_CustomersId_" irá juntar suas informações da outra tabela que também tem valores atrelados a coluna "_CustomersId_".

Supondo que a tabela "_Customers_" tem as seguintes informações

>Customers

|CustomersId|Name|Number|
|---|---|
|1|Flex|32|
|2|Dijon|89|
|3|FireB|25|
|5|Walk|34|

E a tabela "_Order_" tenha os seguintes dados.
>Order

|CustomersId|Name_Order|Number_Order|
|---|---|
|1|Blood|322000|
|2|Water|28394|
|3|Ground|12253|
|4|Big|5672|

Realizando um **Left Join** as tabelas ficarão da seguinte forma.

|CustomersId|Name|Number|CustomersId|Name_Order|Number_Order|
|---|---|---|---|
|1|Flex|32|1|Blood|322000|
|2|Dijon|89|2|Water|28394|
|3|FireB|25|3|Ground|12253|

Ao visualizar essa tabela, com o **Left Join**, percebemos que ele não trouxe a linha com o "_CustomersId_" 5 da tabela "_Customers_" e nem a linha com "_CustomersId_" 4 da tabela "_Order_". Isso acontece por que queremos apenas os valores que são iguais em "_CustomersId_" para ambas tabelas.

```sql
where t1.num_nota = 234;
```
E por último, teremos o where, que traduzindo significa enquanto, ou seja, enquanto a coluna "_num_nota_" da tabela "_t1_"(Customers) for igual a 234.
Utilizando esse filtro você poderá trazer tudo de uma tabela, cruzando informações com outra tabela, enquanto o "_num_nota_" for igual a 234.
