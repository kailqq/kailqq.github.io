---
comments: true
---

# Relational Model

!!!info "relational model"
    - the relational model is vary simple and elegant
    - A relational database is a collection of relations (based on the relational model)
    - A relation is a table with columns and rows
    - relational model has two advantages:
          - straight forward data representation
          - ease with which even complex queries can be expressed
    - Owing to the great language SQL


<figure markdown="span">
![](./img/lec2-1.png){ width="400" }
<figcaption>Example</figcaption>
</figure>

The difference between relationship and relation

- A relationship is an association among several entities
- A relation is the mathematical concept, referred to as a table

Entity set and relationship set <--> real world

Relation---Table,tuple---row  <--> machine world


## Structure of Relational Databases


### Basic Structure

Formally,given sets $D_1,D_2,\ldots,D_n.(D_i|_{j=1,\ldots,k})$

A relation $r$ is a subset of 

\[
    D_1\times D_2\times\ldots\times D_n
\]

aka a **Cartesian product** of a list of domains $D_1,D_2,\ldots,D_n$

Thus,a relation is a set of $n$-tuples$(a_{1j},a_{2j},\ldots,a_{nj})$

where $a_{ij}\in D_i$

即一个关系是一个元组的集合，每个元组有$n$个属性，每个属性的值来自于一个域$D_i$

<figure markdown="span">
![](./img/lec2-2.png){ width="400" }
<figcaption>Example</figcaption>
</figure>

!!!eg
    ```python
    If 
         customer-name = {Jones, Smith, Curry, Lindsay} 
         customer-street = {Main, North, Park} 
         customer-city = {Harrison, Rye, Pittsfield} 
    Then r = {(Jones, Main, Harrison), 
              (Smith, North, Rye),
              (Curry, North, Rye),
              (Lindsay, Park, Pittsfield)}
                     
    is a relation over customer-name x customer-street x customer-city.  (total 36 tuples) 
    ```

### Attribute Types

Each attribute of a relation has a name

THe set of allowed values for each attribute is called the **domain** of the attribute

**Attribute values** are normally required to be atomic,i.e.,indivisible---1st normal form

- E,g multivalue attributes,composite attributes,derived attributes

For every domain , there exists a special value called **null** 

The null value causes complications(并发) in the definition of many operations. 

### Concepts about Relation

A relation is concerned with the following concepts:

- relation schema:describes the structure of the relation

EG.`Student-schema = (sid: string, name: string, sex: string, age: int, dept:  string)`

- relation instance: corresponds to the snapshot(快照) of the data in the relation at a given instant in time. 

```
Variable --- relation 
Variable  type --- relation schema 
Variable  value --- relation instance 
```

### Relation Schema

A **relation schema** is a blueprint or structure that defines the organization of data in a relational database. It specifies the **tables** (also called relations), the **attributes** (or columns), and the **data types** for each attribute. It serves as a way to describe the logical view of the data, but without the actual data being stored.

In a relational schema:
- Each **relation (table)** has a name.
- Each **attribute (column)** within the relation has a name and an associated data type (like `integer`, `varchar`, `date`, etc.).
- The **keys** for the relation are often defined, like primary keys, foreign keys, or unique keys.

For example, a relation schema for a `Student` table could look like this:

- **Student**(`student_id: INT`, `first_name: VARCHAR(50)`, `last_name: VARCHAR(50)`, `dob: DATE`)

Here:
- `Student` is the relation.(`student_id: INT`, `first_name: VARCHAR(50)`, `last_name: VARCHAR(50)`, `dob: DATE`)is the relation schema.
- `student_id`, `first_name`, `last_name`, and `dob` are the attributes.
- `INT`, `VARCHAR(50)`, and `DATE` are the data types for those attributes.

The relation schema helps in organizing the data in a relational database and ensures consistency, integrity, and the proper relationships between different tables.


### Relation Instance

The current values (i.e., relation instance) of a relation are specified  by a table. 

An element t of r is a tuple, represented by a row in a table. 

Let a tuple variable t be a tuple, then t[name] denotes the value of t on the name attribute. 

<figure markdown="span">
![relation instance](./img/lec2-3.png)
<figcaption>Example</figcaption>
</figure>

The order of tuples is *irrelevant* (i.e., tuples may be stored in an arbitrary). 

No duplicated tuples in a relation. Attribute values are atomic. 


### Key

let $K \subset R$,$K$ is a *superkey* (超码) of $R$ if values for $K$ are sufficient to identify a unique tuple of each possible relation $r(R)$

Eg,E.g., both {ID} and {ID, name} are superkeys of the relation instructor. 


$K$ is a *candidate key* (候选码) if K is minimal superkey. 

E.g., both {ID} and {name} are candidate keys of the relation instructor.Since each of them is a superkey and no any subset. 

$K$ is a *primary key* (主码), if $K$ is a candidate key and is defined by user explicitly. 

Primary key is usually marked by underline. 


*Foreign key* (外码) is a set of attributes in a relation that is a key of another relation.

Assume there exists relations $r$ and $s$: $r(A, B, C)$, $s(B, D)$, we can say that attribute $B$ in relation $r$ is foreign key referencing $s$, and $r$ is a referencing relation (参照关系), and $s$ is a referenced relation (被参照关系). 


**参照关系中外码的值必须在被参照关系中实际存在, 或为null**

Primary key and foreign key are integrated constraints. 
即外键和主键是一体的约束，协同工作。

