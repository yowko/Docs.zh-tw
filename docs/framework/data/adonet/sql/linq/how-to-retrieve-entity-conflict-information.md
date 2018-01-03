---
title: "如何：擷取實體衝突資訊"
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
ms.assetid: 9a02b608-e7bb-4041-a452-a7fed26fd008
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: e43ca054477b75b5737a8ef8f05fc1874d870ac5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-retrieve-entity-conflict-information"></a><span data-ttu-id="acf25-102">如何：擷取實體衝突資訊</span><span class="sxs-lookup"><span data-stu-id="acf25-102">How to: Retrieve Entity Conflict Information</span></span>
<span data-ttu-id="acf25-103">您可以使用 <xref:System.Data.Linq.ObjectChangeConflict> 類別的物件，提供有關 <xref:System.Data.Linq.ChangeConflictException> 例外狀況所揭露的衝突資訊。</span><span class="sxs-lookup"><span data-stu-id="acf25-103">You can use objects of the <xref:System.Data.Linq.ObjectChangeConflict> class to provide information about conflicts revealed by <xref:System.Data.Linq.ChangeConflictException> exceptions.</span></span> <span data-ttu-id="acf25-104">如需詳細資訊，請參閱[開放式並行存取： 概觀](../../../../../../docs/framework/data/adonet/sql/linq/optimistic-concurrency-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="acf25-104">For more information, see [Optimistic Concurrency: Overview](../../../../../../docs/framework/data/adonet/sql/linq/optimistic-concurrency-overview.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="acf25-105">範例</span><span class="sxs-lookup"><span data-stu-id="acf25-105">Example</span></span>  
 <span data-ttu-id="acf25-106">下列範例會逐一查看累積衝突的清單。</span><span class="sxs-lookup"><span data-stu-id="acf25-106">The following example iterates through a list of accumulated conflicts.</span></span>  
  
 [!code-csharp[System.Data.Linq.ObjectChangeConflict#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.objectchangeconflict/cs/program.cs#1)]
 [!code-vb[System.Data.Linq.ObjectChangeConflict#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.objectchangeconflict/vb/module1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="acf25-107">請參閱</span><span class="sxs-lookup"><span data-stu-id="acf25-107">See Also</span></span>  
 [<span data-ttu-id="acf25-108">如何：管理變更衝突</span><span class="sxs-lookup"><span data-stu-id="acf25-108">How to: Manage Change Conflicts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)
