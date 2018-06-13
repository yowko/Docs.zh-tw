---
title: 如何：使用異動括住提交的資料
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 94044a31-de90-479b-935a-8159b4ae5c5a
ms.openlocfilehash: aa77d364d1ee4efc09386dd7e889914aeb2f3f26
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33361523"
---
# <a name="how-to-bracket-data-submissions-by-using-transactions"></a>如何：使用異動括住提交的資料
您可以使用 <xref:System.Transactions.TransactionScope> 來括住資料庫提交。 如需詳細資訊，請參閱[交易支援](../../../../../../docs/framework/data/adonet/sql/linq/transaction-support.md)。  
  
## <a name="example"></a>範例  
 下列程式碼會將資料庫提交封入 <xref:System.Transactions.TransactionScope> 中。  
  
 [!code-csharp[DLinqSubmittingChanges#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSubmittingChanges/cs/Program.cs#3)]
 [!code-vb[DLinqSubmittingChanges#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSubmittingChanges/vb/Module1.vb#3)]  
  
## <a name="see-also"></a>另請參閱  
 [下載範例資料庫](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)  
 [變更和提交資料](../../../../../../docs/framework/data/adonet/sql/linq/making-and-submitting-data-changes.md)  
 [異動支援](../../../../../../docs/framework/data/adonet/sql/linq/transaction-support.md)
