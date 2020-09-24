---
title: SQL Server 資料類型和 ADO.NET
titleSuffix: ''
ms.date: 03/30/2017
ms.assetid: 81b43550-23e8-43bb-b460-7eb8ac825c33
ms.openlocfilehash: db4618ac624ea8401cab682a8c21d8f23c253d05
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91155454"
---
# <a name="sql-server-data-types-and-adonet"></a>SQL Server 資料類型和 ADO.NET

SQL Server 和 .NET Framework 是以不同的型別系統為基礎，而且可能會導致資料遺失。 為了保留資料完整性，.NET Framework Data Provider for SQL Server (<xref:System.Data.SqlClient>) 針對使用 SQL Server 資料提供了具型別的存取子方法。 您可以使用 <xref:System.Data.SqlDbType> 類別中的列舉來指定 <xref:System.Data.SqlClient.SqlParameter> 資料類型。  
  
 如需描述 SQL Server 和 .NET Framework 資料類型之間資料類型對應的詳細資訊和資料表，請參閱 [SQL Server 資料類型](../sql-server-data-type-mappings.md)對應。  
  
 SQL Server 2008 引進了新的資料類型，其設計目的是為了符合商務需求，以處理日期和時間、結構化、半結構化與非結構化資料。 《SQL Server 2008 線上叢書》中有說明。  
  
 可在應用程式中使用的 SQL Server 資料類型，取決於您目前使用的 SQL Server 版本。 如需詳細資訊，請參閱下表中的相關《SQL Server 線上叢書》版本。  
  
 **SQL Server 文件**  
  
1. [資料類型 (Transact-SQL)](/sql/t-sql/data-types/data-types-transact-sql)  
  
## <a name="in-this-section"></a>本節內容  

 [SqlTypes 和資料集](sqltypes-and-the-dataset.md)  
 說明針對 `DataSet` 中的 `SqlTypes` 所提供的類型支援。  
  
 [處理 Null 值](handling-null-values.md)  
 示範如何處理 Null 值與三值邏輯。  
  
 [比較 GUID 和 uniqueidentifier 值](comparing-guid-and-uniqueidentifier-values.md)  
 示範如何在 SQL Server 和 .NET Framework 中使用 GUID 和 uniqueidentifier 值。  
  
 [日期和時間資料](date-and-time-data.md)  
 描述如何使用 SQL Server 2008 中引進的新日期和時間資料類型。  
  
 [大型 UDT](large-udts.md)  
 示範如何從 SQL Server 2008 引進的大型值 UDT 擷取資料。  
  
 [SQL Server 中的 XML 資料](xml-data-in-sql-server.md)  
 說明如何使用從 SQL Server 擷取的 XML 資料。  
  
## <a name="reference"></a>參考  

 <xref:System.Data.DataSet>  
 描述 `DataSet` 類別與其所有成員。  
  
 <xref:System.Data.SqlTypes>  
 描述 `SqlTypes` 命名空間與其所有成員。  
  
 <xref:System.Data.SqlDbType>  
 描述 `SqlDbType` 列舉與其所有成員。  
  
 <xref:System.Data.DbType>  
 描述 `DbType` 列舉與其所有成員。  
  
## <a name="see-also"></a>另請參閱

- [SQL Server 資料類型對應](../sql-server-data-type-mappings.md)
- [設定參數和參數資料類型](../configuring-parameters-and-parameter-data-types.md)
- [資料表值參數](table-valued-parameters.md)
- [SQL Server 二進位和大數值資料](sql-server-binary-and-large-value-data.md)
- [ADO.NET 概觀](../ado-net-overview.md) \(部分機器翻譯\)
