---
title: 如何：指定並行衝突檢查
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c2547fcb-58eb-4377-9948-1b8d76a0f3d7
ms.openlocfilehash: c7e4297f90174255f5df1e2a8b0b100b168abb08
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33362588"
---
# <a name="how-to-specify-concurrency-conflict-checking"></a><span data-ttu-id="b8ad9-102">如何：指定並行衝突檢查</span><span class="sxs-lookup"><span data-stu-id="b8ad9-102">How to: Specify Concurrency-Conflict Checking</span></span>
<span data-ttu-id="b8ad9-103">您可以指定在呼叫 <xref:System.Data.Linq.DataContext.SubmitChanges%2A> 時要檢查並行存取衝突的資料庫資料行。</span><span class="sxs-lookup"><span data-stu-id="b8ad9-103">You can specify which columns of the database are to be checked for concurrency conflicts when you call <xref:System.Data.Linq.DataContext.SubmitChanges%2A>.</span></span> <span data-ttu-id="b8ad9-104">如需詳細資訊，請參閱[How to： 指定的成員會用於測試並行衝突](../../../../../../docs/framework/data/adonet/sql/linq/how-to-specify-which-members-are-tested-for-concurrency-conflicts.md)。</span><span class="sxs-lookup"><span data-stu-id="b8ad9-104">For more information, see [How to: Specify Which Members are Tested for Concurrency Conflicts](../../../../../../docs/framework/data/adonet/sql/linq/how-to-specify-which-members-are-tested-for-concurrency-conflicts.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="b8ad9-105">範例</span><span class="sxs-lookup"><span data-stu-id="b8ad9-105">Example</span></span>  
 <span data-ttu-id="b8ad9-106">下列程式碼指定 `HomePage` 成員永遠不應該在更新檢查期間進行測試。</span><span class="sxs-lookup"><span data-stu-id="b8ad9-106">The following code specifies that the `HomePage` member should never be tested during update checks.</span></span> <span data-ttu-id="b8ad9-107">如需詳細資訊，請參閱<xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A>。</span><span class="sxs-lookup"><span data-stu-id="b8ad9-107">For more information, see <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A>.</span></span>  
  
 [!code-csharp[System.Data.Linq.Mapping.UpdateCheck#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.mapping.updatecheck/cs/northwind.cs#1)]
 [!code-vb[System.Data.Linq.Mapping.UpdateCheck#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.mapping.updatecheck/vb/northwind.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="b8ad9-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b8ad9-108">See Also</span></span>  
 [<span data-ttu-id="b8ad9-109">LINQ to SQL 物件模型</span><span class="sxs-lookup"><span data-stu-id="b8ad9-109">The LINQ to SQL Object Model</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)  
 [<span data-ttu-id="b8ad9-110">如何：使用程式碼編輯器自訂實體類別</span><span class="sxs-lookup"><span data-stu-id="b8ad9-110">How to: Customize Entity Classes by Using the Code Editor</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)
