---
title: HOW TO：偵測和解決發生衝突的提交內容
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 91e27206-01fb-4c7a-8afc-1383a6ac5067
ms.openlocfilehash: 2de0182cc0b87768a9cff553b7ec6e77f8ccc7b8
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70793769"
---
# <a name="how-to-detect-and-resolve-conflicting-submissions"></a><span data-ttu-id="e441c-102">作法：偵測和解決發生衝突的提交內容</span><span class="sxs-lookup"><span data-stu-id="e441c-102">How to: Detect and Resolve Conflicting Submissions</span></span>
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="e441c-103">提供了許多資源，以便偵測和解決多位使用者變更資料庫所造成的衝突。</span><span class="sxs-lookup"><span data-stu-id="e441c-103">provides many resources for detecting and resolving conflicts that stem from multi-user changes to the database.</span></span> <span data-ttu-id="e441c-104">如需詳細資訊，請參閱[如何：管理變更衝突](how-to-manage-change-conflicts.md)。</span><span class="sxs-lookup"><span data-stu-id="e441c-104">For more information, see [How to: Manage Change Conflicts](how-to-manage-change-conflicts.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="e441c-105">範例</span><span class="sxs-lookup"><span data-stu-id="e441c-105">Example</span></span>  
 <span data-ttu-id="e441c-106">下列`try`範例顯示/ <xref:System.Data.Linq.ChangeConflictException>攔截例外狀況的區塊。`catch`</span><span class="sxs-lookup"><span data-stu-id="e441c-106">The following example shows a `try`/`catch` block that catches a <xref:System.Data.Linq.ChangeConflictException> exception.</span></span> <span data-ttu-id="e441c-107">主控台視窗中會顯示每個衝突的實體和成員資訊。</span><span class="sxs-lookup"><span data-stu-id="e441c-107">Entity and member information for each conflict is displayed in the console window.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e441c-108">您必須納入 `using System.Reflection` 指示詞 (在 Visual Basic 中為 `Imports System.Reflection`)，才能支援資訊擷取。</span><span class="sxs-lookup"><span data-stu-id="e441c-108">You must include the `using System.Reflection` directive (`Imports System.Reflection` in Visual Basic) to support the information retrieval.</span></span> <span data-ttu-id="e441c-109">如需詳細資訊，請參閱 <xref:System.Reflection>。</span><span class="sxs-lookup"><span data-stu-id="e441c-109">For more information, see <xref:System.Reflection>.</span></span>  
  
 [!code-csharp[DLinqSubmittingChanges#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSubmittingChanges/cs/Program.cs#2)]
 [!code-vb[DLinqSubmittingChanges#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSubmittingChanges/vb/Module1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="e441c-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e441c-110">See also</span></span>

- [<span data-ttu-id="e441c-111">變更和提交資料</span><span class="sxs-lookup"><span data-stu-id="e441c-111">Making and Submitting Data Changes</span></span>](making-and-submitting-data-changes.md)
- [<span data-ttu-id="e441c-112">如何：管理變更衝突</span><span class="sxs-lookup"><span data-stu-id="e441c-112">How to: Manage Change Conflicts</span></span>](how-to-manage-change-conflicts.md)
