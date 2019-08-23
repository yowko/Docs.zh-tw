---
title: 作法：偵測和解決發生衝突的提交內容
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 91e27206-01fb-4c7a-8afc-1383a6ac5067
ms.openlocfilehash: ff33196f83e2c0d8d759e4ffc3fb7442e8ba0e3b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69940101"
---
# <a name="how-to-detect-and-resolve-conflicting-submissions"></a><span data-ttu-id="0cd70-102">HOW TO：偵測和解決發生衝突的提交內容</span><span class="sxs-lookup"><span data-stu-id="0cd70-102">How to: Detect and Resolve Conflicting Submissions</span></span>
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="0cd70-103">提供了許多資源，以便偵測和解決多位使用者變更資料庫所造成的衝突。</span><span class="sxs-lookup"><span data-stu-id="0cd70-103">provides many resources for detecting and resolving conflicts that stem from multi-user changes to the database.</span></span> <span data-ttu-id="0cd70-104">如需詳細資訊，請參閱[如何：管理變更衝突](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)。</span><span class="sxs-lookup"><span data-stu-id="0cd70-104">For more information, see [How to: Manage Change Conflicts](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="0cd70-105">範例</span><span class="sxs-lookup"><span data-stu-id="0cd70-105">Example</span></span>  
 <span data-ttu-id="0cd70-106">下列`try`範例顯示/ <xref:System.Data.Linq.ChangeConflictException>攔截例外狀況的區塊。`catch`</span><span class="sxs-lookup"><span data-stu-id="0cd70-106">The following example shows a `try`/`catch` block that catches a <xref:System.Data.Linq.ChangeConflictException> exception.</span></span> <span data-ttu-id="0cd70-107">主控台視窗中會顯示每個衝突的實體和成員資訊。</span><span class="sxs-lookup"><span data-stu-id="0cd70-107">Entity and member information for each conflict is displayed in the console window.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0cd70-108">您必須納入 `using System.Reflection` 指示詞 (在 Visual Basic 中為 `Imports System.Reflection`)，才能支援資訊擷取。</span><span class="sxs-lookup"><span data-stu-id="0cd70-108">You must include the `using System.Reflection` directive (`Imports System.Reflection` in Visual Basic) to support the information retrieval.</span></span> <span data-ttu-id="0cd70-109">如需詳細資訊，請參閱 <xref:System.Reflection>。</span><span class="sxs-lookup"><span data-stu-id="0cd70-109">For more information, see <xref:System.Reflection>.</span></span>  
  
 [!code-csharp[DLinqSubmittingChanges#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSubmittingChanges/cs/Program.cs#2)]
 [!code-vb[DLinqSubmittingChanges#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSubmittingChanges/vb/Module1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="0cd70-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0cd70-110">See also</span></span>

- [<span data-ttu-id="0cd70-111">變更和提交資料</span><span class="sxs-lookup"><span data-stu-id="0cd70-111">Making and Submitting Data Changes</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/making-and-submitting-data-changes.md)
- [<span data-ttu-id="0cd70-112">如何：管理變更衝突</span><span class="sxs-lookup"><span data-stu-id="0cd70-112">How to: Manage Change Conflicts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)
