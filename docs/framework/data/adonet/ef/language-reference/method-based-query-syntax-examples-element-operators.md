---
title: 以方法為基礎的查詢語法範例：項目運算子
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8438b995-bd07-4223-b22d-13adadef33fb
ms.openlocfilehash: 89cbda4d049b30ee50accf94d5b7ec172bc25ae2
ms.sourcegitcommit: 3500c4845f96a91a438a02ef2c6b4eef45a5e2af
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/07/2019
ms.locfileid: "55826495"
---
# <a name="method-based-query-syntax-examples-element-operators"></a><span data-ttu-id="6b492-102">以方法為基礎的查詢語法範例：項目運算子</span><span class="sxs-lookup"><span data-stu-id="6b492-102">Method-Based Query Syntax Examples: Element Operators</span></span>
<span data-ttu-id="6b492-103">本主題中的範例將示範如何使用<xref:System.Linq.Enumerable.First%2A>方法來查詢[AdventureWorks Sales Model](https://archive.codeplex.com/?p=msftdbprodsamples)使用以方法為基礎的查詢語法。</span><span class="sxs-lookup"><span data-stu-id="6b492-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.First%2A> method to query the [AdventureWorks Sales Model](https://archive.codeplex.com/?p=msftdbprodsamples) using method-based query syntax.</span></span> <span data-ttu-id="6b492-104">這些範例中使用的 AdventureWorks Sales Model 是從 AdventureWorks 範例資料庫中的 Contact、Address、Product、SalesOrderHeader 和 SalesOrderDetail 資料表所建立。</span><span class="sxs-lookup"><span data-stu-id="6b492-104">The AdventureWorks Sales Model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="6b492-105">本主題中的範例會使用下列`using` / `Imports`陳述式：</span><span class="sxs-lookup"><span data-stu-id="6b492-105">The example in this topic uses the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="first"></a><span data-ttu-id="6b492-106">First</span><span class="sxs-lookup"><span data-stu-id="6b492-106">First</span></span>  
  
### <a name="example"></a><span data-ttu-id="6b492-107">範例</span><span class="sxs-lookup"><span data-stu-id="6b492-107">Example</span></span>  
 <span data-ttu-id="6b492-108">下列範例會使用<xref:System.Linq.Enumerable.First%2A>方法來尋找開頭的第一個電子郵件地址以 'caroline'。</span><span class="sxs-lookup"><span data-stu-id="6b492-108">The following example uses the <xref:System.Linq.Enumerable.First%2A> method to find the first email address that starts with 'caroline'.</span></span>  
  
 [!code-csharp[DP L2E Examples#FirstCondition_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#firstcondition_mq)]
 [!code-vb[DP L2E Examples#FirstCondition_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#firstcondition_mq)]  
  
## <a name="see-also"></a><span data-ttu-id="6b492-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6b492-109">See also</span></span>
- [<span data-ttu-id="6b492-110">LINQ to Entities 中的查詢</span><span class="sxs-lookup"><span data-stu-id="6b492-110">Queries in LINQ to Entities</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)
