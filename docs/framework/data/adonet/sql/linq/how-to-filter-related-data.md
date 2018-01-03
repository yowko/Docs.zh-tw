---
title: "如何：篩選相關資料"
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
ms.assetid: ec8b8f97-5d01-4f31-9b97-d1556df6a4bc
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 9d51ac97611379cc6c47ef698bc635bbf46d1e5f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-filter-related-data"></a><span data-ttu-id="60b43-102">如何：篩選相關資料</span><span class="sxs-lookup"><span data-stu-id="60b43-102">How to: Filter Related Data</span></span>
<span data-ttu-id="60b43-103">使用 <xref:System.Data.Linq.DataLoadOptions.AssociateWith%2A> 方法，可指定子查詢限制所擷取的資料量。</span><span class="sxs-lookup"><span data-stu-id="60b43-103">Use the <xref:System.Data.Linq.DataLoadOptions.AssociateWith%2A> method to specify sub-queries to limit the amount of retrieved data.</span></span>  
  
## <a name="example"></a><span data-ttu-id="60b43-104">範例</span><span class="sxs-lookup"><span data-stu-id="60b43-104">Example</span></span>  
 <span data-ttu-id="60b43-105">在下列範例中，<xref:System.Data.Linq.DataLoadOptions.AssociateWith%2A> 方法會將所擷取的 `Orders` 限制為今天尚未運送的訂單。</span><span class="sxs-lookup"><span data-stu-id="60b43-105">In the following example, the <xref:System.Data.Linq.DataLoadOptions.AssociateWith%2A> method limits the `Orders` retrieved to those that have not been shipped today.</span></span> <span data-ttu-id="60b43-106">若不使用這種方法，則即使只需要某個子集，仍然會擷取所有 `Orders`。</span><span class="sxs-lookup"><span data-stu-id="60b43-106">Without this approach, all `Orders` would have been retrieved even though only a subset is desired.</span></span>  
  
 [!code-csharp[System.Data.Linq.DataLoadOptions#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.dataloadoptions/cs/program.cs#1)]
 [!code-vb[System.Data.Linq.DataLoadOptions#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.dataloadoptions/vb/module1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="60b43-107">請參閱</span><span class="sxs-lookup"><span data-stu-id="60b43-107">See Also</span></span>  
 [<span data-ttu-id="60b43-108">查詢資料庫</span><span class="sxs-lookup"><span data-stu-id="60b43-108">Querying the Database</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/querying-the-database.md)
