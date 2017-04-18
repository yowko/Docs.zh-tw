---
title: "ODBC 結構描述集合 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1bb126a5-ceec-4649-a4bc-8aa19e801046
caps.latest.revision: 3
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 3
---
# ODBC 結構描述集合
本節將討論 Microsoft SQL Server、Oracle 和 Microsoft Jet 之 ODBC 驅動程式的結構描述集合支援。  
  
## Microsoft SQL Server ODBC 驅動程式  
 除了通用結構描述集合之外，Microsoft SQL Server ODBC 驅動程式還支援下列特定的結構描述集合：  
  
-   資料表  
  
-   Indexes  
  
-   資料行  
  
-   程序  
  
-   ProcedureColumns  
  
-   ProcedureParameters  
  
-   檢視  
  
### Tables 與 Views  
  
|ColumnName|DataType|  
|----------------|--------------|  
|TABLE\_CAT|String|  
|TABLE\_SCHEM|String|  
|TABLE\_NAME|String|  
|TABLE\_TYPE|String|  
|REMARKS|String|  
  
### Indexes  
  
|ColumnName|DataType|  
|----------------|--------------|  
|TABLE\_CAT|String|  
|TABLE\_SCHEM|String|  
|TABLE\_NAME|String|  
|NON\_UNIQUE|Int16|  
|INDEX\_QUALIFIER|String|  
|INDEX\_NAME|String|  
|TYPE|Int16|  
|ORDINAL\_POSITION|Int16|  
|COLUMN\_NAME|String|  
|ASC\_OR\_DESC|String|  
|CARDINATLITY|Int32|  
|PAGES|Int32|  
|FILTER\_CONDITION|String|  
|SS\_TYPE\_SCHEMA|String|  
|SS\_DATA\_TYPE|Byte|  
  
### 資料行  
  
|ColumnName|DataType|  
|----------------|--------------|  
|TABLE\_CAT|String|  
|TABLE\_SCHEM|String|  
|TABLE\_NAME|String|  
|COLUMN\_NAME|String|  
|DATA\_TYPE|Int16|  
|TYPE\_NAME|String|  
|COLUMN\_SIZE|Int32|  
|BUFFER\_LENGTH|Int32|  
|DECIMAL\_DIGITS|Int16|  
|NUM\_PREC\_RADIX|Int16|  
|NULLABLE|Int16|  
|REMARKS|String|  
|COLUMN\_DEF|String|  
|SQL\_DATA\_TYPE|Int16|  
|SQL\_DATETIME\_SUB|Int16|  
|CHAR\_OCTET\_LENGTH|Int32|  
|ORDINAL\_POSITION|Int32|  
|IS\_NULLABLE|String|  
|SS\_TYPE\_CATALOG|String|  
|SS\_TYPE\_SCHEMA|String|  
|SS\_DATA\_TYPE|Byte|  
  
### 程序  
  
|ColumnName|DataType|  
|----------------|--------------|  
|PROCEDURE\_CAT|String|  
|PROCEDURE\_SCHEM|String|  
|PROCEDURE\_NAME|String|  
|NUM\_INPUT\_PARAMS|Int32|  
|NUM\_OUTPUT\_PARAMS|Int32|  
|NUM\_RESULT\_SETS|Int32|  
|REMARKS|String|  
|PROCEDURE\_TYPE|Int16|  
  
### ProcedureColumns  
  
|ColumnName|DataType|  
|----------------|--------------|  
|PROCEDURE\_CAT|String|  
|PROCEDURE\_SCHEM|String|  
|PROCEDURE\_NAME|String|  
|COLUMN\_NAME|String|  
|COLUMN\_TYPE|Int16|  
|DATA\_TYPE|Int16|  
|TYPE\_NAME|String|  
|COLUMN\_SIZE|Int32|  
|BUFFER\_LENGTH|Int32|  
|DECIMAL\_DIGITS|Int16|  
|NUM\_PREC\_RADIX|Int16|  
|NULLABLE|Int16|  
|REMARKS|String|  
|COLUMN\_DEF|String|  
|SQL\_DATA\_TYPE|Int16|  
|SQL\_DATETIME\_SUB|Int16|  
|CHAR\_OCTET\_LENGTH|Int32|  
|ORDINAL\_POSITION|Int32|  
|IS\_NULLABLE|String|  
|SS\_TYPE\_CATALOG|String|  
|SS\_TYPE\_SCHEMA|String|  
|SS\_DATA\_TYPE|Byte|  
  
### ProcedureParameters  
  
|ColumnName|DataType|  
|----------------|--------------|  
|PROCEDURE\_CAT|String|  
|PROCEDURE\_SCHEM|String|  
|PROCEDURE\_NAME|String|  
|COLUMN\_NAME|String|  
|COLUMN\_TYPE|Int16|  
|DATA\_TYPE|Int16|  
|TYPE\_NAME|String|  
|COLUMN\_SIZE|Int32|  
|BUFFER\_LENGTH|Int32|  
|DECIMAL\_DIGITS|Int16|  
|NUM\_PREC\_RADIX|Int16|  
|NULLABLE|Int16|  
|REMARKS|String|  
|COLUMN\_DEF|String|  
|SQL\_DATA\_TYPE|Int16|  
|SQL\_DATETIME\_SUB|Int16|  
|CHAR\_OCTET\_LENGTH|Int32|  
|ORDINAL\_POSITION|Int32|  
|IS\_NULLABLE|String|  
|SS\_TYPE\_CATALOG|String|  
|SS\_TYPE\_SCHEMA|String|  
|SS\_DATA\_TYPE|Byte|  
  
## Microsoft Oracle ODBC 驅動程式  
 除了通用結構描述集合之外，Microsoft SQL Server Oracle ODBC 驅動程式還支援下列特定結構描述集合：  
  
-   資料表  
  
-   資料行  
  
-   程序  
  
-   ProcedureColumns  
  
-   ProcedureParameters  
  
-   檢視  
  
-   Indexes  
  
### Tables 與 Views  
  
|ColumnName|DataType|  
|----------------|--------------|  
|TABLE\_QUALIFIER|String|  
|TABLE\_OWNER|String|  
|TABLE\_NAME|String|  
|TABLE\_TYPE|String|  
|REMARKS|String|  
  
### 資料行  
  
|ColumnName|DataType|  
|----------------|--------------|  
|TABLE\_QUALIFIER|String|  
|TABLE\_OWNER|String|  
|TABLE\_NAME|String|  
|COLUMN\_NAME|String|  
|DATA\_TYPE|Int16|  
|TYPE\_NAME|String|  
|PRECISION|Int32|  
|LENGTH|Int32|  
|SCALE|Int16|  
|RADIX|Int16|  
|NULLABLE|Int16|  
|REMARKS|String|  
|ORDINAL\_POSITION|Int32|  
  
### 程序  
  
|ColumnName|DataType|  
|----------------|--------------|  
|PROCEDURE\_QUALIFIER|String|  
|PROCEDURE\_OWNER|String|  
|PROCEDURE\_NAME|String|  
|NUM\_INPUT\_PARAMS|Int16|  
|NUM\_OUTPUT\_PARAMS|Int16|  
|NUM\_RESULT\_SETS|Int16|  
|REMARKS|String|  
|PROCEDURE\_TYPE|Int16|  
  
### ProcedureColumns  
  
|ColumnName|DataType|  
|----------------|--------------|  
|PROCEDURE\_QUALIFIER|String|  
|PROCEDURE\_OWNER|String|  
|PROCEDURE\_NAME|String|  
|COLUMN\_NAME|String|  
|COLUMN\_TYPE|Int16|  
|DATA\_TYPE|Int16|  
|TYPE\_NAME|String|  
|PRECISION|Int32|  
|LENGTH|Int32|  
|SCALE|Int16|  
|RADIX|Int16|  
|NULLABLE|Int16|  
|REMARKS|String|  
|OVERLOAD|Int32|  
|ORDINAL\_POSITION|Int32|  
  
## Microsoft Jet ODBC 驅動程式  
 除了通用結構描述集合之外，Microsoft Jet ODBC 驅動程式還支援下列特定的結構描述集合：  
  
-   資料表  
  
-   Indexes  
  
-   資料行  
  
-   程序  
  
-   ProcedureColumns  
  
-   ProcedureParameters  
  
-   檢視  
  
### Tables 與 Views  
  
|ColumnName|DataType|  
|----------------|--------------|  
|TABLE\_QUALIFIER|String|  
|TABLE\_OWNER|String|  
|TABLE\_NAME|String|  
|TABLE\_TYPE|String|  
|REMARKS|String|  
  
### 資料行  
  
|ColumnName|DataType|  
|----------------|--------------|  
|TABLE\_QUALIFIER|String|  
|TABLE\_OWNER|String|  
|TABLE\_NAME|String|  
|COLUMN\_NAME|String|  
|DATA\_TYPE|Int16|  
|TYPE\_NAME|String|  
|PRECISION|Int32|  
|LENGTH|Int32|  
|SCALE|Int16|  
|RADIX|Int16|  
|NULLABLE|Int16|  
|REMARKS|String|  
|ORDINAL\_POSITION|Int32|  
  
### 程序  
  
|ColumnName|DataType|  
|----------------|--------------|  
|PROCEDURE\_QUALIFIER|String|  
|PROCEDURE\_OWNER|String|  
|PROCEDURE\_NAME|String|  
|NUM\_INPUT\_PARAMS|Int16|  
|NUM\_OUTPUT\_PARAMS|Int16|  
|NUM\_RESULT\_SETS|Int16|  
|REMARKS|String|  
|PROCEDURE\_TYPE|Int16|  
  
### ProcedureColumns  
  
|ColumnName|DataType|  
|----------------|--------------|  
|PROCEDURE\_QUALIFIER|String|  
|PROCEDURE\_OWNER|String|  
|PROCEDURE\_NAME|String|  
|COLUMN\_NAME|String|  
|COLUMN\_TYPE|Int16|  
|DATA\_TYPE|Int16|  
|TYPE\_NAME|String|  
|PRECISION|Int32|  
|LENGTH|Int32|  
|SCALE|Int16|  
|RADIX|Int16|  
|NULLABLE|Int16|  
|REMARKS|String|  
|OVERLOAD|Int32|  
|ORDINAL\_POSITION|Int32|  
  
### ProcedureParameters  
  
|ColumnName|DataType|  
|----------------|--------------|  
|PROCEDURE\_CAT|String|  
|PROCEDURE\_SCHEM|String|  
|PROCEDURE\_NAME|String|  
|COLUMN\_NAME|String|  
|COLUMN\_TYPE|Int16|  
|DATA\_TYPE|Int16|  
|TYPE\_NAME|String|  
|COLUMN\_SIZE|Int32|  
|BUFFER\_LENGTH|Int32|  
|DECIMAL\_DIGITS|Int16|  
|NUM\_PREC\_RADIX|Int16|  
|NULLABLE|Int16|  
|REMARKS|String|  
|COLUMN\_DEF|String|  
|SQL\_DATA\_TYPE|Int16|  
|SQL\_DATETIME\_SUB|Int16|  
|CHAR\_OCTET\_LENGTH|Int32|  
|ORDINAL\_POSITION|Int32|  
|IS\_NULLABLE|String|  
  
## 請參閱  
 [ADO.NET Managed 提供者和資料集開發人員中心](http://go.microsoft.com/fwlink/?LinkId=217917)