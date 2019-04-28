---
title: SQL Server 結構描述集合
ms.date: 03/30/2017
ms.assetid: c6403cc3-d78b-4f85-bab1-ada7a3446ec5
ms.openlocfilehash: 79bf9f1253b64863d3eabddff8c33b6ffab70f41
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61878456"
---
# <a name="sql-server-schema-collections"></a>SQL Server 結構描述集合
除了通用結構描述集合之外，Microsoft .NET Framework Data Provider for SQL Server 還支援其他結構描述集合。 這些結構描述集合會因您目前使用的 SQL Server 版本而稍微不同。 若要判斷支援的結構描述集合清單，請呼叫**GetSchema**方法沒有引數，或以結構描述集合名稱"MetaDataCollections"。 這會傳回 <xref:System.Data.DataTable>，包括支援的結構描述集合清單、每個集合所支援的限制數目，以及集合所使用之識別項部分的數目。  
  
## <a name="databases"></a>資料庫  
  
|ColumnName|DataType|描述|  
|----------------|--------------|-----------------|  
|database_name|String|資料庫的名稱。|  
|dbid|Int16|資料庫 ID。|  
|create_date|DateTime|資料庫的建立日期。|  
  
## <a name="foreign-keys"></a>外部索引鍵  
  
|ColumnName|DataType|描述|  
|----------------|--------------|-----------------|  
|CONSTRAINT_CATALOG|String|條件約束所屬的目錄。|  
|CONSTRAINT_SCHEMA|String|包含條件約束的結構描述。|  
|CONSTRAINT_NAME|String|名稱。|  
|TABLE_CATALOG|String|包含條件約束的資料表名稱。|  
|TABLE_SCHEMA|String|包含資料表的結構描述。|  
|TABLE_NAME|String|資料表名稱|  
|CONSTRAINT_TYPE|String|條件約束的型別。 僅允許 FOREIGN KEY。|  
|IS_DEFERRABLE|String|指定條件約束是否可以延遲。 傳回 NO。|  
|INITIALLY_DEFERRED|String|指定條件約束一開始是否可以延遲。 傳回 NO。|  
  
## <a name="indexes"></a>索引  
  
|ColumnName|DataType|描述|  
|----------------|--------------|-----------------|  
|constraint_catalog|String|索引所屬的目錄。|  
|constraint_schema|String|包含索引的結構描述。|  
|constraint_name|String|索引名稱。|  
|table_catalog|String|與索引相關的資料表名稱。|  
|table_schema|String|包含與索引相關之資料表的結構描述。|  
|table_name|String|資料表名稱。|  
|index_name|String|索引名稱。|  
  
### <a name="indexes-sql-server-2008"></a>Indexes (SQL Server 2008)  
 從 .NET Framework 3.5 版 SP1 和 SQL Server 2008 開始，下列資料行就已經加入至 Indexes 結構描述集合，以便支援新的空間類型、Filestream 和疏鬆資料行。 舊版 .NET Framework 和 SQL Server 不支援這些資料行。  
  
|ColumnName|DataType|描述|  
|----------------|--------------|-----------------|  
|type_desc|String|索引的類型將屬於下列其中一種類型：<br /><br /> -   HEAP<br />叢集<br />-非叢集<br />-   XML<br />-   SPATIAL|  
  
## <a name="indexcolumns"></a>IndexColumns  
  
|ColumnName|DataType|描述|  
|----------------|--------------|-----------------|  
|constraint_catalog|String|索引所屬的目錄。|  
|constraint_schema|String|包含索引的結構描述。|  
|constraint_name|String|索引名稱。|  
|table_catalog|String|與索引相關的資料表名稱。|  
|table_schema|String|包含與索引相關之資料表的結構描述。|  
|table_name|String|資料表名稱。|  
|column_name|String|與索引相關的資料行名稱。|  
|ordinal_position|Int32|資料行序數位置。|  
|KeyType|Byte|物件的型別。|  
|index_name|String|索引名稱。|  
  
## <a name="procedures"></a>程序  
  
|ColumnName|DataType|描述|  
|----------------|--------------|-----------------|  
|SPECIFIC_CATALOG|String|目錄的特定名稱。|  
|SPECIFIC_SCHEMA|String|結構描述的特定名稱。|  
|SPECIFIC_NAME|String|目錄的特定名稱。|  
|ROUTINE_CATALOG|String|預存程序所屬的目錄。|  
|ROUTINE_SCHEMA|String|包含預存程序的結構描述。|  
|ROUTINE_NAME|String|預存程序的名稱。|  
|ROUTINE_TYPE|String|針對預存程序傳回 PROCEDURE，並針對函式傳回 FUNCTION。|  
|CREATED|DateTime|建立程序的時間。|  
|LAST_ALTERED|DateTime|上次修改程序的時間。|  
  
## <a name="procedure-parameters"></a>Procedure Parameters  
  
|ColumnName|DataType|描述|  
|----------------|--------------|-----------------|  
|SPECIFIC_CATALOG|String|此為其參數之程序的目錄名稱。|  
|SPECIFIC_SCHEMA|String|包含此參數所屬程序的結構描述。|  
|SPECIFIC_NAME|String|此參數所屬程序的名稱。|  
|ORDINAL_POSITION|Int32|以 1 開始的參數序數位置。 若為程序的傳回值，則此項為 0。|  
|PARAMETER_MODE|String|若為輸入參數，傳回 IN；若為輸出參數，傳回 OUT；若為輸入/輸出參數，傳回 INOUT。|  
|IS_RESULT|String|若表示做為函式之程序的結果，傳回 YES。 否則，傳回 NO。|  
|AS_LOCATOR|String|若宣告為定位器，傳回 YES。 否則，傳回 NO。|  
|PARAMETER_NAME|String|參數名稱。 若對應至函式的傳回值，則為 NULL。|  
|DATA_TYPE|String|系統提供的資料型別。|  
|CHARACTER_MAXIMUM_LENGTH|Int32|二進位或字元資料型別的長度上限 (字元數)。 否則，傳回 NULL。|  
|CHARACTER_OCTET_LENGTH|Int32|二進位或字元資料型別的最大長度 (以位元組為單位)。 否則，傳回 NULL。|  
|COLLATION_CATALOG|String|參數集合的目錄名稱。 若不是其中一個字元型別，則傳回 NULL。|  
|COLLATION_SCHEMA|String|永遠傳回 NULL。|  
|COLLATION_NAME|String|參數集合的名稱。 若不是其中一個字元型別，則傳回 NULL。|  
|CHARACTER_SET_CATALOG|String|參數字元集的目錄名稱。 若不是其中一個字元型別，則傳回 NULL。|  
|CHARACTER_SET_SCHEMA|String|永遠傳回 NULL。|  
|CHARACTER_SET_NAME|String|參數字元集的名稱。 若不是其中一個字元型別，則傳回 NULL。|  
|NUMERIC_PRECISION|Byte|概略數值資料、精確數值資料、整數資料或貨幣資料的精確度。 否則，傳回 NULL。|  
|NUMERIC_PRECISION_RADIX|Int16|概略數值資料、精確數值資料、整數資料或貨幣資料的精確度基數。 否則，傳回 NULL。|  
|NUMERIC_SCALE|Int32|概略數值資料、精確數值資料、整數資料或貨幣資料的小數位數。 否則，傳回 NULL。|  
|DATETIME_PRECISION|Int16|若參數型別為 datetime 或 smalldatetime，則為以分數秒為單位的精確度。 否則，傳回 NULL。|  
|INTERVAL_TYPE|String|NULL。 保留供 SQL Server 日後使用。|  
|INTERVAL_PRECISION|Int16|NULL。 保留供 SQL Server 日後使用。|  
  
## <a name="tables"></a>資料表  
  
|ColumnName|DataType|描述|  
|----------------|--------------|-----------------|  
|TABLE_CATALOG|String|資料表的目錄。|  
|TABLE_SCHEMA|String|包含資料表的結構描述。|  
|TABLE_NAME|String|資料表名稱。|  
|TABLE_TYPE|String|資料表型別。 可為 VIEW 或 BASE TABLE。|  
  
## <a name="columns"></a>資料行  
  
|ColumnName|DataType|描述|  
|----------------|--------------|-----------------|  
|TABLE_CATALOG|String|資料表的目錄。|  
|TABLE_SCHEMA|String|包含資料表的結構描述。|  
|TABLE_NAME|String|資料表名稱。|  
|COLUMN_NAME|String|資料行名稱。|  
|ORDINAL_POSITION|Int32|資料行識別碼。|  
|COLUMN_DEFAULT|String|資料行的預設值。|  
|IS_NULLABLE|String|資料行的 Null 屬性。 若此資料行允許 NULL，其會傳回 YES。 否則，傳回 NO。|  
|DATA_TYPE|String|系統提供的資料型別。|  
|CHARACTER_MAXIMUM_LENGTH|Int32 – Sql8, Int16 – Sql7|二進位資料、字元資料或文字及影像資料的長度上限 (以字元數為單位)。 否則，傳回 NULL。|  
|CHARACTER_OCTET_LENGTH|Int32 – SQL8, Int16 – Sql7|二進位資料、字元資料或文件及影像資料的長度上限 (以位元組為單位)。 否則，傳回 NULL。|  
|NUMERIC_PRECISION|Unsigned Byte|概略數值資料、精確數值資料、整數資料或貨幣資料的精確度。 否則，傳回 NULL。|  
|NUMERIC_PRECISION_RADIX|Int16|概略數值資料、精確數值資料、整數資料或貨幣資料的精確度基數。 否則，傳回 NULL。|  
|NUMERIC_SCALE|Int32|概略數值資料、精確數值資料、整數資料或貨幣資料的小數位數。 否則，傳回 NULL。|  
|DATETIME_PRECISION|Int16|datetime 及 SQL-92 間隔資料型別的子型別程式碼。 若為其他資料型別，則傳回 NULL。|  
|CHARACTER_SET_CATALOG|String|若資料行為字元資料或文字資料型別，則傳回 master，表示字元集所在的資料庫。 否則，傳回 NULL。|  
|CHARACTER_SET_SCHEMA|String|永遠傳回 NULL。|  
|CHARACTER_SET_NAME|String|若此資料行為字元資料或文字資料型別，則傳回字元集的唯一名稱。 否則，傳回 NULL。|  
|COLLATION_CATALOG|String|若資料行為字元資料或文字資料型別，則傳回 master，表示定義定序的資料庫。 否則，此資料行為 UNLL。|  
  
### <a name="columns-sql-server-2008"></a>Columns (SQL Server 2008)  
 從 .NET Framework 3.5 版 SP1 和 SQL Server 2008 開始，下列資料行就已經加入至 Columns 結構描述集合，以便支援新的空間類型、Filestream 和疏鬆資料行。 舊版 .NET Framework 和 SQL Server 不支援這些資料行。  
  
|ColumnName|DataType|描述|  
|----------------|--------------|-----------------|  
|IS_FILESTREAM|String|YES (如果資料行具有 FILESTREAM 屬性)。<br /><br /> NO (如果資料行沒有 FILESTREAM 屬性)。|  
|IS_SPARSE|String|YES (如果資料行是疏鬆資料行)。<br /><br /> NO (如果資料行不是疏鬆資料行)。|  
|IS_COLUMN_SET|String|YES (如果資料行是資料行集資料行)。<br /><br /> NO (如果資料行不是資料行集資料行)。|  
  
### <a name="allcolumns-sql-server-2008"></a>AllColumns (SQL Server 2008)  
 從 .NET Framework 3.5 版 SP1 和 SQL Server 2008 開始，就已經加入 AllColumns 結構描述集合，以便支援疏鬆資料行。 舊版 .NET Framework 和 SQL Server 不支援 AllColumns。  
  
 AllColumns 與 Columns 結構描述集合具有相同的限制和產生的 DataTable 結構描述。 唯一的差異是 AllColumns 包含了 Columns 結構描述集合並未包含的資料行集資料行。 下表將描述這些資料行。  
  
|ColumnName|DataType|描述|  
|----------------|--------------|-----------------|  
|TABLE_CATALOG|String|資料表的目錄。|  
|TABLE_SCHEMA|String|包含資料表的結構描述。|  
|TABLE_NAME|String|資料表名稱。|  
|COLUMN_NAME|String|資料行名稱。|  
|ORDINAL_POSITION|Int32|資料行識別碼。|  
|COLUMN_DEFAULT|String|資料行的預設值。|  
|IS_NULLABLE|String|資料行的 Null 屬性。 若此資料行允許 NULL，其會傳回 YES。 否則，會傳回 NO。|  
|DATA_TYPE|String|系統提供的資料型別。|  
|CHARACTER_MAXIMUM_LENGTH|Int32|二進位資料、字元資料或文字及影像資料的長度上限 (以字元數為單位)。 否則，傳回 NULL。|  
|CHARACTER_OCTET_LENGTH|Int32|二進位資料、字元資料或文件及影像資料的長度上限 (以位元組為單位)。 否則，傳回 NULL。|  
|NUMERIC_PRECISION|Unsigned Byte|概略數值資料、精確數值資料、整數資料或貨幣資料的精確度。 否則，傳回 NULL。|  
|NUMERIC_PRECISION_RADIX|Int16|概略數值資料、精確數值資料、整數資料或貨幣資料的精確度基數。 否則，傳回 NULL。|  
|NUMERIC_SCALE|Int32|概略數值資料、精確數值資料、整數資料或貨幣資料的小數位數。 否則，傳回 NULL。|  
|DATETIME_PRECISION|Int16|datetime 及 SQL-92 間隔資料型別的子型別程式碼。 若為其他資料型別，則傳回 NULL。|  
|CHARACTER_SET_CATALOG|String|若資料行為字元資料或文字資料型別，則傳回 master，表示字元集所在的資料庫。 否則，傳回 NULL。|  
|CHARACTER_SET_SCHEMA|String|永遠傳回 NULL。|  
|CHARACTER_SET_NAME|String|若此資料行為字元資料或文字資料型別，則傳回字元集的唯一名稱。 否則，傳回 NULL。|  
|COLLATION_CATALOG|String|若資料行為字元資料或文字資料型別，則傳回 master，表示定義定序的資料庫。 否則，此資料行為 UNLL。|  
|IS_FILESTREAM|String|YES (如果資料行具有 FILESTREAM 屬性)。<br /><br /> NO (如果資料行沒有 FILESTREAM 屬性)。|  
|IS_SPARSE|String|YES (如果資料行是疏鬆資料行)。<br /><br /> NO (如果資料行不是疏鬆資料行)。|  
|IS_COLUMN_SET|String|YES (如果資料行是資料行集資料行)。<br /><br /> NO (如果資料行不是資料行集資料行)。|  
  
### <a name="columnsetcolumns-sql-server-2008"></a>ColumnSetColumns (SQL Server 2008)  
 從 .NET Framework 3.5 版 SP1 和 SQL Server 2008 開始，就已經加入 ColumnSetColumns 結構描述集合，以便支援疏鬆資料行。 舊版 .NET Framework 和 SQL Server 不支援 ColumnSetColumns。 ColumnSetColumns 結構描述集合會針對資料行集中的所有資料行傳回結構描述。 下表將描述這些資料行。  
  
|ColumnName|DataType|描述|  
|----------------|--------------|-----------------|  
|TABLE_CATALOG|String|資料表的目錄。|  
|TABLE_SCHEMA|String|包含資料表的結構描述。|  
|TABLE_NAME|String|資料表名稱。|  
|COLUMN_NAME|String|資料行名稱。|  
|ORDINAL_POSITION|Int32|資料行識別碼。|  
|COLUMN_DEFAULT|String|資料行的預設值。|  
|IS_NULLABLE|String|資料行的 Null 屬性。 若此資料行允許 NULL，其會傳回 YES。 否則，會傳回 NO。|  
|DATA_TYPE|String|系統提供的資料型別。|  
|CHARACTER_MAXIMUM_LENGTH|Int32|二進位資料、字元資料或文字及影像資料的長度上限 (以字元數為單位)。 否則，傳回 NULL。|  
|CHARACTER_OCTET_LENGTH|Int32|二進位資料、字元資料或文件及影像資料的長度上限 (以位元組為單位)。 否則，傳回 NULL。|  
|NUMERIC_PRECISION|Unsigned Byte|概略數值資料、精確數值資料、整數資料或貨幣資料的精確度。 否則，傳回 NULL。|  
|NUMERIC_PRECISION_RADIX|Int16|概略數值資料、精確數值資料、整數資料或貨幣資料的精確度基數。 否則，傳回 NULL。|  
|NUMERIC_SCALE|Int32|概略數值資料、精確數值資料、整數資料或貨幣資料的小數位數。 否則，傳回 NULL。|  
|DATETIME_PRECISION|Int16|datetime 及 SQL-92 間隔資料型別的子型別程式碼。 若為其他資料型別，則傳回 NULL。|  
|CHARACTER_SET_CATALOG|String|若資料行為字元資料或文字資料型別，則傳回 master，表示字元集所在的資料庫。 否則，傳回 NULL。|  
|CHARACTER_SET_SCHEMA|String|永遠傳回 NULL。|  
|CHARACTER_SET_NAME|String|若此資料行為字元資料或文字資料型別，則傳回字元集的唯一名稱。 否則，傳回 NULL。|  
|COLLATION_CATALOG|String|若資料行為字元資料或文字資料型別，則傳回 master，表示定義定序的資料庫。 否則，此資料行為 UNLL。|  
|IS_FILESTREAM|String|YES (如果資料行具有 FILESTREAM 屬性)。<br /><br /> NO (如果資料行沒有 FILESTREAM 屬性)。|  
|IS_SPARSE|String|YES (如果資料行是疏鬆資料行)。<br /><br /> NO (如果資料行不是疏鬆資料行)。|  
|IS_COLUMN_SET|String|YES (如果資料行是資料行集資料行)。<br /><br /> NO (如果資料行不是資料行集資料行)。|  
  
## <a name="users"></a>使用者  
  
|ColumnName|DataType|描述|  
|----------------|--------------|-----------------|  
|uid|Int16|使用者 ID，在此資料庫中是唯一的。 1 是資料庫擁有人。|  
|user_name|String|使用者名稱或群組名稱，在此資料庫中是唯一的。|  
|createdate|DateTime|加入帳戶的日期。|  
|updatedate|DateTime|上次變更帳戶的日期。|  
  
## <a name="views"></a>檢視  
  
|ColumnName|DataType|描述|  
|----------------|--------------|-----------------|  
|TABLE_CATALOG|String|檢視表的目錄。|  
|TABLE_SCHEMA|String|包含檢視表的結構描述。|  
|TABLE_NAME|String|檢視表名稱。|  
|CHECK_OPTION|String|WITH CHECK OPTION 的型別。 若原始檢視表是使用 WITH CHECK OPTION 所建立的，則為 CASCADE。 否則，傳回 NONE。|  
|IS_UPDATABLE|String|指定檢視表是否可以更新。 永遠傳回 NO。|  
  
## <a name="viewcolumns"></a>ViewColumns  
  
|ColumnName|DataType|描述|  
|----------------|--------------|-----------------|  
|VIEW_CATALOG|String|檢視表的目錄。|  
|VIEW_SCHEMA|String|包含檢視表的結構描述。|  
|VIEW_NAME|String|檢視表名稱。|  
|TABLE_CATALOG|String|與此檢視表相關之資料表的目錄。|  
|TABLE_SCHEMA|String|包含與此檢視表相關之資料表的結構描述。|  
|TABLE_NAME|String|與檢視表相關之資料表的名稱。 基底資料表。|  
|COLUMN_NAME|String|資料行名稱。|  
  
## <a name="userdefinedtypes"></a>UserDefinedTypes  
  
|ColumnName|DataType|描述|  
|----------------|--------------|-----------------|  
|assembly_name|String|組件檔案的名稱。|  
|udt_name|String|組件的類別名稱。|  
|version_major|Object|主要版本號碼。|  
|version_minor|Object|次要版本號碼。|  
|version_build|Object|組建編號。|  
|version_revision|Object|修訂編號。|  
|culture_info|Object|與此 UDT 相關的文化特性資訊。|  
|public_key|Object|此組件使用的公開金鑰。|  
|is_fixed_length|Boolean|指定型別的長度是否永遠與 max_length 相同。|  
|max_length|Int16|型別的最大長度 (以位元組為單位)。|  
|Create_Date|DateTime|建立/登錄組件的日期。|  
|Permission_set_desc|String|組件使用權限集合/安全性層級的易記名稱。|  
  
## <a name="see-also"></a>另請參閱

- [擷取資料庫結構描述資訊](../../../../docs/framework/data/adonet/retrieving-database-schema-information.md)
- [ADO.NET Managed 提供者和 DataSet 開發人員中心](https://go.microsoft.com/fwlink/?LinkId=217917)
