---
title: 作法：擷取實體衝突資訊
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 9a02b608-e7bb-4041-a452-a7fed26fd008
ms.openlocfilehash: e8c548ac632454d9c488ebd5f7b471f6759418fb
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91155870"
---
# <a name="how-to-retrieve-entity-conflict-information"></a><span data-ttu-id="b6d6c-102">作法：擷取實體衝突資訊</span><span class="sxs-lookup"><span data-stu-id="b6d6c-102">How to: Retrieve Entity Conflict Information</span></span>

<span data-ttu-id="b6d6c-103">您可以使用 <xref:System.Data.Linq.ObjectChangeConflict> 類別的物件，提供有關 <xref:System.Data.Linq.ChangeConflictException> 例外狀況所揭露的衝突資訊。</span><span class="sxs-lookup"><span data-stu-id="b6d6c-103">You can use objects of the <xref:System.Data.Linq.ObjectChangeConflict> class to provide information about conflicts revealed by <xref:System.Data.Linq.ChangeConflictException> exceptions.</span></span> <span data-ttu-id="b6d6c-104">如需詳細資訊，請參閱 [開放式平行存取：總覽](optimistic-concurrency-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="b6d6c-104">For more information, see [Optimistic Concurrency: Overview](optimistic-concurrency-overview.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="b6d6c-105">範例</span><span class="sxs-lookup"><span data-stu-id="b6d6c-105">Example</span></span>  

 <span data-ttu-id="b6d6c-106">下列範例會逐一查看累積衝突的清單。</span><span class="sxs-lookup"><span data-stu-id="b6d6c-106">The following example iterates through a list of accumulated conflicts.</span></span>  
  
 [!code-csharp[System.Data.Linq.ObjectChangeConflict#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.objectchangeconflict/cs/program.cs#1)]
 [!code-vb[System.Data.Linq.ObjectChangeConflict#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.objectchangeconflict/vb/module1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="b6d6c-107">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b6d6c-107">See also</span></span>

- [<span data-ttu-id="b6d6c-108">作法：管理變更衝突</span><span class="sxs-lookup"><span data-stu-id="b6d6c-108">How to: Manage Change Conflicts</span></span>](how-to-manage-change-conflicts.md)
