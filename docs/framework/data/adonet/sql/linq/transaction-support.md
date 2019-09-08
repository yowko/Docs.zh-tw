---
title: 異動支援
ms.date: 03/30/2017
ms.assetid: 8cceb26e-8d36-4365-8967-58e2e89e0187
ms.openlocfilehash: 9c7128ef432fa609b8d628bc74caebe790058ede
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70792270"
---
# <a name="transaction-support"></a>異動支援
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]支援三種不同的交易模型。 以下按照執行檢查的順序列出這些模型。  
  
## <a name="explicit-local-transaction"></a>明確本機異動  
 呼叫 <xref:System.Data.Linq.DataContext.SubmitChanges%2A> 後，如果 <xref:System.Data.Linq.DataContext.Transaction%2A> 屬性已設為 (`IDbTransaction`) 交易，則會在相同交易的情況下執行 <xref:System.Data.Linq.DataContext.SubmitChanges%2A> 呼叫。  
  
 順利執行異動後，您必須負責認可或復原此異動。 對應至此交易的連接必須符合用於建構 <xref:System.Data.Linq.DataContext> 的連接。 如果使用不同的連接，則會擲回例外狀況。  
  
## <a name="explicit-distributable-transaction"></a>明確可散發異動  
 您可以在[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]作用中的範圍<xref:System.Transactions.Transaction>內呼叫 api <xref:System.Data.Linq.DataContext.SubmitChanges%2A>（包括但不限於）。 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]偵測到呼叫是在交易的範圍內，而且不會建立新的交易。 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]在此情況下也可避免關閉連接。 您可以在此種異動的情況中執行查詢和 <xref:System.Data.Linq.DataContext.SubmitChanges%2A> 執行。  
  
## <a name="implicit-transaction"></a>隱含交易  
 當您呼叫<xref:System.Data.Linq.DataContext.SubmitChanges%2A>時[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] ，會檢查呼叫是否<xref:System.Transactions.Transaction>在的範圍內，或是`Transaction`屬性（`IDbTransaction`）是否設定為使用者啟動的本機交易。 如果找不到交易， [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]則會啟動本機交易`IDbTransaction`（），並使用它來執行所產生的 SQL 命令。 當所有 SQL 命令都已順利完成時[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] ，會認可本機交易並傳回。  
  
## <a name="see-also"></a>另請參閱

- [背景資訊](background-information.md)
- [如何：使用交易來括住資料提交](how-to-bracket-data-submissions-by-using-transactions.md)
