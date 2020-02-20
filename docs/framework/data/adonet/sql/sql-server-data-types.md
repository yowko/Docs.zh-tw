---
title: SQL Server 資料類型和 ADO.NET
titleSuffix: ''
ms.date: 03/30/2017
ms.assetid: 81b43550-23e8-43bb-b460-7eb8ac825c33
ms.openlocfilehash: f727c69b1dd5c23c6a89911005256de70255fd4c
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452327"
---
# <a name="sql-server-data-types-and-adonet"></a>SQL Server 資料類型和 ADO.NET
SQL Server 和 .NET Framework 是以不同的型別系統為基礎，而且可能會導致資料遺失。 為了保留資料完整性，.NET Framework Data Provider for SQL Server (<xref:System.Data.SqlClient>) 針對使用 SQL Server 資料提供了具型別的存取子方法。 您可以使用 <xref:System.Data.SqlDbType> 類別 (Class) 中的列舉型別 (Enumeration) 來指定 <xref:System.Data.SqlClient.SqlParameter> 資料型別。  
  
 如需詳細資訊和描述 SQL Server 和 .NET Framework 資料類型之間之資料類型對應的資料表，請參閱[SQL Server 資料類型](../sql-server-data-type-mappings.md)對應。  
  
 SQL Server 2008 導入了一些設計成符合商務需求的新資料型別，以便使用日期和時間、結構化、半結構化和非結構化資料。 《SQL Server 2008 線上叢書》中有說明。  
  
 可用於應用程式中的 SQL Server 資料型別取決於您所使用的 SQL Server 版本。 如需詳細資訊，請參閱下表中的相關《SQL Server 線上叢書》版本。  
  
 **SQL Server 文件**  
  
1. [資料類型 (Transact-SQL)](/sql/t-sql/data-types/data-types-transact-sql)  
  
## <a name="in-this-section"></a>本節內容  
 [SqlTypes 和資料集](sqltypes-and-the-dataset.md)  
 說明針對 `SqlTypes` 中的 `DataSet` 所提供的類型支援。  
  
 [處理 Null 值](handling-null-values.md)  
 示範如何使用 Null 值和三種值的邏輯。  
  
 [比較 GUID 和 uniqueidentifier 值](comparing-guid-and-uniqueidentifier-values.md)  
 示範如何在 SQL Server 和 .NET Framework 中使用 GUID 和 uniqueidentifier 值。  
  
 [日期和時間資料](date-and-time-data.md)  
 說明如何使用 SQL Server 2008 所導入的新日期和時間資料型別。  
  
 [大型 UDT](large-udts.md)  
 示範如何從 SQL Server 2008 所導入的大數值 UDT 中擷取資料。  
  
 [SQL Server 中的 XML 資料](xml-data-in-sql-server.md)  
 說明如何使用從 SQL Server 擷取的 XML 資料。  
  
## <a name="reference"></a>參考  
 <xref:System.Data.DataSet>  
 說明 `DataSet` 類別及其所有成員。  
  
 <xref:System.Data.SqlTypes>  
 說明 `SqlTypes` 命名空間 (Namespace) 及其所有成員。  
  
 <xref:System.Data.SqlDbType>  
 說明 `SqlDbType` 列舉型別及其所有成員。  
  
 <xref:System.Data.DbType>  
 說明 `DbType` 列舉型別及其所有成員。  
  
## <a name="see-also"></a>另請參閱

- [SQL Server 資料類型對應](../sql-server-data-type-mappings.md)
- [設定參數和參數資料類型](../configuring-parameters-and-parameter-data-types.md)
- [資料表值參數](table-valued-parameters.md)
- [SQL Server 二進位和大量數值資料](sql-server-binary-and-large-value-data.md)
- [ADO.NET 概觀](../ado-net-overview.md)
