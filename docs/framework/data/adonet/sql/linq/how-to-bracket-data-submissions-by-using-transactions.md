---
title: 作法：使用異動括住提交的資料
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 94044a31-de90-479b-935a-8159b4ae5c5a
ms.openlocfilehash: 6a4c5ba7c4938b48fe489e43ff4a3ff806bd8916
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70793813"
---
# <a name="how-to-bracket-data-submissions-by-using-transactions"></a><span data-ttu-id="0cca2-102">作法：使用異動括住提交的資料</span><span class="sxs-lookup"><span data-stu-id="0cca2-102">How to: Bracket Data Submissions by Using Transactions</span></span>
<span data-ttu-id="0cca2-103">您可以使用 <xref:System.Transactions.TransactionScope> 來括住資料庫提交。</span><span class="sxs-lookup"><span data-stu-id="0cca2-103">You can use <xref:System.Transactions.TransactionScope> to bracket your submissions to the database.</span></span> <span data-ttu-id="0cca2-104">如需詳細資訊，請參閱[交易支援](transaction-support.md)。</span><span class="sxs-lookup"><span data-stu-id="0cca2-104">For more information, see [Transaction Support](transaction-support.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="0cca2-105">範例</span><span class="sxs-lookup"><span data-stu-id="0cca2-105">Example</span></span>  
 <span data-ttu-id="0cca2-106">下列程式碼會將資料庫提交封入 <xref:System.Transactions.TransactionScope> 中。</span><span class="sxs-lookup"><span data-stu-id="0cca2-106">The following code encloses the database submission in a <xref:System.Transactions.TransactionScope>.</span></span>  
  
 [!code-csharp[DLinqSubmittingChanges#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSubmittingChanges/cs/Program.cs#3)]
 [!code-vb[DLinqSubmittingChanges#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSubmittingChanges/vb/Module1.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="0cca2-107">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0cca2-107">See also</span></span>

- [<span data-ttu-id="0cca2-108">下載範例資料庫</span><span class="sxs-lookup"><span data-stu-id="0cca2-108">Downloading Sample Databases</span></span>](downloading-sample-databases.md)
- [<span data-ttu-id="0cca2-109">變更和提交資料</span><span class="sxs-lookup"><span data-stu-id="0cca2-109">Making and Submitting Data Changes</span></span>](making-and-submitting-data-changes.md)
- [<span data-ttu-id="0cca2-110">異動支援</span><span class="sxs-lookup"><span data-stu-id="0cca2-110">Transaction Support</span></span>](transaction-support.md)
