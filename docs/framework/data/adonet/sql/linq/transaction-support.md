---
title: "異動支援"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8cceb26e-8d36-4365-8967-58e2e89e0187
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 7c1d438a83f090795a158ade1dfdbb7d2b2df863
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="transaction-support"></a>異動支援
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]支援三種不同的交易模型。 以下按照執行檢查的順序列出這些模型。  
  
## <a name="explicit-local-transaction"></a>明確本機交易  
 呼叫 <xref:System.Data.Linq.DataContext.SubmitChanges%2A> 後，如果 <xref:System.Data.Linq.DataContext.Transaction%2A> 屬性已設為 (`IDbTransaction`) 交易，則會在相同交易的情況下執行 <xref:System.Data.Linq.DataContext.SubmitChanges%2A> 呼叫。  
  
 順利執行交易後，您必須負責認可或復原此交易。 對應至此交易的連接必須符合用於建構 <xref:System.Data.Linq.DataContext> 的連接。 如果使用不同的連接，則會擲回例外狀況。  
  
## <a name="explicit-distributable-transaction"></a>明確可散發異動  
 您可以呼叫[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]Api (包括但不是限於<xref:System.Data.Linq.DataContext.SubmitChanges%2A>) 範圍中的作用中<xref:System.Transactions.Transaction>。 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]偵測到該呼叫交易範圍內，而不會建立新的交易。 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]也可避免在此情況下關閉連接。 您可以在此種交易的情況中執行查詢和 <xref:System.Data.Linq.DataContext.SubmitChanges%2A> 執行。  
  
## <a name="implicit-transaction"></a>隱含異動  
 當您呼叫<xref:System.Data.Linq.DataContext.SubmitChanges%2A>，[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]會查看此呼叫是否在範圍內<xref:System.Transactions.Transaction>或`Transaction`屬性 (`IDbTransaction`) 設定為使用者啟動的本機交易。 如果兩種交易，[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]啟動本機交易 (`IDbTransaction`) 並用它來執行所產生的 SQL 命令。 當所有 SQL 命令已順利都完成時，[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]認可本機交易並傳回結果。  
  
## <a name="see-also"></a>另請參閱  
 [背景資訊](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)  
 [如何： 使用異動括資料提交](../../../../../../docs/framework/data/adonet/sql/linq/how-to-bracket-data-submissions-by-using-transactions.md)
