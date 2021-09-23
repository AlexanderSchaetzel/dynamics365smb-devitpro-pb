---
title: "Data Access"
description: Learn how to improve data access performance in Business Central.
ms.custom: na
ms.date: 09/23/2021
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: conceptual
ms.service: "dynamics365-business-central"
ms.search.keywords: data access,sql,partitioning,constraints
author: jswymer
---
# Data Access
Data that is needed in the client goes through the following path from the [!INCLUDE[server](../developer/includes/server.md)] to the SQL Server database:
1.  If the data is cached in the [!INCLUDE[server](../developer/includes/server.md)] data cache, it's returned.
2.  If the data isn't cached in the [!INCLUDE[server](../developer/includes/server.md)] data cache, it's fetched from SQL Server over the network as follows:
    1. If the data resides in SQL Servers data cache, it's returned.
    2. If the data doesn't reside in SQL Servers data cache, it's fetched from storage and returned.

## [!INCLUDE[prod_short](../developer/includes/prod_short.md)] Server data caching
In [!INCLUDE[prod_short](../developer/includes/prod_short.md)], the data cache is shared by all users who are connected to the same [!INCLUDE[server](../developer/includes/server.md)] instance. So, after one user has read a record, a second user who reads the same record gets it from the cache.  

The following AL methods use the cache system:  
-   GET  
-   GETBYSYSTEMID
-   FIND  
-   FINDFIRST  
-   FINDLAST  
-   FINDSET  
-   COUNT  
-   ISEMPTY  
-   CALCFIELDS  

There are two types of caches, global and private:  

-   Global cache is for all users connected to a [!INCLUDE[server](../developer/includes/server.md)] instance.  
-   Private cache is per user, per company, in a transactional scope. Data in a private cache for a given table and company is flushed when a transaction ends.  

The cache that is used is determined by the lock state of a table. If a table isn't locked, then the global cache is queried for data; otherwise, the private cache is queried.  

Results from query objects aren't cached.  

For a call to any of the **FIND** functions, 1024 rows are cached. You can set the size of the cache by using the **Data Cache Size** setting in the [!INCLUDE[server](../developer/includes/server.md)] configuration file. The default size is 9, which approximates a cache size of 500 MB. If you increase this number by one, then the cache size doubles.  

You can bypass the cache by using the [SELECTLATESTVERSION method \(Database\)](../developer/methods-auto/database/database-SELECTLATESTVERSION-method.md).  

[!INCLUDE[prod_short](../developer/includes/prod_short.md)] synchronizes caching between [!INCLUDE[server](../developer/includes/server.md)] instances that are connected to the same database. By default, the synchronization occurs every 30 seconds.  

You can set the cache synchronization interval by using the *CacheSynchronizationPeriod* parameter in the CustomSettings.config file. This parameter isn't included in the CustomSetting.config file by default, so you must add it manually using the following format:

```
<add key="CacheSynchronizationPeriod" value="hh:mm:ss" />
```
For example, to set the interval to 50 seconds, set the `value` to `"00:00:50"`. For more information about the CustomSettings.config file, see [Configuring Business Central Server](configure-server-instance.md).  

## [!INCLUDE[server](../developer/includes/server.md)] connections to SQL Server
Starting from [!INCLUDE[nav7long_md](../developer/includes/nav7long_md.md)], the [!INCLUDE[server](../developer/includes/server.md)] uses ADO.NET to connect to the SQL Server database. Installations of [!INCLUDE[nav2009](../developer/includes/nav2009_md.md)] and earlier uses ODBC to connect to the SQL Server database.

The ADO.NET interface is a managed data access layer that supports SQL Server connection pooling, which can dramatically decrease memory consumption by [!INCLUDE[server](../developer/includes/server.md)]. SQL Server connection pooling also simplifies deployment of the [!INCLUDE[prod_short](../developer/includes/prod_short.md)] three-tier architecture for deployments where the three tiers are installed on separate computers. Specifically, administrators are no longer required to manually create SPNs or to set up delegation when the client, [!INCLUDE[server](../developer/includes/server.md)], and SQL Server are on separate computers.  

There's no longer a one-to-one correlation between the number of client connections and the number of SQL Server connections. In earlier versions of [!INCLUDE[prod_short](../developer/includes/prod_short.md)], each SQL Server connection could consume up to 40 MB of memory. Additionally, memory allocation is now in managed memory, which is more efficient than unmanaged memory.  

 Records are retrieved using Multiple Active Result Sets \(MARS\). methods such as NEXT, FIND\('-'\), FIND\('+'\), FIND\('>'\), and FIND\('\<'\) are faster with MARS than the server cursors that earlier versions of [!INCLUDE[prod_short](../developer/includes/prod_short.md)] used.  

## <a name="readwrite"></a>Data read/write performance  
AL functions COUNT and AVERAGE formulas can use SIFT indexes. For more information, see [CALCSUMS method \(Record\)](../developer/methods-auto/record/record-CALCSUMS-method.md) and [CALCFIELDS method \(Record\)](../developer/methods-auto/record/record-CALCFIELDS-method.md). MIN and MAX formulas use SQL Server MIN and MAX functions exclusively.  

 RecordIds and SQL Variant columns in a table don't prevent the use of BULK inserts. For more information, see [Bulk Inserts](optimize-sql-bulk-inserts.md).  

In most cases, filtering on FlowFields issues a single SQL statement. In earlier versions of [!INCLUDE[prod_short](../developer/includes/prod_short.md)], filtering on FlowFields issued an SQL statement for each filtered FlowField and for each record in the table to calculate the filtered FlowFields. The exceptions in [!INCLUDE[prod_short](../developer/includes/prod_short.md)] in which filtering on FlowFields doesn't issue a single SQL statement are as follows:  

-   You use the ValueIsFilter option on a field and the field has a value.  

-   A second predicate is specified on a source field and the field that is used for the second predicate has a value. For example, when you specify the [CalcFormula Property](../developer/properties/devenv-CalcFormula-Property.md) for a FlowField, you can specify table filters in the **Calculation Formula** window. If you specify two or more filters on the same source field, then filtering doesn't issue a single SQL statement.  

<!-- property doesn't exist any longer
-   You specify **Validated** for the [SecurityFiltering Property](../developer/properties/devenv-SecurityFiltering-Property.md) on a record. This value for the **SecurityFiltering** property means that each record that is part of the calculation must be verified for inclusion in the security filter.  -->

In most cases, calling the FIND or NEXT functions after you have set the view to include only marked records issues a single SQL statement. In earlier versions of [!INCLUDE[prod_short](../developer/includes/prod_short.md)], calling FIND or NEXT functions that have marked records issued an SQL statement for each mark. There are some exceptions if many records are marked. For more information, see [MARKEDONLY method \(Record\)](../developer/methods-auto/record/record-MARKEDONLY-method.md).  

## <a name="TablePartitioning"></a>Using SQL Server table partitioning

Starting in [!INCLUDE[nav2018_md](../developer/includes/nav2018_md.md)], the use of SQL Server table and index partitioning is a supported configuration. The data of partitioned tables and indexes is divided into units that can be spread across more than one filegroup in a SQL Server database. All partitions of a single index or table must be in the same database. The table or index is treated as a single logical entity when queries or updates are done on the data. Before SQL Server 2016 SP1, partitioned tables and indexes weren't available in every edition of SQL Server.

Partitioning large tables or indexes can have the following manageability and performance benefits:

- You can do maintenance operations on one or more partitions more quickly. The operations are more efficient because they target only these data subsets, instead of the whole table. For example, you can choose to rebuild one or more partitions of an index.
- You can possibly improve query performance, based on the types of queries you frequently run and on your hardware configuration. When SQL Server does data sorting for I/O operations, it sorts the data first by partition. SQL Server accesses one drive at a time, which might reduce performance. To improve data sorting performance, stripe the data files of your partitions across more than one disk by setting up a RAID (redundant array of independent disks). In this way, although SQL Server still sorts data by partition, it can access all the drives of each partition at the same time.
- You can use partitioning to distribute parts of tables to different IO sub systems. For example, you could archive data for old transactions on slow and less expensive disks and keep current data on solid-state drives (SSD).
You can improve performance by enabling lock escalation at the partition level instead of a whole table. Doing so may also reduce lock contention on the table.

For more general information about partitioned tables and indexes in SQL Server, see [Partitioned Tables and Indexes](/sql/relational-databases/partitions/partitioned-tables-and-indexes).

### How [!INCLUDE[prod_short](../developer/includes/prod_short.md)] supports partitioning

If you have altered tables in a [!INCLUDE[prod_short](../developer/includes/prod_short.md)] database to make them partitioned tables, the synchronization engine, which is responsible for mapping the logical metamodel to physical tables, will respect this configuration during upgrades. After a schema upgrade, even if tables were dropped and recreated, the partitioning strategy that's applied to the original tables will be added to the upgraded tables.
You can create a partitioned table or index in SQL Server by using SQL Server Management Studio or Transact-SQL.

> [!NOTE]  
> For partitioning to work, the partition column must be part of the clustering key on the table.

### How to choose a good partitioning strategy

Choosing the right partitioning strategy for a table depends on the data distribution, data growth patterns, and the way data is queried. SQL optimizer uses a technique called *partition elimination* to improve performance by accessing only partitions that are needed to satisfy the query's filter criteria. For SQL optimizer to use partition elimination, the partition key must be present as a predicate in the WHERE clause of the SQL statement it needs to prepare an execution plan for. For tables such as ledgers, a data partition strategy that uses dates can be used to eliminate historical data from queries. For tables that have state, like a status field, and a highly skewed distribution with one or two end states as the majority, a strategy that partitions on the state field might be a good choice.

Data partitioning is a commonly used technique in data warehouses. Including the words “data warehouse” in an internet search for partitioning examples might help finding a strategy that matches your needs.

### Table partitioning example

This example uses Transact-SQL to change table **G_L Entry** to be partitioned on the **Posting Date** field, with data partitioned on the year, and where all partitions are aligned to the PRIMARY file group.

1. In SQL query editor, create a partition function that creates partitions that divide on year. This function can be used for partitioning multiple tables:

    ```sql
    CREATE PARTITION FUNCTION [DataHistoryPartitionmethod] (datetime)
    AS RANGE LEFT FOR VALUES (
    '20151231 23:59:59.997',
    '20161231 23:59:59.997',
    '20171231 23:59:59.997',
    '20181231 23:59:59.997'  )
    GO
    ```

2. Create a partition scheme that maps partitions to file groups. In this example, all partitions are mapped to the PRIMARY file group. This scheme can be used for partitioning multiple tables:

    ```sql
    CREATE PARTITION SCHEME DataHistoryPartitionScheme
    AS PARTITION DataHistoryPartitionmethod ALL TO ([PRIMARY])
    GO
    ```

3. In the [!INCLUDE[nav_dev_long_md](../developer/includes/nav_dev_long_md.md)], add the **Posting Date** field to the primary key.

    For more information, see [Table Keys](../developer/devenv-table-keys.md).

4. In the Transact-SQL Editor, partition table **G_L Entry** by using the previously defined partition scheme:

    ```tsql
    ALTER TABLE [dbo].[G_L Entry]  
    DROP CONSTRAINT [G_L Entry$0]
    GO

    ALTER TABLE [dbo].[G_L Entry]
    ADD CONSTRAINT [G_L Entry$0] PRIMARY KEY CLUSTERED
    (
    [$companyId], [Entry No_], [Posting Date]
    )
    ON DataHistoryPartitionScheme( [Posting Date] )
    GO
    ```

> [!TIP]
> SQL Server Management Studio includes the **Create Partition Wizard** to help you create partitioning functions, partitioning schemes, as well as changing a table to be partitioned. For more information, see [Create Partitioned Tables and Indexes](/sql/relational-databases/partitions/create-partitioned-tables-and-indexes).

## <a name="Compression"></a>Using SQL Server data compression

Since [!INCLUDE[prod_short](../developer/includes/prod_short.md)] April 2019, it's possible to configure data compression directly in table metadata by using the [CompressionType property](../developer/properties/devenv-compressiontype-property.md). Previously, compression could only be configured in SQL Server. You use data compression to help reduce the size of selected tables in the database. Besides saving space, data compression can help improve performance of I/O-intensive workloads because the data is stored in fewer pages and queries will read fewer pages from disk. So data compression is especially useful if your storage system is based on disks and not SSD.

However, extra CPU resources are required on the database server to compress and decompress the data while data is exchanged with the [!INCLUDE[server](../developer/includes/server.md)].

With the **CompressionType** property, you can configure row or page type compression or configure the table not to use compression. With these compression settings, [!INCLUDE[prod_short](../developer/includes/prod_short.md)] table synchronization process will make changes to the SQL Server table, overwriting the current compression type, if any. You can choose to control data compression directly on SQL Server by setting the **CompressionType** property to **Unspecified**, in which case table synchronization process won't control the data compression.

To evaluate whether a table is a good candidate to compress, you can use the stored procedure `sp_estimate_data_compression_savings` in SQL Server. For more information, see [sp_estimate_data_compression_savings (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-estimate-data-compression-savings-transact-sql).

Because SQL Server supports data compression on the partition level, you can combine SQL Server data compression with table partitioning to achieve flexible data archiving on historical parts of a large table, without having the CPU overhead on the active part of the table.

> [!NOTE]
> Prior to SQL Server 2016 SP1, compression wasn't available in every edition of SQL Server.

For more general information about table compression in SQL Server, see [Data Compression](/sql/relational-databases/data-compression/data-compression). For guidance on strategy, capacity planning, and best practices for data compression, see [Data Compression: Strategy, Capacity Planning, and Best Practices](/previous-versions/sql/sql-server-2008/dd894051(v=sql.100)).

## Default SQL constraints

To add a default constraint to a field (column), use the following SQL statement:

```sql
ALTER TABLE ADD CONSTRAINT constraint_name DEFAULT default_value FOR field_name
```

The name of the default constraint isn't important, as long as it isn't used by other columns in the table.

### Default constraint value

[!INCLUDE[prod_short](../developer/includes/prod_short.md)] sets default constraints on fields in a tables. The following table list the values used for default constraints for the different data types:

|Data type|value|
|---------|-------|
|Integer, Option, Boolean, Byte, Duration, BigInteger|0|
|Decimal|0.0|
|DateFormula|''|
|Text|N''|
|RecordId, TableFilter|0x00|
|Guid, Media, MediaSet| 00000000-0000-0000-0000-000000000000|
|Code (varies, depending on the SqlType)||
|Default, VarChar, Variant|N''|
|Integer, BigInt|0|
|Time, Date, DateTime|'1753.01.01'|

> [!NOTE]
> Blobs don't get default constraints, but they allowed to be null.

## See Also

[Query Objects and Performance](optimize-sql-query-objects-and-performance.md)  
[GetBySystemId(Guid)](../developer/methods-auto/record/record-getbysystemid-method.md)  
