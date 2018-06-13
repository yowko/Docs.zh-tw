---
title: 如何：偵測和解決發生衝突的提交內容
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 91e27206-01fb-4c7a-8afc-1383a6ac5067
ms.openlocfilehash: dfe1fac4285b915c316fb70d1e3bd1e7b99f145a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33354390"
---
# <a name="how-to-detect-and-resolve-conflicting-submissions"></a><span data-ttu-id="772d1-102">如何：偵測和解決發生衝突的提交內容</span><span class="sxs-lookup"><span data-stu-id="772d1-102">How to: Detect and Resolve Conflicting Submissions</span></span>
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="772d1-103"> 提供了許多資源，以便偵測和解決多位使用者變更資料庫所造成的衝突。</span><span class="sxs-lookup"><span data-stu-id="772d1-103"> provides many resources for detecting and resolving conflicts that stem from multi-user changes to the database.</span></span> <span data-ttu-id="772d1-104">如需詳細資訊，請參閱[如何： 管理變更衝突](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)。</span><span class="sxs-lookup"><span data-stu-id="772d1-104">For more information, see [How to: Manage Change Conflicts](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="772d1-105">範例</span><span class="sxs-lookup"><span data-stu-id="772d1-105">Example</span></span>  
 <span data-ttu-id="772d1-106">下列範例所示`try` / `catch`區塊攔截<xref:System.Data.Linq.ChangeConflictException>例外狀況。</span><span class="sxs-lookup"><span data-stu-id="772d1-106">The following example shows a `try`/`catch` block that catches a <xref:System.Data.Linq.ChangeConflictException> exception.</span></span> <span data-ttu-id="772d1-107">主控台視窗中會顯示每個衝突的實體和成員資訊。</span><span class="sxs-lookup"><span data-stu-id="772d1-107">Entity and member information for each conflict is displayed in the console window.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="772d1-108">您必須納入 `using System.Reflection` 指示詞 (在 Visual Basic 中為 `Imports System.Reflection`)，才能支援資訊擷取。</span><span class="sxs-lookup"><span data-stu-id="772d1-108">You must include the `using System.Reflection` directive (`Imports System.Reflection` in Visual Basic) to support the information retrieval.</span></span> <span data-ttu-id="772d1-109">如需詳細資訊，請參閱<xref:System.Reflection>。</span><span class="sxs-lookup"><span data-stu-id="772d1-109">For more information, see <xref:System.Reflection>.</span></span>  
  
 [!code-csharp[DLinqSubmittingChanges#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSubmittingChanges/cs/Program.cs#2)]
 [!code-vb[DLinqSubmittingChanges#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSubmittingChanges/vb/Module1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="772d1-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="772d1-110">See Also</span></span>  
 [<span data-ttu-id="772d1-111">變更和提交資料</span><span class="sxs-lookup"><span data-stu-id="772d1-111">Making and Submitting Data Changes</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/making-and-submitting-data-changes.md)  
 [<span data-ttu-id="772d1-112">如何：管理變更衝突</span><span class="sxs-lookup"><span data-stu-id="772d1-112">How to: Manage Change Conflicts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)
