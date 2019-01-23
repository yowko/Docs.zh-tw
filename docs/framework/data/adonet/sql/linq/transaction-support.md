---
title: 異動支援
ms.date: 03/30/2017
ms.assetid: 8cceb26e-8d36-4365-8967-58e2e89e0187
ms.openlocfilehash: f53a6081102991c73543b4cd76365f7e2c0faf89
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54517197"
---
# <a name="transaction-support"></a>異動支援
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 支援三種不同的交易模型。 以下按照執行檢查的順序列出這些模型。  
  
## <a name="explicit-local-transaction"></a>明確本機交易  
 呼叫 <xref:System.Data.Linq.DataContext.SubmitChanges%2A> 後，如果 <xref:System.Data.Linq.DataContext.Transaction%2A> 屬性已設為 (`IDbTransaction`) 交易，則會在相同交易的情況下執行 <xref:System.Data.Linq.DataContext.SubmitChanges%2A> 呼叫。  
  
 順利執行交易後，您必須負責認可或復原此交易。 對應至此交易的連接必須符合用於建構 <xref:System.Data.Linq.DataContext> 的連接。 如果使用不同的連接，則會擲回例外狀況。  
  
## <a name="explicit-distributable-transaction"></a>明確可散發異動  
 您可以呼叫[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]Api (包括但不是限於<xref:System.Data.Linq.DataContext.SubmitChanges%2A>) 中的作用範圍<xref:System.Transactions.Transaction>。 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 偵測到該呼叫在交易的範圍內，而不會建立新的交易。 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 也可避免在此情況下關閉連接。 您可以在此種異動的情況中執行查詢和 <xref:System.Data.Linq.DataContext.SubmitChanges%2A> 執行。  
  
## <a name="implicit-transaction"></a>隱含異動  
 當您呼叫<xref:System.Data.Linq.DataContext.SubmitChanges%2A>，[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]檢查，以查看呼叫是否在範圍<xref:System.Transactions.Transaction>或者`Transaction`屬性 (`IDbTransaction`) 設定為使用者啟動的本機異動。 如果沒有交易中，找到[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]會啟動本機交易 (`IDbTransaction`) 並用它來執行產生的 SQL 命令。 已順利完成所有的 SQL 命令，[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]認可本機交易，並傳回。  
  
## <a name="see-also"></a>另請參閱
- [背景資訊](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)
- [如何：使用異動括住資料提交內容](../../../../../../docs/framework/data/adonet/sql/linq/how-to-bracket-data-submissions-by-using-transactions.md)
