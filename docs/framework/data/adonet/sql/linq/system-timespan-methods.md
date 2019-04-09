---
title: System.TimeSpan 方法
ms.date: 03/30/2017
ms.assetid: 9333fee8-1454-4374-855b-8c14c002f48f
ms.openlocfilehash: dd693a64550293d6894e1d2abc3f651a53fc17fc
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59126941"
---
# <a name="systemtimespan-methods"></a><span data-ttu-id="29f71-102">System.TimeSpan 方法</span><span class="sxs-lookup"><span data-stu-id="29f71-102">System.TimeSpan Methods</span></span>
<span data-ttu-id="29f71-103"><xref:System.TimeSpan?displayProperty=nameWithType> 的成員支援主要取決於您所使用的 .NET Framework 和 Microsoft SQL Server 版本。</span><span class="sxs-lookup"><span data-stu-id="29f71-103">Member support for <xref:System.TimeSpan?displayProperty=nameWithType> greatly depends on the versions of the .NET Framework and Microsoft SQL Server that you are using.</span></span>  
  
 <span data-ttu-id="29f71-104">不支援某種方法、運算子或屬性時，就表示 LINQ to SQL 無法轉譯該成員，以便在 SQL Server 上執行。</span><span class="sxs-lookup"><span data-stu-id="29f71-104">When a method, operator, or property is unsupported; it means that LINQ to SQL cannot translate the member for execution on the SQL Server.</span></span> <span data-ttu-id="29f71-105">雖然您仍然可以在程式碼中使用這些成員，</span><span class="sxs-lookup"><span data-stu-id="29f71-105">You may still be able to use these members in your code.</span></span> <span data-ttu-id="29f71-106">但是必須在查詢轉譯成 Transact-SQL 之前或從資料庫中擷取結果之後，評估這些成員。</span><span class="sxs-lookup"><span data-stu-id="29f71-106">However, they must be evaluated before the query is translated to Transact-SQL or after the results have been retrieved from the database.</span></span>  
  
## <a name="previous-limitations"></a><span data-ttu-id="29f71-107">先前的限制</span><span class="sxs-lookup"><span data-stu-id="29f71-107">Previous Limitations</span></span>  
 <span data-ttu-id="29f71-108">使用 LINQ to SQL 搭配 .NET Framework 3.5 SP1 之前的 .NET Framework 版本時，您無法將 SQL Server 資料庫欄位對應至 <xref:System.TimeSpan?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="29f71-108">When using LINQ to SQL with versions of the .NET Framework prior to .NET Framework 3.5 SP1, you cannot map SQL Server database fields to <xref:System.TimeSpan?displayProperty=nameWithType>.</span></span> <span data-ttu-id="29f71-109">但是，支援 <xref:System.TimeSpan> 的作業，因為 <xref:System.TimeSpan> 值可以從 <xref:System.DateTime> 減法傳回，或引進運算式中做為常值或繫結變數。</span><span class="sxs-lookup"><span data-stu-id="29f71-109">However, operations on <xref:System.TimeSpan> are supported because <xref:System.TimeSpan> values can be returned from <xref:System.DateTime> subtraction or introduced into an expression as a literal or bound variable.</span></span>  
  
## <a name="supported-systemtimespan-member-support"></a><span data-ttu-id="29f71-110">支援的 System.TimeSpan 成員支援</span><span class="sxs-lookup"><span data-stu-id="29f71-110">Supported System.TimeSpan member support</span></span>

 <span data-ttu-id="29f71-111">下列 LINQ to SQL 支援的方法、運算子和屬性都可讓您用於 LINQ to SQL 查詢中。</span><span class="sxs-lookup"><span data-stu-id="29f71-111">The following LINQ to SQL-supported methods, operators, and properties are available for you to use in your LINQ to SQL queries.</span></span> <span data-ttu-id="29f71-112">一旦在物件模型 (Object Model) 或外部對應檔案中對應之後，LINQ to SQL 就可讓您在 LINQ to SQL 查詢內部呼叫許多 <xref:System.TimeSpan?displayProperty=nameWithType> 成員。</span><span class="sxs-lookup"><span data-stu-id="29f71-112">Once mapped in the object model or external mapping file, LINQ to SQL allows you to call many of the <xref:System.TimeSpan?displayProperty=nameWithType> members inside your LINQ to SQL queries.</span></span>  
  
|<span data-ttu-id="29f71-113">支援的 <xref:System.TimeSpan> 方法</span><span class="sxs-lookup"><span data-stu-id="29f71-113">Supported <xref:System.TimeSpan> Methods</span></span>|<span data-ttu-id="29f71-114">支援的 <xref:System.TimeSpan> 運算子</span><span class="sxs-lookup"><span data-stu-id="29f71-114">Supported <xref:System.TimeSpan> Operators</span></span>|<span data-ttu-id="29f71-115">支援的 <xref:System.TimeSpan> 屬性</span><span class="sxs-lookup"><span data-stu-id="29f71-115">Supported <xref:System.TimeSpan> Properties</span></span>|  
|------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------|  
|<xref:System.TimeSpan.Compare%2A>|<xref:System.TimeSpan.op_Equality%2A>|<xref:System.TimeSpan.Days%2A>|  
|<xref:System.TimeSpan.CompareTo%28System.TimeSpan%29>|<xref:System.TimeSpan.op_GreaterThan%2A>|<xref:System.TimeSpan.Hours%2A>|  
|<xref:System.TimeSpan.Duration%2A>|<xref:System.TimeSpan.op_GreaterThanOrEqual%2A>|<xref:System.TimeSpan.MaxValue>|  
|<xref:System.TimeSpan.Equals%28System.TimeSpan%2CSystem.TimeSpan%29>|<xref:System.TimeSpan.op_Inequality%2A>|<xref:System.TimeSpan.Milliseconds%2A>|  
|<xref:System.TimeSpan.Equals%28System.TimeSpan%29>|<xref:System.TimeSpan.op_LessThan%2A>|<xref:System.TimeSpan.Minutes%2A>|  
||<xref:System.TimeSpan.op_LessThanOrEqual%2A>|<xref:System.TimeSpan.MinValue>|  
  
> [!NOTE]
>  <span data-ttu-id="29f71-116">透過 LINQ to SQL 將 <xref:System.TimeSpan?displayProperty=nameWithType> 對應至 SQL `TIME` 資料行的功能需要 .NET Framework 3.5 SP1 和更新版本。</span><span class="sxs-lookup"><span data-stu-id="29f71-116">The ability to map <xref:System.TimeSpan?displayProperty=nameWithType> to a SQL `TIME` column with LINQ to SQL requires the .NET Framework 3.5 SP1 and beyond.</span></span> <span data-ttu-id="29f71-117">SQL `TIME` 資料型別只能在 Microsoft SQL Server 2008 和更新版本中使用。</span><span class="sxs-lookup"><span data-stu-id="29f71-117">The SQL `TIME` data type is only available in Microsoft SQL Server 2008 and beyond.</span></span>  
  
### <a name="addition-and-subtraction"></a><span data-ttu-id="29f71-118">加法和減法</span><span class="sxs-lookup"><span data-stu-id="29f71-118">Addition and Subtraction</span></span>  
 <span data-ttu-id="29f71-119">雖然 CLR <xref:System.TimeSpan?displayProperty=nameWithType> 型別支援加法和減法，但是 SQL `TIME` 型別卻不支援。</span><span class="sxs-lookup"><span data-stu-id="29f71-119">Although the CLR <xref:System.TimeSpan?displayProperty=nameWithType> type does support addition and subtraction, the SQL `TIME` type does not.</span></span> <span data-ttu-id="29f71-120">因此，如果您的 LINQ to SQL 查詢嘗試在對應至 SQL `TIME` 型別時進行加法和減法，它們將會產生錯誤。</span><span class="sxs-lookup"><span data-stu-id="29f71-120">Because of this, your LINQ to SQL queries will generate errors if they attempt addition and subtraction when they are mapped to the SQL `TIME` type.</span></span> <span data-ttu-id="29f71-121">您可以找到 SQL 中的日期和時間類型使用的其他考量事項[SQL-CLR 類型對應](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mapping.md)。</span><span class="sxs-lookup"><span data-stu-id="29f71-121">You can find other considerations for working with SQL date and time types in [SQL-CLR Type Mapping](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mapping.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="29f71-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="29f71-122">See also</span></span>

- [<span data-ttu-id="29f71-123">查詢概念</span><span class="sxs-lookup"><span data-stu-id="29f71-123">Query Concepts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)
- [<span data-ttu-id="29f71-124">建立物件模型</span><span class="sxs-lookup"><span data-stu-id="29f71-124">Creating the Object Model</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/creating-the-object-model.md)
- [<span data-ttu-id="29f71-125">SQL-CLR 類型對應</span><span class="sxs-lookup"><span data-stu-id="29f71-125">SQL-CLR Type Mapping</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mapping.md)
- [<span data-ttu-id="29f71-126">資料類型與函式</span><span class="sxs-lookup"><span data-stu-id="29f71-126">Data Types and Functions</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/data-types-and-functions.md)
