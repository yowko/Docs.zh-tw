---
title: HOW TO：使用異動括住提交的資料
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 94044a31-de90-479b-935a-8159b4ae5c5a
ms.openlocfilehash: 3e58c6f2849ed9714b3356662dae313ab9d11696
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59134000"
---
# <a name="how-to-bracket-data-submissions-by-using-transactions"></a><span data-ttu-id="9c803-102">HOW TO：使用異動括住提交的資料</span><span class="sxs-lookup"><span data-stu-id="9c803-102">How to: Bracket Data Submissions by Using Transactions</span></span>
<span data-ttu-id="9c803-103">您可以使用 <xref:System.Transactions.TransactionScope> 來括住資料庫提交。</span><span class="sxs-lookup"><span data-stu-id="9c803-103">You can use <xref:System.Transactions.TransactionScope> to bracket your submissions to the database.</span></span> <span data-ttu-id="9c803-104">如需詳細資訊，請參閱 <<c0> [ 交易支援](../../../../../../docs/framework/data/adonet/sql/linq/transaction-support.md)。</span><span class="sxs-lookup"><span data-stu-id="9c803-104">For more information, see [Transaction Support](../../../../../../docs/framework/data/adonet/sql/linq/transaction-support.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="9c803-105">範例</span><span class="sxs-lookup"><span data-stu-id="9c803-105">Example</span></span>  
 <span data-ttu-id="9c803-106">下列程式碼會將資料庫提交封入 <xref:System.Transactions.TransactionScope> 中。</span><span class="sxs-lookup"><span data-stu-id="9c803-106">The following code encloses the database submission in a <xref:System.Transactions.TransactionScope>.</span></span>  
  
 [!code-csharp[DLinqSubmittingChanges#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSubmittingChanges/cs/Program.cs#3)]
 [!code-vb[DLinqSubmittingChanges#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSubmittingChanges/vb/Module1.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="9c803-107">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9c803-107">See also</span></span>

- [<span data-ttu-id="9c803-108">下載範例資料庫</span><span class="sxs-lookup"><span data-stu-id="9c803-108">Downloading Sample Databases</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)
- [<span data-ttu-id="9c803-109">變更和提交資料</span><span class="sxs-lookup"><span data-stu-id="9c803-109">Making and Submitting Data Changes</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/making-and-submitting-data-changes.md)
- [<span data-ttu-id="9c803-110">異動支援</span><span class="sxs-lookup"><span data-stu-id="9c803-110">Transaction Support</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/transaction-support.md)
