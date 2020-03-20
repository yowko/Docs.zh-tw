---
title: LINQ to Entities 中的已知問題和考量
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: acd71129-5ff0-4b4e-b266-c72cc0c53601
ms.openlocfilehash: 90119da0fce7a708323d790f91f28206cac0a0dc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150138"
---
# <a name="known-issues-and-considerations-in-linq-to-entities"></a><span data-ttu-id="5e325-102">LINQ to Entities 中的已知問題和考量</span><span class="sxs-lookup"><span data-stu-id="5e325-102">Known Issues and Considerations in LINQ to Entities</span></span>
<span data-ttu-id="5e325-103">本節提供有關 LINQ 到實體查詢的已知問題的資訊。</span><span class="sxs-lookup"><span data-stu-id="5e325-103">This section provides information about known issues with LINQ to Entities queries.</span></span>  
  
- [<span data-ttu-id="5e325-104">不能快取的 LINQ 查詢</span><span class="sxs-lookup"><span data-stu-id="5e325-104">LINQ Queries That cannot be Cached</span></span>](#LINQQueriesThatAreNotCached)  
  
- [<span data-ttu-id="5e325-105">排序資訊遺失</span><span class="sxs-lookup"><span data-stu-id="5e325-105">Ordering Information Lost</span></span>](#OrderingInfoLost)  
  
- [<span data-ttu-id="5e325-106">不支援不帶正負號的整數</span><span class="sxs-lookup"><span data-stu-id="5e325-106">Unsigned Integers Not Supported</span></span>](#UnsignedIntsUnsupported)  
  
- [<span data-ttu-id="5e325-107">類型轉換錯誤</span><span class="sxs-lookup"><span data-stu-id="5e325-107">Type Conversion Errors</span></span>](#TypeConversionErrors)  
  
- [<span data-ttu-id="5e325-108">不支援參考非純量變數</span><span class="sxs-lookup"><span data-stu-id="5e325-108">Referencing Non-Scalar Variables Not Supported</span></span>](#RefNonScalarClosures)  
  
- [<span data-ttu-id="5e325-109">使用 SQL Server 2000 的巢狀查詢可能失敗</span><span class="sxs-lookup"><span data-stu-id="5e325-109">Nested Queries May Fail with SQL Server 2000</span></span>](#NestedQueriesSQL2000)  
  
- [<span data-ttu-id="5e325-110">投影至匿名型別</span><span class="sxs-lookup"><span data-stu-id="5e325-110">Projecting to an Anonymous Type</span></span>](#ProjectToAnonymousType)  
  
<a name="LINQQueriesThatAreNotCached"></a>
## <a name="linq-queries-that-cannot-be-cached"></a><span data-ttu-id="5e325-111">不能快取的 LINQ 查詢</span><span class="sxs-lookup"><span data-stu-id="5e325-111">LINQ Queries That cannot be Cached</span></span>  
 <span data-ttu-id="5e325-112">從 .NET Framework 4.5 開始會自動快取 LINQ to Entities 查詢。</span><span class="sxs-lookup"><span data-stu-id="5e325-112">Starting with .NET Framework 4.5, LINQ to Entities queries are automatically cached.</span></span> <span data-ttu-id="5e325-113">不過，不會自動快取將 `Enumerable.Contains`運算子套用至記憶體中集合的 LINQ to Entities 查詢。</span><span class="sxs-lookup"><span data-stu-id="5e325-113">However, LINQ to Entities queries that apply the `Enumerable.Contains` operator to in-memory collections are not automatically cached.</span></span> <span data-ttu-id="5e325-114">此外也不允許在已編譯的 LINQ 查詢中參數化記憶體中的集合。</span><span class="sxs-lookup"><span data-stu-id="5e325-114">Also parameterizing in-memory collections in compiled LINQ queries is not allowed.</span></span>  
  
<a name="OrderingInfoLost"></a>
## <a name="ordering-information-lost"></a><span data-ttu-id="5e325-115">排序資訊遺失</span><span class="sxs-lookup"><span data-stu-id="5e325-115">Ordering Information Lost</span></span>  
 <span data-ttu-id="5e325-116">將列投影到匿名型別將導致某些查詢中針對 SQL Server 2005 資料庫設置為"80"的相容性級別執行的排序資訊丟失。</span><span class="sxs-lookup"><span data-stu-id="5e325-116">Projecting columns into an anonymous type will cause ordering information to be lost in some queries that are executed against a SQL Server 2005 database set to a compatibility level of "80".</span></span>  <span data-ttu-id="5e325-117">如果 order-by 清單中的資料行名稱與 selector 中的資料行名稱相符，就會發生這種情況，如以下範例所示：</span><span class="sxs-lookup"><span data-stu-id="5e325-117">This occurs when a column name in the order-by list matches a column name in the selector, as shown in the following example:</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#SBUDT543840](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#sbudt543840)]
 [!code-vb[DP L2E Conceptual Examples#SBUDT543840](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#sbudt543840)]  
  
<a name="UnsignedIntsUnsupported"></a>
## <a name="unsigned-integers-not-supported"></a><span data-ttu-id="5e325-118">不支援不帶正負號的整數</span><span class="sxs-lookup"><span data-stu-id="5e325-118">Unsigned Integers Not Supported</span></span>  
 <span data-ttu-id="5e325-119">不支援在 LINQ 到實體查詢中指定未簽名整數類型，因為實體框架不支援未簽名整數。</span><span class="sxs-lookup"><span data-stu-id="5e325-119">Specifying an unsigned integer type in a LINQ to Entities query is not supported because the Entity Framework does not support unsigned integers.</span></span> <span data-ttu-id="5e325-120">如果指定未簽名整數，則查詢運算式轉換<xref:System.ArgumentException>期間將引發異常，如以下示例所示。</span><span class="sxs-lookup"><span data-stu-id="5e325-120">If you specify an unsigned integer, an <xref:System.ArgumentException> exception will be thrown during the query expression translation, as shown in the following example.</span></span> <span data-ttu-id="5e325-121">此範例會查詢 ID 為 48000 的訂單。</span><span class="sxs-lookup"><span data-stu-id="5e325-121">This example queries for an order with ID 48000.</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#UIntAsQueryParam](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#uintasqueryparam)]
 [!code-vb[DP L2E Conceptual Examples#UIntAsQueryParam](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#uintasqueryparam)]  
  
<a name="TypeConversionErrors"></a>
## <a name="type-conversion-errors"></a><span data-ttu-id="5e325-122">型別轉換錯誤</span><span class="sxs-lookup"><span data-stu-id="5e325-122">Type Conversion Errors</span></span>  
 <span data-ttu-id="5e325-123">在 Visual Basic 中，使用 `CByte` 函式將屬性對應到值為 1 的 SQL Server 位元型別資料行時，將會擲回 <xref:System.Data.SqlClient.SqlException> 並且顯示「算術溢位錯誤」訊息。</span><span class="sxs-lookup"><span data-stu-id="5e325-123">In Visual Basic, when a property is mapped to a column of SQL Server bit type with a value of 1 using the `CByte` function, a <xref:System.Data.SqlClient.SqlException> is thrown with an "Arithmetic overflow error" message.</span></span> <span data-ttu-id="5e325-124">以下範例會查詢 AdventureWorks 範例資料庫中的 `Product.MakeFlag` 資料行，並且在重複處理查詢結果時擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="5e325-124">The following example queries the `Product.MakeFlag` column in the AdventureWorks sample database and an exception is thrown when the query results are iterated over.</span></span>  
  
 [!code-vb[DP L2E Conceptual Examples#SBUDT544355](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#sbudt544355)]  
  
<a name="RefNonScalarClosures"></a>
## <a name="referencing-non-scalar-variables-not-supported"></a><span data-ttu-id="5e325-125">不支援參考非純量變數</span><span class="sxs-lookup"><span data-stu-id="5e325-125">Referencing Non-Scalar Variables Not Supported</span></span>  
 <span data-ttu-id="5e325-126">不支援在查詢中參考非純量變數，例如實體。</span><span class="sxs-lookup"><span data-stu-id="5e325-126">Referencing a non-scalar variables, such as an entity, in a query is not supported.</span></span> <span data-ttu-id="5e325-127">執行這類查詢時，系統會擲回 <xref:System.NotSupportedException> 例外狀況，並且顯示一則訊息，表示「無法建立 `EntityType` 型別的常數值。</span><span class="sxs-lookup"><span data-stu-id="5e325-127">When such a query executes, a <xref:System.NotSupportedException> exception is thrown with a message that states "Unable to create a constant value of type `EntityType`.</span></span> <span data-ttu-id="5e325-128">在此僅支援基本型別 (『例如 Int32、String 和 Guid』)」。</span><span class="sxs-lookup"><span data-stu-id="5e325-128">Only primitive types ('such as Int32, String, and Guid') are supported in this context."</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5e325-129">支援參考純量變數的集合。</span><span class="sxs-lookup"><span data-stu-id="5e325-129">Referencing a collection of scalar variables is supported.</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#SBUDT555877](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#sbudt555877)]
 [!code-vb[DP L2E Conceptual Examples#SBUDT555877](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#sbudt555877)]  
  
<a name="NestedQueriesSQL2000"></a>
## <a name="nested-queries-may-fail-with-sql-server-2000"></a><span data-ttu-id="5e325-130">使用 SQL Server 2000 的巢狀查詢可能失敗</span><span class="sxs-lookup"><span data-stu-id="5e325-130">Nested Queries May Fail with SQL Server 2000</span></span>  
 <span data-ttu-id="5e325-131">使用 SQL Server 2000 時，如果 LINQ to Entities 查詢產生三層或更多層深度的巢狀 Transact-SQL 查詢，則查詢可能會失敗。</span><span class="sxs-lookup"><span data-stu-id="5e325-131">With SQL Server 2000, LINQ to Entities queries may fail if they produce nested Transact-SQL queries that are three or more levels deep.</span></span>  
  
<a name="ProjectToAnonymousType"></a>
## <a name="projecting-to-an-anonymous-type"></a><span data-ttu-id="5e325-132">投影至匿名型別</span><span class="sxs-lookup"><span data-stu-id="5e325-132">Projecting to an Anonymous Type</span></span>  
 <span data-ttu-id="5e325-133">如果您透過在 <xref:System.Data.Objects.ObjectQuery%601.Include%2A> 上使用 <xref:System.Data.Objects.ObjectQuery%601> 方法，將初始查詢路徑定義為包括相關物件，然後使用 LINQ 將傳回的物件投影至匿名型別，則包括方法中所指定的物件不會包括在查詢結果中。</span><span class="sxs-lookup"><span data-stu-id="5e325-133">If you define your initial query path to include related objects by using the <xref:System.Data.Objects.ObjectQuery%601.Include%2A> method on the <xref:System.Data.Objects.ObjectQuery%601> and then use LINQ to project the returned objects to an anonymous type, the objects specified in the include method are not included in the query results.</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#ProjToAnonType1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#projtoanontype1)]
 [!code-vb[DP L2E Conceptual Examples#ProjToAnonType1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#projtoanontype1)]  
  
 <span data-ttu-id="5e325-134">若要取得相關物件，請不要將傳回的型別投影至匿名型別。</span><span class="sxs-lookup"><span data-stu-id="5e325-134">To get related objects, do not project returned types to an anonymous type.</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#ProjToAnonType2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#projtoanontype2)]
 [!code-vb[DP L2E Conceptual Examples#ProjToAnonType2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#projtoanontype2)]  
  
## <a name="see-also"></a><span data-ttu-id="5e325-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5e325-135">See also</span></span>

- [<span data-ttu-id="5e325-136">林Q 到實體</span><span class="sxs-lookup"><span data-stu-id="5e325-136">LINQ to Entities</span></span>](linq-to-entities.md)
