---
title: 查詢運算式語法範例：項目運算子
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 32268fe2-de18-4065-8060-f250def83837
ms.openlocfilehash: 36823b02d581b47493950b6393bda323b2e8f9b7
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2018
ms.locfileid: "43749180"
---
# <a name="query-expression-syntax-examples-element-operators"></a><span data-ttu-id="a1cc6-102">查詢運算式語法範例：項目運算子</span><span class="sxs-lookup"><span data-stu-id="a1cc6-102">Query Expression Syntax Examples: Element Operators</span></span>
<span data-ttu-id="a1cc6-103">本主題中的範例將示範如何使用<xref:System.Linq.Enumerable.First%2A>方法來查詢[AdventureWorks Sales Model](https://msdn.microsoft.com/library/f16cd988-673f-4376-b034-129ca93c7832)搭配查詢運算式語法。</span><span class="sxs-lookup"><span data-stu-id="a1cc6-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.First%2A> method to query the [AdventureWorks Sales Model](https://msdn.microsoft.com/library/f16cd988-673f-4376-b034-129ca93c7832) using the query expression syntax.</span></span> <span data-ttu-id="a1cc6-104">這些範例中使用的 AdventureWorks Sales Model 是從 AdventureWorks 範例資料庫中的 Contact、Address、Product、SalesOrderHeader 和 SalesOrderDetail 資料表所建立。</span><span class="sxs-lookup"><span data-stu-id="a1cc6-104">The AdventureWorks Sales Model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="a1cc6-105">本主題中的範例使用下列`using` / `Imports`陳述式：</span><span class="sxs-lookup"><span data-stu-id="a1cc6-105">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="first"></a><span data-ttu-id="a1cc6-106">First</span><span class="sxs-lookup"><span data-stu-id="a1cc6-106">First</span></span>  
  
### <a name="example"></a><span data-ttu-id="a1cc6-107">範例</span><span class="sxs-lookup"><span data-stu-id="a1cc6-107">Example</span></span>  
 <span data-ttu-id="a1cc6-108">下列範例會使用 <xref:System.Linq.Enumerable.First%2A> 方法來傳回名字為 "Brooke" 的第一位連絡人。</span><span class="sxs-lookup"><span data-stu-id="a1cc6-108">The following example uses the <xref:System.Linq.Enumerable.First%2A> method to return the first contact whose first name is "Brooke".</span></span>  
  
 [!code-csharp[DP L2E Examples#FirstSimple](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#firstsimple)]
 [!code-vb[DP L2E Examples#FirstSimple](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#firstsimple)]  
  
## <a name="see-also"></a><span data-ttu-id="a1cc6-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a1cc6-109">See Also</span></span>  
 [<span data-ttu-id="a1cc6-110">LINQ to Entities 中的查詢</span><span class="sxs-lookup"><span data-stu-id="a1cc6-110">Queries in LINQ to Entities</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)
