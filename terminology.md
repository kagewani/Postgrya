Here's a comparison table of database terminology:

| Common/Standard Term | PostgreSQL Specific Term | Description |
|---------------------|-------------------------|-------------|
| Row | Tuple | A single record in a table |
| Column | Attribute | A field within a table |
| Table | Relation | A structured collection of data |
| Data type | Type | The kind of data a column can hold |
| Primary key | Primary key | Unique identifier for rows (same) |
| Foreign key | Foreign key | Reference to another table (same) |
| Index | Index | Data structure for faster queries (same) |
| View | View | Virtual table based on a query (same) |
| Null value | Null value | Absence of data (same) |
| Constraint | Constraint | Rule enforced on data (same) |
| Query | Query | Request for data (same) |
| Transaction | Transaction | Unit of work (same) |

## Why the Different Terms?

PostgreSQL's terminology reflects its academic origins and adherence to **relational theory**. The terms "relation," "tuple," and "attribute" come from formal relational algebra and were coined by Edgar F. Codd, the inventor of the relational model.

In practice, PostgreSQL documentation and the community use both sets of terms interchangeably - you'll see "row" far more often than "tuple" in everyday usage. However, some internal system catalogs and error messages may use the formal terminology, so it's helpful to know both.

The formal terms are most commonly seen in:
- Academic contexts
- PostgreSQL's internal catalogs (like `pg_attribute`)
- Some error messages
- Advanced documentation about query planning and execution


Here's the updated table with Russian terminology:

| Common/Standard Term | PostgreSQL Specific Term | Russian Term (Русский) | Description |
|---------------------|-------------------------|---------------------|-------------|
| Row | Tuple | Строка / Кортеж | A single record in a table |
| Column | Attribute | Столбец / Колонка / Атрибут | A field within a table |
| Table | Relation | Таблица / Отношение | A structured collection of data |
| Data type | Type | Тип данных | The kind of data a column can hold |
| Primary key | Primary key | Первичный ключ | Unique identifier for rows |
| Foreign key | Foreign key | Внешний ключ | Reference to another table |
| Index | Index | Индекс | Data structure for faster queries |
| View | View | Представление | Virtual table based on a query |
| Null value | Null value | Null / Нулевое значение | Absence of data |
| Constraint | Constraint | Ограничение / Constraint | Rule enforced on data |
| Query | Query | Запрос | Request for data |
| Transaction | Transaction | Транзакция | Unit of work |
| Schema | Schema | Схема | Namespace for database objects |

## Notes on Russian Usage

In the Russian technical community, there's a blend of translated and transliterated terms:

- **Commonly translated**: строка, столбец, таблица, запрос, представление are standard in Russian documentation
- **Academic terms**: "кортеж" (tuple) and "отношение" (relation) appear in academic contexts and formal literature
- **Often transliterated or kept in English**: Many developers use English terms directly (index, constraint, view) especially in code comments and casual discussion
- **Mixed usage**: "Null" is often kept as-is rather than translated

The official Russian PostgreSQL documentation translates most terms, but in practice, Russian developers frequently mix Russian and English terminology depending on context.
