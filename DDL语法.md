## DDL语法 (2017.10.11)
1. `WITH (OIDS=FALSE)`
```
等价于： WITHOUT OIDS
```
2. `WITH OIDS`
```
等价于： WITH (OIDS)
```
3. `with介绍`
```
WITH ( storage_parameter [= value] [, ... ] )
这个子句为表或指定一个可选的存储参数，参见存储参数获取更多信息。用于表的 WITH 子句还可以
包含 OIDS=TRUE 或单独的 OIDS 来指定给新表中的每一行都分配一个 OID(对象标识符)，或者
 OIDS=FALSE 表示不分配 OID 。如果没有指定 OIDS 默认行为取决于 default_with_oids 配置参数。
 如果新表是从有 OID 的表继承而来，那么即使明确指定 OIDS=FALSE 也将强制按照 OIDS=TRUE 执行。

如果明确或隐含的指定了 OIDS=FALSE ，新表将不会存储 OID ，也不会为行分配 OID 。这将减小 OID 的
开销并因此延缓了 32-bit OID 计数器的循环。因为一旦计数器发生循环之后 OID 将不能被视为唯一，这将
大大降低 OID 的实用性。另外，排除了 OID 的表也为每条记录减小了 4 字节的存储空间，从而可以稍微提
升一些性能。

可以使用 ALTER TABLE 从已有的表中删除 OID 列。
```
4. `DDL的写法--SQL语法的一部分`
```
DROP TABLE IF EXISTS "puton"."unit";
CREATE TABLE "puton"."unit" (
"uuid" uuid NOT NULL,
"planuuid" uuid,
"name" text COLLATE "default",
"mode" int2,
"area" text COLLATE "default",
"sex" int2,
"method" text COLLATE "default",
"status" int2 DEFAULT 0,
"bid" float8,
"age" jsonb
)
WITH (OIDS=FALSE)

;
```