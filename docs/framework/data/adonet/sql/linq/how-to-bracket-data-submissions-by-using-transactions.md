---
title: "如何：使用異動括住提交的資料"
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
ms.assetid: 94044a31-de90-479b-935a-8159b4ae5c5a
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 3481bcae3c67d08dc372195b6dba65c6b506b7f3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-bracket-data-submissions-by-using-transactions"></a><span data-ttu-id="32644-102">如何：使用異動括住提交的資料</span><span class="sxs-lookup"><span data-stu-id="32644-102">How to: Bracket Data Submissions by Using Transactions</span></span>
<span data-ttu-id="32644-103">您可以使用 <xref:System.Transactions.TransactionScope> 來括住資料庫提交。</span><span class="sxs-lookup"><span data-stu-id="32644-103">You can use <xref:System.Transactions.TransactionScope> to bracket your submissions to the database.</span></span> <span data-ttu-id="32644-104">如需詳細資訊，請參閱[交易支援](../../../../../../docs/framework/data/adonet/sql/linq/transaction-support.md)。</span><span class="sxs-lookup"><span data-stu-id="32644-104">For more information, see [Transaction Support](../../../../../../docs/framework/data/adonet/sql/linq/transaction-support.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="32644-105">範例</span><span class="sxs-lookup"><span data-stu-id="32644-105">Example</span></span>  
 <span data-ttu-id="32644-106">下列程式碼會將資料庫提交封入 <xref:System.Transactions.TransactionScope> 中。</span><span class="sxs-lookup"><span data-stu-id="32644-106">The following code encloses the database submission in a <xref:System.Transactions.TransactionScope>.</span></span>  
  
 [!code-csharp[DLinqSubmittingChanges#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSubmittingChanges/cs/Program.cs#3)]
 [!code-vb[DLinqSubmittingChanges#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSubmittingChanges/vb/Module1.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="32644-107">請參閱</span><span class="sxs-lookup"><span data-stu-id="32644-107">See Also</span></span>  
 [<span data-ttu-id="32644-108">下載範例資料庫</span><span class="sxs-lookup"><span data-stu-id="32644-108">Downloading Sample Databases</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)  
 [<span data-ttu-id="32644-109">變更和提交資料</span><span class="sxs-lookup"><span data-stu-id="32644-109">Making and Submitting Data Changes</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/making-and-submitting-data-changes.md)  
 [<span data-ttu-id="32644-110">異動支援</span><span class="sxs-lookup"><span data-stu-id="32644-110">Transaction Support</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/transaction-support.md)
