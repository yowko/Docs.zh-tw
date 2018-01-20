---
title: "以方法為基礎的查詢語法範例：項目運算子"
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
ms.assetid: 8438b995-bd07-4223-b22d-13adadef33fb
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: b1a5cda6597940bbf99f50c325532d8b50fad5f0
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/19/2018
---
# <a name="method-based-query-syntax-examples-element-operators"></a><span data-ttu-id="b2a3d-102">以方法為基礎的查詢語法範例：項目運算子</span><span class="sxs-lookup"><span data-stu-id="b2a3d-102">Method-Based Query Syntax Examples: Element Operators</span></span>
<span data-ttu-id="b2a3d-103">本主題中的範例將示範如何使用<xref:System.Linq.Enumerable.First%2A>方法來查詢[AdventureWorks Sales Model](http://msdn.microsoft.com/library/f16cd988-673f-4376-b034-129ca93c7832)使用以方法為基礎的查詢語法。</span><span class="sxs-lookup"><span data-stu-id="b2a3d-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.First%2A> method to query the [AdventureWorks Sales Model](http://msdn.microsoft.com/library/f16cd988-673f-4376-b034-129ca93c7832) using method-based query syntax.</span></span> <span data-ttu-id="b2a3d-104">這些範例中使用的 AdventureWorks Sales Model 是從 AdventureWorks 範例資料庫中的 Contact、Address、Product、SalesOrderHeader 和 SalesOrderDetail 資料表所建立。</span><span class="sxs-lookup"><span data-stu-id="b2a3d-104">The AdventureWorks Sales Model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="b2a3d-105">本主題中的範例使用下列`using` / `Imports`陳述式：</span><span class="sxs-lookup"><span data-stu-id="b2a3d-105">The example in this topic uses the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="first"></a><span data-ttu-id="b2a3d-106">First</span><span class="sxs-lookup"><span data-stu-id="b2a3d-106">First</span></span>  
  
### <a name="example"></a><span data-ttu-id="b2a3d-107">範例</span><span class="sxs-lookup"><span data-stu-id="b2a3d-107">Example</span></span>  
 <span data-ttu-id="b2a3d-108">下列範例會使用 <xref:System.Linq.Enumerable.First%2A> 方法來尋找以 'caroline' 開頭的第一筆電子郵件地址。</span><span class="sxs-lookup"><span data-stu-id="b2a3d-108">The following example uses the <xref:System.Linq.Enumerable.First%2A> method to find the first e-mail address that starts with 'caroline'.</span></span>  
  
 [!code-csharp[DP L2E Examples#FirstCondition_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#firstcondition_mq)]
 [!code-vb[DP L2E Examples#FirstCondition_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#firstcondition_mq)]  
  
## <a name="see-also"></a><span data-ttu-id="b2a3d-109">請參閱</span><span class="sxs-lookup"><span data-stu-id="b2a3d-109">See Also</span></span>  
 [<span data-ttu-id="b2a3d-110">LINQ to Entities 中的查詢</span><span class="sxs-lookup"><span data-stu-id="b2a3d-110">Queries in LINQ to Entities</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)
