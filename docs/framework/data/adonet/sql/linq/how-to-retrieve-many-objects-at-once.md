---
title: "如何：一次擷取多個物件"
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
ms.assetid: 18aff4d8-bde8-461b-9960-ccabb24e9d22
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: f7b9adc9d8bde80a3e888ce873a611f01f69fd9d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-retrieve-many-objects-at-once"></a><span data-ttu-id="b95fd-102">如何：一次擷取多個物件</span><span class="sxs-lookup"><span data-stu-id="b95fd-102">How to: Retrieve Many Objects At Once</span></span>
<span data-ttu-id="b95fd-103">您可以使用 <xref:System.Data.Linq.DataLoadOptions.LoadWith%2A>，在單一查詢中擷取多個物件。</span><span class="sxs-lookup"><span data-stu-id="b95fd-103">You can retrieve many objects in one query by using <xref:System.Data.Linq.DataLoadOptions.LoadWith%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b95fd-104">範例</span><span class="sxs-lookup"><span data-stu-id="b95fd-104">Example</span></span>  
 <span data-ttu-id="b95fd-105">下列程式碼使用 <xref:System.Data.Linq.DataLoadOptions.LoadWith%2A> 方法來擷取 `Customer` 和 `Order` 物件。</span><span class="sxs-lookup"><span data-stu-id="b95fd-105">The following code uses the <xref:System.Data.Linq.DataLoadOptions.LoadWith%2A> method to retrieve both `Customer` and `Order` objects.</span></span>  
  
 [!code-csharp[DLinqQueryConcepts#9](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryConcepts/cs/Program.cs#9)]
 [!code-vb[DLinqQueryConcepts#9](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryConcepts/vb/Module1.vb#9)]  
  
## <a name="see-also"></a><span data-ttu-id="b95fd-106">請參閱</span><span class="sxs-lookup"><span data-stu-id="b95fd-106">See Also</span></span>  
 [<span data-ttu-id="b95fd-107">查詢概念</span><span class="sxs-lookup"><span data-stu-id="b95fd-107">Query Concepts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)
