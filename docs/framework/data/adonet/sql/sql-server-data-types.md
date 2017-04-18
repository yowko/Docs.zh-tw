---
title: "SQL Server 資料型別和 ADO.NET | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 81b43550-23e8-43bb-b460-7eb8ac825c33
caps.latest.revision: 6
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 6
---
# SQL Server 資料型別和 ADO.NET
SQL Server 和 .NET Framework 是以不同的型別系統為基礎，而且可能會導致資料遺失。  為了保留資料完整性，.NET Framework Data Provider for SQL Server \(<xref:System.Data.SqlClient>\) 針對使用 SQL Server 資料提供了具型別的存取子方法。  您可以使用 <xref:System.Data.SqlDbType> 類別 \(Class\) 中的列舉型別 \(Enumeration\) 來指定 <xref:System.Data.SqlClient.SqlParameter> 資料型別。  
  
 如需詳細資訊以及描述 SQL Server 與 .NET Framework 資料型別之間資料型別對應的表格，請參閱 [SQL Server 資料型別對應](../../../../../docs/framework/data/adonet/sql-server-data-type-mappings.md)。  
  
 SQL Server 2008 導入了一些設計成符合商務需求的新資料型別，以便使用日期和時間、結構化、半結構化和非結構化資料。  這些資料型別列於《SQL Server 2008 線上叢書》中。  
  
 可用於應用程式中的 SQL Server 資料型別取決於您所使用的 SQL Server 版本。  如需詳細資訊，請參閱下表中的相關《SQL Server 線上叢書》版本。  
  
 **SQL Server 線上叢書**  
  
1.  [資料類型 \(Database Engine\)](http://go.microsoft.com/fwlink/?LinkID=107468)  
  
## 在本節中  
 [SqlType 和 DataSet](../../../../../docs/framework/data/adonet/sql/sqltypes-and-the-dataset.md)  
 說明針對 `DataSet` 中的 `SqlTypes` 所提供的型別支援。  
  
 [處理 Null 值](../../../../../docs/framework/data/adonet/sql/handling-null-values.md)  
 示範如何使用 Null 值和三種值的邏輯。  
  
 [比較 GUID 及 uniqueidentifier 值](../../../../../docs/framework/data/adonet/sql/comparing-guid-and-uniqueidentifier-values.md)  
 示範如何在 SQL Server 和 .NET Framework 中使用 GUID 和 uniqueidentifier 值。  
  
 [日期和時間資料](../../../../../docs/framework/data/adonet/sql/date-and-time-data.md)  
 說明如何使用 SQL Server 2008 所導入的新日期和時間資料型別。  
  
 [大型 UDT](../../../../../docs/framework/data/adonet/sql/large-udts.md)  
 示範如何從 SQL Server 2008 所導入的大數值 UDT 中擷取資料。  
  
 [SQL Server 中的 XML 資料](../../../../../docs/framework/data/adonet/sql/xml-data-in-sql-server.md)  
 說明如何使用從 SQL Server 擷取的 XML 資料。  
  
## 參考  
 <xref:System.Data.DataSet>  
 說明 `DataSet` 類別及其所有成員。  
  
 <xref:System.Data.SqlTypes>  
 說明 `SqlTypes` 命名空間 \(Namespace\) 及其所有成員。  
  
 <xref:System.Data.SqlDbType>  
 說明 `SqlDbType` 列舉型別及其所有成員。  
  
 <xref:System.Data.DbType>  
 說明 `DbType` 列舉型別及其所有成員。  
  
## 請參閱  
 [SQL Server 資料型別對應](../../../../../docs/framework/data/adonet/sql-server-data-type-mappings.md)   
 [設定參數和參數資料類型](../../../../../docs/framework/data/adonet/configuring-parameters-and-parameter-data-types.md)   
 [資料表值參數](../../../../../docs/framework/data/adonet/sql/table-valued-parameters.md)   
 [SQL Server 二進位和大數值資料](../../../../../docs/framework/data/adonet/sql/sql-server-binary-and-large-value-data.md)   
 [ADO.NET Managed 提供者和資料集開發人員中心](http://go.microsoft.com/fwlink/?LinkId=217917)