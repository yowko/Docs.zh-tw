---
title: "傳回兩個序列之間的集合差異"
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
ms.assetid: 62efb546-c898-408f-af21-36e7c6fed217
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 7156e6a60527f4fd33e9b8d56504b4697152261e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="return-the-set-difference-between-two-sequences"></a><span data-ttu-id="11a5c-102">傳回兩個序列之間的集合差異</span><span class="sxs-lookup"><span data-stu-id="11a5c-102">Return the Set Difference Between Two Sequences</span></span>
<span data-ttu-id="11a5c-103">使用 <xref:System.Linq.Queryable.Except%2A> 運算子傳回兩個序列之間的集合差異。</span><span class="sxs-lookup"><span data-stu-id="11a5c-103">Use the <xref:System.Linq.Queryable.Except%2A> operator to return the set difference between two sequences.</span></span>  
  
## <a name="example"></a><span data-ttu-id="11a5c-104">範例</span><span class="sxs-lookup"><span data-stu-id="11a5c-104">Example</span></span>  
 <span data-ttu-id="11a5c-105">這個範例會使用 <xref:System.Linq.Queryable.Except%2A> 傳回有 `Customers` 居住但無 `Employees` 居住的所有國家 (地區) 序列。</span><span class="sxs-lookup"><span data-stu-id="11a5c-105">This example uses <xref:System.Linq.Queryable.Except%2A> to return a sequence of all countries in which `Customers` live but in which no `Employees` live.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#41](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#41)]
 [!code-vb[DLinqQueryExamples#41](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#41)]  
  
 <span data-ttu-id="11a5c-106">在 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 中，<xref:System.Linq.Queryable.Except%2A> 作業僅妥善定義於集合上。</span><span class="sxs-lookup"><span data-stu-id="11a5c-106">In [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], the <xref:System.Linq.Queryable.Except%2A> operation is well defined only on sets.</span></span> <span data-ttu-id="11a5c-107">尚未定義多重集 (Multiset) 的語意 (Semantics)。</span><span class="sxs-lookup"><span data-stu-id="11a5c-107">The semantics for multisets is undefined.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="11a5c-108">請參閱</span><span class="sxs-lookup"><span data-stu-id="11a5c-108">See Also</span></span>  
 [<span data-ttu-id="11a5c-109">查詢範例</span><span class="sxs-lookup"><span data-stu-id="11a5c-109">Query Examples</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)  
 [<span data-ttu-id="11a5c-110">標準查詢運算子轉譯</span><span class="sxs-lookup"><span data-stu-id="11a5c-110">Standard Query Operator Translation</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/standard-query-operator-translation.md)
