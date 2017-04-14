---
title: "SQL Server 結構描述集合 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c6403cc3-d78b-4f85-bab1-ada7a3446ec5
caps.latest.revision: 5
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 5
---
# SQL Server 結構描述集合
除了通用結構描述集合之外，Microsoft .NET Framework Data Provider for SQL Server 還支援其他結構描述集合。  這些結構描述集合會因您目前使用的 SQL Server 版本而稍微不同。  若要判斷支援的結構描述集合清單，請呼叫 **GetSchema** 方法但不搭配任何引數或搭配結構描述集合名稱 "MetaDataCollections"。  這會傳回 <xref:System.Data.DataTable>，包括支援的結構描述集合清單、每個集合所支援的限制數目，以及集合所使用之識別項部分的數目。  
  
## 資料庫  
  
|ColumnName|DataType|描述|  
|----------------|--------------|--------|  
|database\_name|String|資料庫的名稱。|  
|Dbid|Int16|資料庫 ID。|  
|create\_date|DateTime|資料庫的建立日期。|  
  
## Foreign Keys  
  
|ColumnName|DataType|描述|  
|----------------|--------------|--------|  
|constraint\_catalog|String|條件約束所屬的目錄。|  
|constraint\_schema|String|包含條件約束的結構描述。|  
|constraint\_name|String|名稱。|  
|table\_catalog|String|包含條件約束的資料表名稱。|  
|table\_schema|String|包含資料表的結構描述。|  
|table\_name|String|資料表名稱|  
|constraint\_type|String|條件約束的型別。  僅允許 FOREIGN KEY。|  
|is\_deferrable|String|指定條件約束是否可以延遲。  傳回 NO。|  
|initially\_deferred|String|指定條件約束一開始是否可以延遲。  傳回 NO。|  
  
## Indexes  
  
|ColumnName|DataType|描述|  
|----------------|--------------|--------|  
|constraint\_catalog|String|索引所屬的目錄。|  
|constraint\_schema|String|包含索引的結構描述。|  
|constraint\_name|String|索引名稱。|  
|table\_catalog|String|與索引相關的資料表名稱。|  
|table\_schema|String|包含與索引相關之資料表的結構描述。|  
|table\_name|String|資料表名稱。|  
  
### Indexes \(SQL Server 2008\)  
 從 .NET Framework 3.5 版 SP1 和 SQL Server 2008 開始，下列資料行就已經加入至 Indexes 結構描述集合，以便支援新的空間類型、Filestream 和疏鬆資料行。  舊版 .NET Framework 和 SQL Server 不支援這些資料行。  
  
|ColumnName|DataType|描述|  
|----------------|--------------|--------|  
|type\_desc|String|索引的類型將屬於下列其中一種類型：<br /><br /> -   HEAP<br />-   CLUSTERED<br />-   NONCLUSTERED<br />-   XML<br />-   SPATIAL|  
  
## IndexColumns  
  
|ColumnName|DataType|描述|  
|----------------|--------------|--------|  
|constraint\_catalog|String|索引所屬的目錄。|  
|constraint\_schema|String|包含索引的結構描述。|  
|constraint\_name|String|索引名稱。|  
|table\_catalog|String|與索引相關的資料表名稱。|  
|table\_schema|String|包含與索引相關之資料表的結構描述。|  
|table\_name|String|資料表名稱。|  
|column\_name|String|與索引相關的資料行名稱。|  
|ordinal\_position|Int32|資料行序數位置。|  
|KeyType|UInt16|物件的型別。|  
  
## 程序  
  
|ColumnName|DataType|描述|  
|----------------|--------------|--------|  
|specific\_catalog|String|目錄的特定名稱。|  
|specific\_schema|String|結構描述的特定名稱。|  
|specific\_name|String|目錄的特定名稱。|  
|routine\_catalog|String|預存程序所屬的目錄。|  
|routine\_schema|String|包含預存程序的結構描述。|  
|routine\_name|String|預存程序的名稱。|  
|routine\_type|String|針對預存程序傳回 PROCEDURE，並針對函式傳回 FUNCTION。|  
|created|DateTime|建立程序的時間。|  
|last\_altered|DateTime|上次修改程序的時間。|  
  
## Procedure Parameters  
  
|ColumnName|DataType|描述|  
|----------------|--------------|--------|  
|specific\_catalog|String|此為其參數之程序的目錄名稱。|  
|specific\_schema|String|包含此參數所屬程序的結構描述。|  
|specific\_name|String|此參數所屬程序的名稱。|  
|ordinal\_position|Int16|以 1 開始的參數序數位置。  若為程序的傳回值，則此項為 0。|  
|parameter\_mode|String|若為輸入參數，傳回 IN；若為輸出參數，傳回 OUT；若為輸入\/輸出參數，傳回 INOUT。|  
|is\_result|String|若表示做為函式之程序的結果，傳回 YES。  否則，傳回 NO。|  
|as\_locator|String|若宣告為定位器，傳回 YES。  否則，傳回 NO。|  
|parameter\_name|String|參數名稱。  若對應至函式的傳回值，則為 NULL。|  
|data\_type|String|系統提供的資料型別。|  
|character\_maximum\_length|Int32|二進位或字元資料型別的長度上限 \(字元數\)。  否則，傳回 NULL。|  
|character\_octet\_length|Int32|二進位或字元資料型別的最大長度 \(以位元組為單位\)。  否則，傳回 NULL。|  
|collation\_catalog|String|參數集合的目錄名稱。  若不是其中一個字元型別，則傳回 NULL。|  
|collation\_schema|String|永遠傳回 NULL。|  
|collation\_name|String|參數集合的名稱。  若不是其中一個字元型別，則傳回 NULL。|  
|character\_set\_catalog|String|參數字元集的目錄名稱。  若不是其中一個字元型別，則傳回 NULL。|  
|character\_set\_schema|String|永遠傳回 NULL。|  
|character\_set\_name|String|參數字元集的名稱。  若不是其中一個字元型別，則傳回 NULL。|  
|numeric\_precision|Byte|概略數值資料、精確數值資料、整數資料或貨幣資料的精確度。  否則，傳回 NULL。|  
|numeric\_precision\_radix|Int16|概略數值資料、精確數值資料、整數資料或貨幣資料的精確度基數。  否則，傳回 NULL。|  
|numeric\_scale|Int32|概略數值資料、精確數值資料、整數資料或貨幣資料的小數位數。  否則，傳回 NULL。|  
|datetime\_precision|Int16|若參數型別為 datetime 或 smalldatetime，則為以分數秒為單位的精確度。  否則，傳回 NULL。|  
|interval\_type|String|NULL。  保留供 SQL Server 日後使用。|  
|interval\_precision|Int16|NULL。  保留供 SQL Server 日後使用。|  
  
## 資料表  
  
|ColumnName|DataType|描述|  
|----------------|--------------|--------|  
|table\_catalog|String|資料表的目錄。|  
|table\_schema|String|包含資料表的結構描述。|  
|table\_name|String|資料表名稱。|  
|table\_type|String|資料表型別。  可為 VIEW 或 BASE TABLE。|  
  
## 資料行  
  
|ColumnName|DataType|描述|  
|----------------|--------------|--------|  
|table\_catalog|String|資料表的目錄。|  
|table\_schema|String|包含資料表的結構描述。|  
|table\_name|String|資料表名稱。|  
|column\_name|String|資料行名稱。|  
|ordinal\_position|Int16|資料行識別碼。|  
|column\_default|String|資料行的預設值。|  
|is\_nullable|String|資料行的 Null 屬性。  若此資料行允許 NULL，其會傳回 YES。  否則，傳回 NO。|  
|data\_type|String|系統提供的資料型別。|  
|character\_maximum\_length|Int32 – Sql8, Int16 – Sql7|二進位資料、字元資料或文字及影像資料的長度上限 \(以字元數為單位\)。  否則，傳回 NULL。|  
|character\_octet\_length|Int32 – SQL8, Int16 – Sql7|二進位資料、字元資料或文件及影像資料的長度上限 \(以位元組為單位\)。  否則，傳回 NULL。|  
|numeric\_precision|Unsigned Byte|概略數值資料、精確數值資料、整數資料或貨幣資料的精確度。  否則，傳回 NULL。|  
|numeric\_precision\_radix|Int16|概略數值資料、精確數值資料、整數資料或貨幣資料的精確度基數。  否則，傳回 NULL。|  
|numeric\_scale|Int32|概略數值資料、精確數值資料、整數資料或貨幣資料的小數位數。  否則，傳回 NULL。|  
|datetime\_precision|Int16|datetime 及 SQL\-92 間隔資料型別的子型別程式碼。  若為其他資料型別，則傳回 NULL。|  
|character\_set\_catalog|String|若資料行為字元資料或文字資料型別，則傳回 master，表示字元集所在的資料庫。  否則，傳回 NULL。|  
|character\_set\_schema|String|永遠傳回 NULL。|  
|character\_set\_name|String|若此資料行為字元資料或文字資料型別，則傳回字元集的唯一名稱。  否則，傳回 NULL。|  
|collation\_catalog|String|若資料行為字元資料或文字資料型別，則傳回 master，表示定義定序的資料庫。  否則，此資料行為 UNLL。|  
  
### Columns \(SQL Server 2008\)  
 從 .NET Framework 3.5 版 SP1 和 SQL Server 2008 開始，下列資料行就已經加入至 Columns 結構描述集合，以便支援新的空間類型、Filestream 和疏鬆資料行。  舊版 .NET Framework 和 SQL Server 不支援這些資料行。  
  
|ColumnName|DataType|描述|  
|----------------|--------------|--------|  
|IS\_FILESTREAM|String|YES \(如果資料行具有 FILESTREAM 屬性\)。<br /><br /> NO \(如果資料行沒有 FILESTREAM 屬性\)。|  
|IS\_SPARSE|String|YES \(如果資料行是疏鬆資料行\)。<br /><br /> NO \(如果資料行不是疏鬆資料行\)。|  
|IS\_COLUMN\_SET|String|YES \(如果資料行是資料行集資料行\)。<br /><br /> NO \(如果資料行不是資料行集資料行\)。|  
  
### AllColumns \(SQL Server 2008\)  
 從 .NET Framework 3.5 版 SP1 和 SQL Server 2008 開始，就已經加入 AllColumns 結構描述集合，以便支援疏鬆資料行。  舊版 .NET Framework 和 SQL Server 不支援 AllColumns。  
  
 AllColumns 與 Columns 結構描述集合具有相同的限制和產生的 DataTable 結構描述。  唯一的差異是 AllColumns 包含了 Columns 結構描述集合並未包含的資料行集資料行。  下表將描述這些資料行。  
  
|ColumnName|DataType|描述|  
|----------------|--------------|--------|  
|table\_catalog|String|資料表的目錄。|  
|table\_schema|String|包含資料表的結構描述。|  
|table\_name|String|資料表名稱。|  
|column\_name|String|資料行名稱。|  
|ordinal\_position|Int16|資料行識別碼。|  
|column\_default|String|資料行的預設值。|  
|is\_nullable|String|資料行的 Null 屬性。  若此資料行允許 NULL，其會傳回 YES。  否則，會傳回 NO。|  
|data\_type|String|系統提供的資料型別。|  
|character\_maximum\_length|Int32|二進位資料、字元資料或文字及影像資料的長度上限 \(以字元數為單位\)。  否則，傳回 NULL。|  
|character\_octet\_length|Int32|二進位資料、字元資料或文件及影像資料的長度上限 \(以位元組為單位\)。  否則，傳回 NULL。|  
|numeric\_precision|Unsigned Byte|概略數值資料、精確數值資料、整數資料或貨幣資料的精確度。  否則，傳回 NULL。|  
|numeric\_precision\_radix|Int16|概略數值資料、精確數值資料、整數資料或貨幣資料的精確度基數。  否則，傳回 NULL。|  
|numeric\_scale|Int32|概略數值資料、精確數值資料、整數資料或貨幣資料的小數位數。  否則，傳回 NULL。|  
|datetime\_precision|Int16|datetime 及 SQL\-92 間隔資料型別的子型別程式碼。  若為其他資料型別，則傳回 NULL。|  
|character\_set\_catalog|String|若資料行為字元資料或文字資料型別，則傳回 master，表示字元集所在的資料庫。  否則，傳回 NULL。|  
|character\_set\_schema|String|永遠傳回 NULL。|  
|character\_set\_name|String|若此資料行為字元資料或文字資料型別，則傳回字元集的唯一名稱。  否則，傳回 NULL。|  
|collation\_catalog|String|若資料行為字元資料或文字資料型別，則傳回 master，表示定義定序的資料庫。  否則，此資料行為 UNLL。|  
|IS\_FILESTREAM|String|YES \(如果資料行具有 FILESTREAM 屬性\)。<br /><br /> NO \(如果資料行沒有 FILESTREAM 屬性\)。|  
|IS\_SPARSE|String|YES \(如果資料行是疏鬆資料行\)。<br /><br /> NO \(如果資料行不是疏鬆資料行\)。|  
|IS\_COLUMN\_SET|String|YES \(如果資料行是資料行集資料行\)。<br /><br /> NO \(如果資料行不是資料行集資料行\)。|  
  
### ColumnSetColumns \(SQL Server 2008\)  
 從 .NET Framework 3.5 版 SP1 和 SQL Server 2008 開始，就已經加入 ColumnSetColumns 結構描述集合，以便支援疏鬆資料行。  舊版 .NET Framework 和 SQL Server 不支援 ColumnSetColumns。  ColumnSetColumns 結構描述集合會針對資料行集中的所有資料行傳回結構描述。  下表將描述這些資料行。  
  
|ColumnName|DataType|描述|  
|----------------|--------------|--------|  
|table\_catalog|String|資料表的目錄。|  
|table\_schema|String|包含資料表的結構描述。|  
|table\_name|String|資料表名稱。|  
|column\_name|String|資料行名稱。|  
|ordinal\_position|Int16|資料行識別碼。|  
|column\_default|String|資料行的預設值。|  
|is\_nullable|String|資料行的 Null 屬性。  若此資料行允許 NULL，其會傳回 YES。  否則，會傳回 NO。|  
|data\_type|String|系統提供的資料型別。|  
|character\_maximum\_length|Int32|二進位資料、字元資料或文字及影像資料的長度上限 \(以字元數為單位\)。  否則，傳回 NULL。|  
|character\_octet\_length|Int32|二進位資料、字元資料或文件及影像資料的長度上限 \(以位元組為單位\)。  否則，傳回 NULL。|  
|numeric\_precision|Unsigned Byte|概略數值資料、精確數值資料、整數資料或貨幣資料的精確度。  否則，傳回 NULL。|  
|numeric\_precision\_radix|Int16|概略數值資料、精確數值資料、整數資料或貨幣資料的精確度基數。  否則，傳回 NULL。|  
|numeric\_scale|Int32|概略數值資料、精確數值資料、整數資料或貨幣資料的小數位數。  否則，傳回 NULL。|  
|datetime\_precision|Int16|datetime 及 SQL\-92 間隔資料型別的子型別程式碼。  若為其他資料型別，則傳回 NULL。|  
|character\_set\_catalog|String|若資料行為字元資料或文字資料型別，則傳回 master，表示字元集所在的資料庫。  否則，傳回 NULL。|  
|character\_set\_schema|String|永遠傳回 NULL。|  
|character\_set\_name|String|若此資料行為字元資料或文字資料型別，則傳回字元集的唯一名稱。  否則，傳回 NULL。|  
|collation\_catalog|String|若資料行為字元資料或文字資料型別，則傳回 master，表示定義定序的資料庫。  否則，此資料行為 UNLL。|  
|IS\_FILESTREAM|String|YES \(如果資料行具有 FILESTREAM 屬性\)。<br /><br /> NO \(如果資料行沒有 FILESTREAM 屬性\)。|  
|IS\_SPARSE|String|YES \(如果資料行是疏鬆資料行\)。<br /><br /> NO \(如果資料行不是疏鬆資料行\)。|  
|IS\_COLUMN\_SET|String|YES \(如果資料行是資料行集資料行\)。<br /><br /> NO \(如果資料行不是資料行集資料行\)。|  
  
## 使用者  
  
|ColumnName|DataType|描述|  
|----------------|--------------|--------|  
|uid|Int16|使用者 ID，在此資料庫中是唯一的。  1 是資料庫擁有人。|  
|name|String|使用者名稱或群組名稱，在此資料庫中是唯一的。|  
|createdate|DateTime|加入帳戶的日期。|  
|updatedate|DateTime|上次變更帳戶的日期。|  
  
## 檢視  
  
|ColumnName|DataType|描述|  
|----------------|--------------|--------|  
|table\_catalog|String|檢視表的目錄。|  
|table\_schema|String|包含檢視表的結構描述。|  
|table\_name|String|檢視表名稱。|  
|check\_option|String|WITH CHECK OPTION 的型別。  若原始檢視表是使用 WITH CHECK OPTION 所建立的，則為 CASCADE。  否則，傳回 NONE。|  
|is\_updatable|String|指定檢視表是否可以更新。  永遠傳回 NO。|  
  
## ViewColumns  
  
|ColumnName|DataType|描述|  
|----------------|--------------|--------|  
|view\_catalog|String|檢視表的目錄。|  
|view\_schema|String|包含檢視表的結構描述。|  
|view\_name|String|檢視表名稱。|  
|table\_catalog|String|與此檢視表相關之資料表的目錄。|  
|table\_schema|String|包含與此檢視表相關之資料表的結構描述。|  
|table\_name|String|與檢視表相關之資料表的名稱。  基底資料表。|  
|column\_name|String|資料行名稱。|  
  
## UserDefinedTypes  
  
|ColumnName|DataType|描述|  
|----------------|--------------|--------|  
|assembly\_name|String|組件檔案的名稱。|  
|UDT\_name|String|組件的類別名稱。|  
|version\_major|物件|主要版本號碼。|  
|version\_minor|物件|次要版本號碼。|  
|version\_build|物件|組建編號。|  
|version\_revision|物件|修訂編號。|  
|Culture\_info|物件|與此 UDT 相關的文化特性資訊。|  
|Public\_key|物件|此組件使用的公開金鑰。|  
|Is\_fixed\_length|Boolean|指定型別的長度是否永遠與 max\_length 相同。|  
|max\_length|Int16|型別的最大長度 \(以位元組為單位\)。|  
|permission\_set\_desc|String|組件使用權限集合\/安全性層級的易記名稱。|  
|create\_date|DateTime|建立\/登錄組件的日期。|  
  
## 請參閱  
 [擷取資料庫結構描述資訊](../../../../docs/framework/data/adonet/retrieving-database-schema-information.md)   
 [ADO.NET Managed 提供者和資料集開發人員中心](http://go.microsoft.com/fwlink/?LinkId=217917)