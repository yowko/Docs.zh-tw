---
title: HOW TO：篩選相關的資料
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ec8b8f97-5d01-4f31-9b97-d1556df6a4bc
ms.openlocfilehash: 9a046c94363a1a161e19dcb68e015f8c6791e511
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54703467"
---
# <a name="how-to-filter-related-data"></a><span data-ttu-id="18cd1-102">HOW TO：篩選相關的資料</span><span class="sxs-lookup"><span data-stu-id="18cd1-102">How to: Filter Related Data</span></span>
<span data-ttu-id="18cd1-103">使用 <xref:System.Data.Linq.DataLoadOptions.AssociateWith%2A> 方法，可指定子查詢限制所擷取的資料量。</span><span class="sxs-lookup"><span data-stu-id="18cd1-103">Use the <xref:System.Data.Linq.DataLoadOptions.AssociateWith%2A> method to specify sub-queries to limit the amount of retrieved data.</span></span>  
  
## <a name="example"></a><span data-ttu-id="18cd1-104">範例</span><span class="sxs-lookup"><span data-stu-id="18cd1-104">Example</span></span>  
 <span data-ttu-id="18cd1-105">在下列範例中，<xref:System.Data.Linq.DataLoadOptions.AssociateWith%2A> 方法會將所擷取的 `Orders` 限制為今天尚未運送的訂單。</span><span class="sxs-lookup"><span data-stu-id="18cd1-105">In the following example, the <xref:System.Data.Linq.DataLoadOptions.AssociateWith%2A> method limits the `Orders` retrieved to those that have not been shipped today.</span></span> <span data-ttu-id="18cd1-106">若不使用這種方法，則即使只需要某個子集，仍然會擷取所有 `Orders`。</span><span class="sxs-lookup"><span data-stu-id="18cd1-106">Without this approach, all `Orders` would have been retrieved even though only a subset is desired.</span></span>  
  
 [!code-csharp[System.Data.Linq.DataLoadOptions#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.dataloadoptions/cs/program.cs#1)]
 [!code-vb[System.Data.Linq.DataLoadOptions#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.dataloadoptions/vb/module1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="18cd1-107">另請參閱</span><span class="sxs-lookup"><span data-stu-id="18cd1-107">See also</span></span>
- [<span data-ttu-id="18cd1-108">查詢資料庫</span><span class="sxs-lookup"><span data-stu-id="18cd1-108">Querying the Database</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/querying-the-database.md)
