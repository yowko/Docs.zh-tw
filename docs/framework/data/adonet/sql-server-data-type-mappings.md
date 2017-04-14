---
title: "SQL Server 資料型別對應 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: fafdc31a-f435-4cd3-883f-1dfadd971277
caps.latest.revision: 8
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 8
---
# SQL Server 資料型別對應
SQL Server 和 .NET Framework 是以不同的型別系統為基礎。  例如，.NET Framework <xref:System.Decimal> 結構的最大小數點位數為 28，而 SQL Server decimal 和 numeric 資料型別的最大小數點位數為 38。  為了在讀取和寫入資料時維持資料完整性，<xref:System.Data.SqlClient.SqlDataReader> 會公開 \(Expose\) SQL Server 特有的具型別存取子方法 \(可傳回 <xref:System.Data.SqlTypes> 的物件\) 以及存取子方法 \(可傳回 .NET Framework 型別\)。  SQL Server 型別和 .NET Framework 型別也會由 <xref:System.Data.DbType> 和 <xref:System.Data.SqlDbType> 類別 \(Class\) 中的列舉型別 \(Enumeration\) 表示，而且您可以在指定 <xref:System.Data.SqlClient.SqlParameter> 資料型別時使用這些類別。  
  
 下表將顯示推斷的 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 型別、<xref:System.Data.DbType> 和 <xref:System.Data.SqlDbType> 列舉型別，以及 <xref:System.Data.SqlClient.SqlDataReader> 的存取子方法。  
  
|SQL Server Database Engine 型別|.NET Framework 類型|SqlDbType 列舉型別|SqlDataReader SqlTypes 具型別的存取子|DbType 列舉型別|SqlDataReader DbType 具型別的存取子|  
|-----------------------------------|-----------------------|--------------------|------------------------------------|-----------------|----------------------------------|  
|bigint|Int64|<xref:System.Data.SqlDbType>|<xref:System.Data.SqlClient.SqlDataReader.GetSqlInt64%2A>|<xref:System.Data.DbType>|<xref:System.Data.SqlClient.SqlDataReader.GetInt64%2A>|  
|二進位|Byte\[\]|<xref:System.Data.SqlDbType>|<xref:System.Data.SqlClient.SqlDataReader.GetSqlBinary%2A>|<xref:System.Data.DbType>|<xref:System.Data.SqlClient.SqlDataReader.GetBytes%2A>|  
|位元|Boolean|<xref:System.Data.SqlDbType>|<xref:System.Data.SqlClient.SqlDataReader.GetSqlBoolean%2A>|<xref:System.Data.DbType>|<xref:System.Data.SqlClient.SqlDataReader.GetBoolean%2A>|  
|char|String<br /><br /> Char\[\]|<xref:System.Data.SqlDbType>|<xref:System.Data.SqlClient.SqlDataReader.GetSqlString%2A>|<xref:System.Data.DbType>,<br /><br /> <xref:System.Data.DbType>|<xref:System.Data.SqlClient.SqlDataReader.GetString%2A><br /><br /> <xref:System.Data.SqlClient.SqlDataReader.GetChars%2A>|  
|date<br /><br /> \(SQL Server 2008 及以後版本\)|DateTime|<xref:System.Data.SqlDbType>|<xref:System.Data.SqlClient.SqlDataReader.GetSqlDateTime%2A>|<xref:System.Data.DbType>|<xref:System.Data.SqlClient.SqlDataReader.GetDateTime%2A>|  
|datetime|DateTime|<xref:System.Data.SqlDbType>|<xref:System.Data.SqlClient.SqlDataReader.GetSqlDateTime%2A>|<xref:System.Data.DbType>|<xref:System.Data.SqlClient.SqlDataReader.GetDateTime%2A>|  
|datetime2<br /><br /> \(SQL Server 2008 及以後版本\)|DateTime|<xref:System.Data.SqlDbType>|無|<xref:System.Data.DbType>|<xref:System.Data.SqlClient.SqlDataReader.GetDateTime%2A>|  
|datetimeoffset<br /><br /> \(SQL Server 2008 及以後版本\)|DateTimeOffset|<xref:System.Data.SqlDbType>|無|<xref:System.Data.DbType>|<xref:System.Data.SqlClient.SqlDataReader.GetDateTimeOffset%2A>|  
|decimal|Decimal|<xref:System.Data.SqlDbType>|<xref:System.Data.SqlClient.SqlDataReader.GetSqlDecimal%2A>|<xref:System.Data.DbType>|<xref:System.Data.SqlClient.SqlDataReader.GetDecimal%2A>|  
|FILESTREAM 屬性 varbinary\(max\)|Byte\[\]|<xref:System.Data.SqlDbType>|<xref:System.Data.SqlClient.SqlDataReader.GetSqlBytes%2A>|<xref:System.Data.DbType>|<xref:System.Data.SqlClient.SqlDataReader.GetBytes%2A>|  
|float|Double|<xref:System.Data.SqlDbType>|<xref:System.Data.SqlClient.SqlDataReader.GetSqlDouble%2A>|<xref:System.Data.DbType>|<xref:System.Data.SqlClient.SqlDataReader.GetDouble%2A>|  
|影像|Byte\[\]|<xref:System.Data.SqlDbType>|<xref:System.Data.SqlClient.SqlDataReader.GetSqlBinary%2A>|<xref:System.Data.DbType>|<xref:System.Data.SqlClient.SqlDataReader.GetBytes%2A>|  
|int|Int32|<xref:System.Data.SqlDbType>|<xref:System.Data.SqlClient.SqlDataReader.GetSqlInt32%2A>|<xref:System.Data.DbType>|<xref:System.Data.SqlClient.SqlDataReader.GetInt32%2A>|  
|現金|Decimal|<xref:System.Data.SqlDbType>|<xref:System.Data.SqlClient.SqlDataReader.GetSqlMoney%2A>|<xref:System.Data.DbType>|<xref:System.Data.SqlClient.SqlDataReader.GetDecimal%2A>|  
|nchar|String<br /><br /> Char\[\]|<xref:System.Data.SqlDbType>|<xref:System.Data.SqlClient.SqlDataReader.GetSqlString%2A>|<xref:System.Data.DbType>|<xref:System.Data.SqlClient.SqlDataReader.GetString%2A><br /><br /> <xref:System.Data.SqlClient.SqlDataReader.GetChars%2A>|  
|ntext|String<br /><br /> Char\[\]|<xref:System.Data.SqlDbType>|<xref:System.Data.SqlClient.SqlDataReader.GetSqlString%2A>|<xref:System.Data.DbType>|<xref:System.Data.SqlClient.SqlDataReader.GetString%2A><br /><br /> <xref:System.Data.SqlClient.SqlDataReader.GetChars%2A>|  
|數值|Decimal|<xref:System.Data.SqlDbType>|<xref:System.Data.SqlClient.SqlDataReader.GetSqlDecimal%2A>|<xref:System.Data.DbType>|<xref:System.Data.SqlClient.SqlDataReader.GetDecimal%2A>|  
|nvarchar|String<br /><br /> Char\[\]|<xref:System.Data.SqlDbType>|<xref:System.Data.SqlClient.SqlDataReader.GetSqlString%2A>|<xref:System.Data.DbType>|<xref:System.Data.SqlClient.SqlDataReader.GetString%2A><br /><br /> <xref:System.Data.SqlClient.SqlDataReader.GetChars%2A>|  
|實數|Single|<xref:System.Data.SqlDbType>|<xref:System.Data.SqlClient.SqlDataReader.GetSqlSingle%2A>|<xref:System.Data.DbType>|<xref:System.Data.SqlClient.SqlDataReader.GetFloat%2A>|  
|rowversion|Byte\[\]|<xref:System.Data.SqlDbType>|<xref:System.Data.SqlClient.SqlDataReader.GetSqlBinary%2A>|<xref:System.Data.DbType>|<xref:System.Data.SqlClient.SqlDataReader.GetBytes%2A>|  
|smalldatetime|DateTime|<xref:System.Data.SqlDbType>|<xref:System.Data.SqlClient.SqlDataReader.GetSqlDateTime%2A>|<xref:System.Data.DbType>|<xref:System.Data.SqlClient.SqlDataReader.GetDateTime%2A>|  
|smallint|Int16|<xref:System.Data.SqlDbType>|<xref:System.Data.SqlClient.SqlDataReader.GetSqlInt16%2A>|<xref:System.Data.DbType>|<xref:System.Data.SqlClient.SqlDataReader.GetInt16%2A>|  
|smallmoney|Decimal|<xref:System.Data.SqlDbType>|<xref:System.Data.SqlClient.SqlDataReader.GetSqlMoney%2A>|<xref:System.Data.DbType>|<xref:System.Data.SqlClient.SqlDataReader.GetDecimal%2A>|  
|sql\_variant|Object\*|<xref:System.Data.SqlDbType>|<xref:System.Data.SqlClient.SqlDataReader.GetSqlValue%2A> \*|<xref:System.Data.DbType>|<xref:System.Data.SqlClient.SqlDataReader.GetValue%2A> \*|  
|文字|String<br /><br /> Char\[\]|<xref:System.Data.SqlDbType>|<xref:System.Data.SqlClient.SqlDataReader.GetSqlString%2A>|<xref:System.Data.DbType>|<xref:System.Data.SqlClient.SqlDataReader.GetString%2A><br /><br /> <xref:System.Data.SqlClient.SqlDataReader.GetChars%2A>|  
|時間<br /><br /> \(SQL Server 2008 及以後版本\)|TimeSpan|<xref:System.Data.SqlDbType>|無|<xref:System.Data.DbType>|<xref:System.Data.SqlClient.SqlDataReader.GetDateTime%2A>|  
|時間戳記|Byte\[\]|<xref:System.Data.SqlDbType>|<xref:System.Data.SqlClient.SqlDataReader.GetSqlBinary%2A>|<xref:System.Data.DbType>|<xref:System.Data.SqlClient.SqlDataReader.GetBytes%2A>|  
|tinyint|Byte|<xref:System.Data.SqlDbType>|<xref:System.Data.SqlClient.SqlDataReader.GetSqlByte%2A>|<xref:System.Data.DbType>|<xref:System.Data.SqlClient.SqlDataReader.GetByte%2A>|  
|uniqueidentifier|Guid|<xref:System.Data.SqlDbType>|<xref:System.Data.SqlClient.SqlDataReader.GetSqlGuid%2A>|<xref:System.Data.DbType>|<xref:System.Data.SqlClient.SqlDataReader.GetGuid%2A>|  
|varbinary|Byte\[\]|<xref:System.Data.SqlDbType>|<xref:System.Data.SqlClient.SqlDataReader.GetSqlBinary%2A>|<xref:System.Data.DbType>|<xref:System.Data.SqlClient.SqlDataReader.GetBytes%2A>|  
|varchar|String<br /><br /> Char\[\]|<xref:System.Data.SqlDbType>|<xref:System.Data.SqlClient.SqlDataReader.GetSqlString%2A>|<xref:System.Data.DbType>, <xref:System.Data.DbType>|<xref:System.Data.SqlClient.SqlDataReader.GetString%2A><br /><br /> <xref:System.Data.SqlClient.SqlDataReader.GetChars%2A>|  
|xml|Xml|<xref:System.Data.SqlDbType>|<xref:System.Data.SqlClient.SqlDataReader.GetSqlXml%2A>|<xref:System.Data.DbType>|無|  
  
 \* 如果您知道 `sql_variant` 的基礎型別，請使用特定具型別的存取子。  
  
## [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)] 線上叢書參考  
 如需 [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)] 資料類型的詳細資訊，請參閱[資料類型 \(Database Engine\)](http://go.microsoft.com/fwlink/?LinkID=107468)。  
  
## 請參閱  
 [SQL Server 資料型別和 ADO.NET](../../../../docs/framework/data/adonet/sql/sql-server-data-types.md)   
 [SQL Server 二進位和大數值資料](../../../../docs/framework/data/adonet/sql/sql-server-binary-and-large-value-data.md)   
 [ADO.NET 中的資料型別對應](../../../../docs/framework/data/adonet/data-type-mappings-in-ado-net.md)   
 [設定參數和參數資料類型](../../../../docs/framework/data/adonet/configuring-parameters-and-parameter-data-types.md)   
 [ADO.NET Managed 提供者和資料集開發人員中心](http://go.microsoft.com/fwlink/?LinkId=217917)