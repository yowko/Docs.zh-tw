---
title: System.DateTimeOffset 方法
ms.date: 03/30/2017
ms.assetid: 25b3e5c0-7603-4a70-b3e5-2149e3da69a2
ms.openlocfilehash: 288a0d99feecdeccc0d215ec3c14ec31bb3ccb54
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59149717"
---
# <a name="systemdatetimeoffset-methods"></a><span data-ttu-id="d7fef-102">System.DateTimeOffset 方法</span><span class="sxs-lookup"><span data-stu-id="d7fef-102">System.DateTimeOffset Methods</span></span>
<span data-ttu-id="d7fef-103">一旦在物件模型 (Object Model) 或外部對應檔案中對應之後，LINQ to SQL 就可讓您從 LINQ to SQL 查詢內部呼叫大部分 <xref:System.DateTimeOffset?displayProperty=nameWithType> 方法、運算子和屬性。</span><span class="sxs-lookup"><span data-stu-id="d7fef-103">Once mapped in the object model or external mapping file, LINQ to SQL allows you to call most of the <xref:System.DateTimeOffset?displayProperty=nameWithType> methods, operators, and properties from within your LINQ to SQL queries.</span></span>  
  
 <span data-ttu-id="d7fef-104">不支援的方法只有繼承自 <xref:System.Object?displayProperty=nameWithType> 而且在 LINQ to SQL 查詢內容中沒有意義的方法，例如：`Finalize`、`GetHashCode`、`GetType` 和 `MemberwiseClone`。</span><span class="sxs-lookup"><span data-stu-id="d7fef-104">The only methods not supported are those inherited from <xref:System.Object?displayProperty=nameWithType> that do not make sense in the context of LINQ to SQL queries, such as: `Finalize`, `GetHashCode`, `GetType`, and `MemberwiseClone`.</span></span> <span data-ttu-id="d7fef-105">不支援這些方法的原因是，LINQ to SQL 無法轉譯它們，以便在 SQL Server 上執行。</span><span class="sxs-lookup"><span data-stu-id="d7fef-105">These methods are not supported because LINQ to SQL cannot translate them for execution on the SQL Server.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d7fef-106">Common Language Runtime (CLR) <xref:System.DateTimeOffset?displayProperty=nameWithType> 結構以及透過 LINQ to SQL 將它對應至 SQL `DATETIMEOFFSET` 資料行的功能都需要 .NET Framework 3.5 SP1 或更新版本。</span><span class="sxs-lookup"><span data-stu-id="d7fef-106">The common language runtime (CLR) <xref:System.DateTimeOffset?displayProperty=nameWithType> structure, and the ability to map it to a SQL `DATETIMEOFFSET` column with LINQ to SQL, requires the .NET Framework 3.5 SP1 or beyond.</span></span> <span data-ttu-id="d7fef-107">SQL `DATETIMEOFFSET` 資料行只能在 Microsoft SQL Server 2008 和更新版本中使用。</span><span class="sxs-lookup"><span data-stu-id="d7fef-107">The SQL `DATETIMEOFFSET` column is only available in Microsoft SQL Server 2008 and beyond.</span></span>  
  
## <a name="sqlmethods-date-and-time-methods"></a><span data-ttu-id="d7fef-108">SQLMethods 日期和時間方法</span><span class="sxs-lookup"><span data-stu-id="d7fef-108">SQLMethods Date and Time Methods</span></span>  
 <span data-ttu-id="d7fef-109">除了 <xref:System.DateTimeOffset> 結構所提供的方法以外，LINQ to SQL 還從 <xref:System.Data.Linq.SqlClient.SqlMethods?displayProperty=nameWithType> 類別 (Class) 中提供了下表所列的方法，以便使用日期和時間。</span><span class="sxs-lookup"><span data-stu-id="d7fef-109">In addition to the methods offered by the <xref:System.DateTimeOffset> structure, LINQ to SQL offers the methods listed in the following table from the <xref:System.Data.Linq.SqlClient.SqlMethods?displayProperty=nameWithType> class for working with date and time.</span></span>  
  
||||  
|-|-|-|  
|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffDay%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffMillisecond%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffNanosecond%2A>|  
|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffHour%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffMinute%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffSecond%2A>|  
|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffMicrosecond%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffMonth%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffYear%2A>|  
  
## <a name="see-also"></a><span data-ttu-id="d7fef-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d7fef-110">See also</span></span>

- [<span data-ttu-id="d7fef-111">查詢概念</span><span class="sxs-lookup"><span data-stu-id="d7fef-111">Query Concepts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)
- [<span data-ttu-id="d7fef-112">建立物件模型</span><span class="sxs-lookup"><span data-stu-id="d7fef-112">Creating the Object Model</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/creating-the-object-model.md)
- [<span data-ttu-id="d7fef-113">SQL-CLR 類型對應</span><span class="sxs-lookup"><span data-stu-id="d7fef-113">SQL-CLR Type Mapping</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mapping.md)
