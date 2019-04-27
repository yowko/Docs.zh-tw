---
title: System.DateTime 方法
ms.date: 03/30/2017
ms.assetid: 4f80700c-e83f-4ab6-af0f-1c9a606e1133
ms.openlocfilehash: 85af6f252362b811356d68a3ae220df2bb813882
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61876768"
---
# <a name="systemdatetime-methods"></a><span data-ttu-id="9d678-102">System.DateTime 方法</span><span class="sxs-lookup"><span data-stu-id="9d678-102">System.DateTime Methods</span></span>
<span data-ttu-id="9d678-103">下列 LINQ to SQL 支援的方法、運算子和屬性都可用於 LINQ to SQL 查詢中。</span><span class="sxs-lookup"><span data-stu-id="9d678-103">The following LINQ to SQL-supported methods, operators, and properties are available to use in LINQ to SQL queries.</span></span> <span data-ttu-id="9d678-104">不支援某種方法、運算子或屬性時，就表示 LINQ to SQL 無法轉譯該成員，以便在 SQL Server 上執行。</span><span class="sxs-lookup"><span data-stu-id="9d678-104">When a method, operator or property is unsupported, LINQ to SQL cannot translate the member for execution on the SQL Server.</span></span> <span data-ttu-id="9d678-105">雖然您可以在程式碼中使用這些成員，但是必須在查詢轉譯成 Transact-SQL 之前或從資料庫中擷取結果之後，評估這些成員。</span><span class="sxs-lookup"><span data-stu-id="9d678-105">You may use these members in your code, however, they must be evaluated before the query is translated to Transact-SQL or after the results have been retrieved from the database.</span></span>  
  
## <a name="supported-systemdatetime-members"></a><span data-ttu-id="9d678-106">支援的 System.DateTime 成員</span><span class="sxs-lookup"><span data-stu-id="9d678-106">Supported System.DateTime Members</span></span>  
 <span data-ttu-id="9d678-107">一旦在物件模型 (Object Model) 或外部對應檔案中對應之後，LINQ to SQL 就可讓您在 LINQ to SQL 查詢內部呼叫下列 <xref:System.DateTime?displayProperty=nameWithType> 成員。</span><span class="sxs-lookup"><span data-stu-id="9d678-107">Once mapped in the object model or external mapping file, LINQ to SQL allows you to call the following <xref:System.DateTime?displayProperty=nameWithType> members inside LINQ to SQL queries.</span></span>  
  
|<span data-ttu-id="9d678-108">支援的 <xref:System.DateTime> 方法</span><span class="sxs-lookup"><span data-stu-id="9d678-108">Supported <xref:System.DateTime> Methods</span></span>|<span data-ttu-id="9d678-109">支援的 <xref:System.DateTime> 運算子</span><span class="sxs-lookup"><span data-stu-id="9d678-109">Supported <xref:System.DateTime> Operators</span></span>|<span data-ttu-id="9d678-110">支援的 <xref:System.DateTime> 屬性</span><span class="sxs-lookup"><span data-stu-id="9d678-110">Supported <xref:System.DateTime> Properties</span></span>|  
|------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------|  
|<xref:System.DateTime.Add%2A>|<xref:System.DateTime.op_Addition%2A>|<xref:System.DateTime.Date%2A>|  
|<xref:System.DateTime.AddDays%2A>|<xref:System.DateTime.op_Equality%2A>|<xref:System.DateTime.Day%2A>|  
|<xref:System.DateTime.AddHours%2A>|<xref:System.DateTime.op_GreaterThan%2A>|<xref:System.DateTime.DayOfWeek%2A>|  
|<xref:System.DateTime.AddMilliseconds%2A>|<xref:System.DateTime.op_GreaterThanOrEqual%2A>|<xref:System.DateTime.DayOfYear%2A>|  
|<xref:System.DateTime.AddMinutes%2A>|<xref:System.DateTime.op_Inequality%2A>|<xref:System.DateTime.Hour%2A>|  
|<xref:System.DateTime.AddMonths%2A>|<xref:System.DateTime.op_LessThan%2A>|<xref:System.DateTime.Millisecond%2A>|  
|<xref:System.DateTime.AddSeconds%2A>|<xref:System.DateTime.op_LessThanOrEqual%2A>|<xref:System.DateTime.Minute%2A>|  
|<xref:System.DateTime.AddTicks%2A>|<xref:System.DateTime.op_Subtraction%2A>|<xref:System.DateTime.Month%2A>|  
|<xref:System.DateTime.AddYears%2A>||<xref:System.DateTime.Now%2A>|  
|<xref:System.DateTime.Compare%2A>||<xref:System.DateTime.Second%2A>|  
|<xref:System.DateTime.CompareTo%28System.DateTime%29>||<xref:System.DateTime.TimeOfDay%2A>|  
|<xref:System.DateTime.Equals%28System.DateTime%29>||<xref:System.DateTime.Today%2A>|  
|||<xref:System.DateTime.Year%2A>|  
  
## <a name="members-not-supported-by-linq-to-sql"></a><span data-ttu-id="9d678-111">LINQ to SQL 不支援的成員</span><span class="sxs-lookup"><span data-stu-id="9d678-111">Members Not Supported by LINQ to SQL</span></span>  
 <span data-ttu-id="9d678-112">不支援在 LINQ to SQL 查詢內部使用下列成員。</span><span class="sxs-lookup"><span data-stu-id="9d678-112">The following members are not supported inside LINQ to SQL queries.</span></span>  
  
|||  
|-|-|  
|<xref:System.DateTime.IsDaylightSavingTime%2A>|<xref:System.DateTime.IsLeapYear%2A>|  
|<xref:System.DateTime.DaysInMonth%2A>|<xref:System.DateTime.ToBinary%2A>|  
|<xref:System.DateTime.ToFileTime%2A>|<xref:System.DateTime.ToFileTimeUtc%2A>|  
|<xref:System.DateTime.ToLongDateString%2A>|<xref:System.DateTime.ToLongTimeString%2A>|  
|<xref:System.DateTime.ToOADate%2A>|<xref:System.DateTime.ToShortDateString%2A>|  
|<xref:System.DateTime.ToShortTimeString%2A>|<xref:System.DateTime.ToUniversalTime%2A>|  
|<xref:System.DateTime.FromBinary%2A>|<xref:System.DateTime.UtcNow%2A>|  
|<xref:System.DateTime.FromFileTime%2A>|<xref:System.DateTime.FromFileTimeUtc%2A>|  
|<xref:System.DateTime.FromOADate%2A>|<xref:System.DateTime.GetDateTimeFormats%2A>|  
  
## <a name="method-translation-example"></a><span data-ttu-id="9d678-113">方法轉譯範例</span><span class="sxs-lookup"><span data-stu-id="9d678-113">Method Translation Example</span></span>  
 <span data-ttu-id="9d678-114">所有 LINQ to SQL 支援的方法都會先轉譯成 Transact-SQL，然後再傳送至 SQL Server。</span><span class="sxs-lookup"><span data-stu-id="9d678-114">All methods supported by LINQ to SQL are translated to Transact-SQL before they are sent to   SQL Server.</span></span> <span data-ttu-id="9d678-115">例如，以下列模式為例。</span><span class="sxs-lookup"><span data-stu-id="9d678-115">For example, consider the following pattern.</span></span>  
  
 `(dateTime1 – dateTime2).{Days, Hours, Milliseconds, Minutes, Months, Seconds, Years}`  
  
 <span data-ttu-id="9d678-116">加以辨識後，就會轉譯成對 SQL Server `DATEDIFF` 函式的直接呼叫，如下所示：</span><span class="sxs-lookup"><span data-stu-id="9d678-116">When it is recognized, it is translated into a direct call to the SQL Server `DATEDIFF` function, as follows:</span></span>  
  
 `DATEDIFF({DatePart}, @dateTime1, @dateTime2)`  
  
## <a name="sqlmethods-date-and-time-methods"></a><span data-ttu-id="9d678-117">SQLMethods 日期和時間方法</span><span class="sxs-lookup"><span data-stu-id="9d678-117">SQLMethods Date and Time Methods</span></span>  
 <span data-ttu-id="9d678-118">除了 <xref:System.DateTime> 結構所提供的方法以外，LINQ to SQL 還從 <xref:System.Data.Linq.SqlClient.SqlMethods?displayProperty=nameWithType> 類別 (Class) 中提供了下表所列的方法，以便使用日期和時間。</span><span class="sxs-lookup"><span data-stu-id="9d678-118">In addition to the methods offered by the <xref:System.DateTime> structure, LINQ to SQL offers the methods listed in the following table from the <xref:System.Data.Linq.SqlClient.SqlMethods?displayProperty=nameWithType> class for working with date and time.</span></span>  
  
||||  
|-|-|-|  
|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffDay%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffMillisecond%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffNanosecond%2A>|  
|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffHour%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffMinute%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffSecond%2A>|  
|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffMicrosecond%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffMonth%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffYear%2A>|  
  
## <a name="see-also"></a><span data-ttu-id="9d678-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9d678-119">See also</span></span>

- [<span data-ttu-id="9d678-120">查詢概念</span><span class="sxs-lookup"><span data-stu-id="9d678-120">Query Concepts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)
- [<span data-ttu-id="9d678-121">建立物件模型</span><span class="sxs-lookup"><span data-stu-id="9d678-121">Creating the Object Model</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/creating-the-object-model.md)
- [<span data-ttu-id="9d678-122">SQL-CLR 類型對應</span><span class="sxs-lookup"><span data-stu-id="9d678-122">SQL-CLR Type Mapping</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mapping.md)
- [<span data-ttu-id="9d678-123">資料類型和函式</span><span class="sxs-lookup"><span data-stu-id="9d678-123">Data Types and Functions</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/data-types-and-functions.md)
