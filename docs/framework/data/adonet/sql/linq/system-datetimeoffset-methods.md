---
title: System.DateTimeOffset 方法
ms.date: 03/30/2017
ms.assetid: 25b3e5c0-7603-4a70-b3e5-2149e3da69a2
ms.openlocfilehash: 2e29cf02d4f7e8004782264bf940bb1faf393269
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70781556"
---
# <a name="systemdatetimeoffset-methods"></a>System.DateTimeOffset 方法
一旦在物件模型 (Object Model) 或外部對應檔案中對應之後，LINQ to SQL 就可讓您從 LINQ to SQL 查詢內部呼叫大部分 <xref:System.DateTimeOffset?displayProperty=nameWithType> 方法、運算子和屬性。  
  
 不支援的方法只有繼承自 <xref:System.Object?displayProperty=nameWithType> 而且在 LINQ to SQL 查詢內容中沒有意義的方法，例如：`Finalize`、`GetHashCode`、`GetType` 和 `MemberwiseClone`。 不支援這些方法的原因是，LINQ to SQL 無法轉譯它們，以便在 SQL Server 上執行。  
  
> [!NOTE]
> Common Language Runtime (CLR) <xref:System.DateTimeOffset?displayProperty=nameWithType> 結構以及透過 LINQ to SQL 將它對應至 SQL `DATETIMEOFFSET` 資料行的功能都需要 .NET Framework 3.5 SP1 或更新版本。 SQL `DATETIMEOFFSET` 資料行只能在 Microsoft SQL Server 2008 和更新版本中使用。  
  
## <a name="sqlmethods-date-and-time-methods"></a>SQLMethods 日期和時間方法  
 除了 <xref:System.DateTimeOffset> 結構所提供的方法以外，LINQ to SQL 還從 <xref:System.Data.Linq.SqlClient.SqlMethods?displayProperty=nameWithType> 類別 (Class) 中提供了下表所列的方法，以便使用日期和時間。  
  
||||  
|-|-|-|  
|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffDay%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffMillisecond%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffNanosecond%2A>|  
|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffHour%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffMinute%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffSecond%2A>|  
|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffMicrosecond%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffMonth%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffYear%2A>|  
  
## <a name="see-also"></a>另請參閱

- [查詢概念](query-concepts.md)
- [建立物件模型](creating-the-object-model.md)
- [SQL-CLR 類型對應](sql-clr-type-mapping.md)
