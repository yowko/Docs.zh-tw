---
title: 異動支援
ms.date: 03/30/2017
ms.assetid: 8cceb26e-8d36-4365-8967-58e2e89e0187
ms.openlocfilehash: 1449f4d10d0feeec47ac17ffda91acb3e0da17ea
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91202197"
---
# <a name="transaction-support"></a>異動支援

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 支援三種不同的交易模型。 以下按照執行檢查的順序列出這些模型。  
  
## <a name="explicit-local-transaction"></a>明確本機異動  

 呼叫 <xref:System.Data.Linq.DataContext.SubmitChanges%2A> 後，如果 <xref:System.Data.Linq.DataContext.Transaction%2A> 屬性已設為 (`IDbTransaction`) 交易，則會在相同交易的情況下執行 <xref:System.Data.Linq.DataContext.SubmitChanges%2A> 呼叫。  
  
 順利執行異動後，您必須負責認可或復原此異動。 對應至此交易的連接必須符合用於建構 <xref:System.Data.Linq.DataContext> 的連接。 如果使用不同的連接，則會擲回例外狀況。  
  
## <a name="explicit-distributable-transaction"></a>明確可散發異動  

 您可以 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] (（包括但不限於作用中的) ）來呼叫 api <xref:System.Data.Linq.DataContext.SubmitChanges%2A> <xref:System.Transactions.Transaction> 。 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 偵測到呼叫是在交易的範圍內，而且不會建立新的交易。 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 也可避免在此情況下關閉連接。 您可以在此種異動的情況中執行查詢和 <xref:System.Data.Linq.DataContext.SubmitChanges%2A> 執行。  
  
## <a name="implicit-transaction"></a>隱含交易  

 當您呼叫時 <xref:System.Data.Linq.DataContext.SubmitChanges%2A> ，會 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 查看此呼叫是否在的範圍內，或者， <xref:System.Transactions.Transaction> 如果 `Transaction` 屬性 (`IDbTransaction`) 設定為使用者啟動的本機交易，則會進行檢查。 如果找不到交易，則會 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 啟動本機交易 (`IDbTransaction`) ，並使用它來執行所產生的 SQL 命令。 當所有 SQL 命令都已順利完成時，會認可 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 本機交易並傳回。  
  
## <a name="see-also"></a>另請參閱

- [背景資訊](background-information.md)
- [作法：使用異動括住提交的資料](how-to-bracket-data-submissions-by-using-transactions.md)
