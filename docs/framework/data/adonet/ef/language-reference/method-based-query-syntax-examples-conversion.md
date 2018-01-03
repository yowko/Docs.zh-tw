---
title: "以方法為基礎的查詢語法範例：轉換"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 19f66872-d5ab-49f8-969f-e53f9632a13d
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: a76ebf99e0f8abe7d0ab3052a05c813402f665b0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="method-based-query-syntax-examples-conversion"></a><span data-ttu-id="df90b-102">以方法為基礎的查詢語法範例：轉換</span><span class="sxs-lookup"><span data-stu-id="df90b-102">Method-Based Query Syntax Examples: Conversion</span></span>
<span data-ttu-id="df90b-103">本主題中的範例將示範如何使用<xref:System.Linq.Enumerable.ToArray%2A>，<xref:System.Linq.Enumerable.ToDictionary%2A>和<xref:System.Linq.Enumerable.ToList%2A>方法來查詢[AdventureWorks Sales Model](http://msdn.microsoft.com/en-us/f16cd988-673f-4376-b034-129ca93c7832)使用以方法為基礎的查詢語法。</span><span class="sxs-lookup"><span data-stu-id="df90b-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.ToArray%2A>, <xref:System.Linq.Enumerable.ToDictionary%2A> and <xref:System.Linq.Enumerable.ToList%2A> methods to query the [AdventureWorks Sales Model](http://msdn.microsoft.com/en-us/f16cd988-673f-4376-b034-129ca93c7832) using method-based query syntax.</span></span> <span data-ttu-id="df90b-104">這些範例中使用的 AdventureWorks Sales Model 是從 AdventureWorks 範例資料庫中的 Contact、Address、Product、SalesOrderHeader 和 SalesOrderDetail 資料表所建立。</span><span class="sxs-lookup"><span data-stu-id="df90b-104">The AdventureWorks Sales Model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="df90b-105">本主題中的範例使用下列`using` / `Imports`陳述式：</span><span class="sxs-lookup"><span data-stu-id="df90b-105">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="toarray"></a><span data-ttu-id="df90b-106">ToArray</span><span class="sxs-lookup"><span data-stu-id="df90b-106">ToArray</span></span>  
  
### <a name="example"></a><span data-ttu-id="df90b-107">範例</span><span class="sxs-lookup"><span data-stu-id="df90b-107">Example</span></span>  
 <span data-ttu-id="df90b-108">以下範例使用 <xref:System.Linq.Enumerable.ToArray%2A> 方法將序列立即評估為陣列。</span><span class="sxs-lookup"><span data-stu-id="df90b-108">The following example uses the <xref:System.Linq.Enumerable.ToArray%2A> method to immediately evaluate a sequence into an array.</span></span>  
  
 [!code-csharp[DP L2E Examples#ToArray](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#toarray)]
 [!code-vb[DP L2E Examples#ToArray](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#toarray)]  
  
## <a name="todictionary"></a><span data-ttu-id="df90b-109">ToDictionary</span><span class="sxs-lookup"><span data-stu-id="df90b-109">ToDictionary</span></span>  
  
### <a name="example"></a><span data-ttu-id="df90b-110">範例</span><span class="sxs-lookup"><span data-stu-id="df90b-110">Example</span></span>  
 <span data-ttu-id="df90b-111">下列範例會使用 <xref:System.Linq.Enumerable.ToDictionary%2A> 方法，立即將序列和相關的索引鍵運算式評估為字典。</span><span class="sxs-lookup"><span data-stu-id="df90b-111">The following example uses the <xref:System.Linq.Enumerable.ToDictionary%2A> method to immediately evaluate a sequence and a related key expression into a dictionary.</span></span>  
  
 [!code-csharp[DP L2E Examples#ToDictionary](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#todictionary)]
 [!code-vb[DP L2E Examples#ToDictionary](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#todictionary)]  
  
## <a name="tolist"></a><span data-ttu-id="df90b-112">ToList</span><span class="sxs-lookup"><span data-stu-id="df90b-112">ToList</span></span>  
  
### <a name="example"></a><span data-ttu-id="df90b-113">範例</span><span class="sxs-lookup"><span data-stu-id="df90b-113">Example</span></span>  
 <span data-ttu-id="df90b-114">下列範例會使用 <xref:System.Linq.Enumerable.ToList%2A> 方法，立即將序列評估為 <xref:System.Collections.Generic.List%601>，其中 `T` 的型別為 <xref:System.Data.DataRow>。</span><span class="sxs-lookup"><span data-stu-id="df90b-114">The following example uses the <xref:System.Linq.Enumerable.ToList%2A> method to immediately evaluate a sequence into a <xref:System.Collections.Generic.List%601>, where `T` is of type <xref:System.Data.DataRow>.</span></span>  
  
 [!code-csharp[DP L2E Examples#ToList](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#tolist)]
 [!code-vb[DP L2E Examples#ToList](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#tolist)]  
  
## <a name="see-also"></a><span data-ttu-id="df90b-115">請參閱</span><span class="sxs-lookup"><span data-stu-id="df90b-115">See Also</span></span>  
 [<span data-ttu-id="df90b-116">LINQ to Entities 中的查詢</span><span class="sxs-lookup"><span data-stu-id="df90b-116">Queries in LINQ to Entities</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)
