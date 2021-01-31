uuid as primary key is today a standard solution for your table.

Main advantage:
- easier synchronization between instances
- more security compared to a sequential id (that can be used to attack the system)

``` sql
id uuid PRIMARY KEY DEFAULT uuid_generate_v4()
```
