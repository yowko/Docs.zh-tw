---
title: "查詢運算式語法範例：項目運算子"
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
ms.assetid: 32268fe2-de18-4065-8060-f250def83837
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 9d919af04c3c8d75be5f4d4571cff719f899d433
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="query-expression-syntax-examples-element-operators"></a><span data-ttu-id="51967-102">查詢運算式語法範例：項目運算子</span><span class="sxs-lookup"><span data-stu-id="51967-102">Query Expression Syntax Examples: Element Operators</span></span>
<span data-ttu-id="51967-103">本主題中的範例將示範如何使用<xref:System.Linq.Enumerable.First%2A>方法來查詢[AdventureWorks Sales Model](http://msdn.microsoft.com/en-us/f16cd988-673f-4376-b034-129ca93c7832)搭配查詢運算式語法。</span><span class="sxs-lookup"><span data-stu-id="51967-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.First%2A> method to query the [AdventureWorks Sales Model](http://msdn.microsoft.com/en-us/f16cd988-673f-4376-b034-129ca93c7832) using the query expression syntax.</span></span> <span data-ttu-id="51967-104">這些範例中使用的 AdventureWorks Sales Model 是從 AdventureWorks 範例資料庫中的 Contact、Address、Product、SalesOrderHeader 和 SalesOrderDetail 資料表所建立。</span><span class="sxs-lookup"><span data-stu-id="51967-104">The AdventureWorks Sales Model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="51967-105">本主題中的範例使用下列`using` / `Imports`陳述式：</span><span class="sxs-lookup"><span data-stu-id="51967-105">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="first"></a><span data-ttu-id="51967-106">First</span><span class="sxs-lookup"><span data-stu-id="51967-106">First</span></span>  
  
### <a name="example"></a><span data-ttu-id="51967-107">範例</span><span class="sxs-lookup"><span data-stu-id="51967-107">Example</span></span>  
 <span data-ttu-id="51967-108">下列範例會使用 <xref:System.Linq.Enumerable.First%2A> 方法來傳回名字為 "Brooke" 的第一位連絡人。</span><span class="sxs-lookup"><span data-stu-id="51967-108">The following example uses the <xref:System.Linq.Enumerable.First%2A> method to return the first contact whose first name is "Brooke".</span></span>  
  
 [!code-csharp[DP L2E Examples#FirstSimple](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#firstsimple)]
 [!code-vb[DP L2E Examples#FirstSimple](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#firstsimple)]  
  
## <a name="see-also"></a><span data-ttu-id="51967-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="51967-109">See Also</span></span>  
 [<span data-ttu-id="51967-110">LINQ to Entities 中的查詢</span><span class="sxs-lookup"><span data-stu-id="51967-110">Queries in LINQ to Entities</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)
