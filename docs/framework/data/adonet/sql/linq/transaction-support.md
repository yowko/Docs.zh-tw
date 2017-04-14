---
title: "交易支援 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 8cceb26e-8d36-4365-8967-58e2e89e0187
caps.latest.revision: 2
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 2
---
# 交易支援
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 支援三種不同的交易模型。  以下按照執行檢查的順序列出這些模型。  
  
## 明確本機交易  
 呼叫 <xref:System.Data.Linq.DataContext.SubmitChanges%2A> 後，如果 <xref:System.Data.Linq.DataContext.Transaction%2A> 屬性已設為 \(`IDbTransaction`\) 交易，則會在相同交易的情況下執行 <xref:System.Data.Linq.DataContext.SubmitChanges%2A> 呼叫。  
  
 順利執行交易後，您必須負責認可或復原此交易。  對應至此交易的連接必須符合用於建構 <xref:System.Data.Linq.DataContext> 的連接。  如果使用不同的連接，則會擲回例外狀況。  
  
## 明確可散發交易  
 您可以在使用中的 <xref:System.Transactions.Transaction> 範圍內呼叫 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] API \(包含但不限於 <xref:System.Data.Linq.DataContext.SubmitChanges%2A>\)。  [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 會偵測到該呼叫在交易的範圍內，而不會建立新交易。  [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 在此情況下也可避免關閉連接。  您可以在此種交易的情況中執行查詢和 <xref:System.Data.Linq.DataContext.SubmitChanges%2A> 執行。  
  
## 隱含交易  
 當您呼叫 <xref:System.Data.Linq.DataContext.SubmitChanges%2A> 時，[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 會查看此呼叫是否在 <xref:System.Transactions.Transaction> 的範圍內，或者 `Transaction` 屬性 \(`IDbTransaction`\) 是否設為使用者啟動的本機交易。  如果兩種交易都找不到，[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 會啟動本機交易 \(`IDbTransaction`\) 並用它來執行所產生的 SQL 命令。  當所有 SQL 命令都已順利完成後，[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 會認可本機交易並傳回結果。  
  
## 請參閱  
 [背景資訊](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)   
 [HOW TO：使用交易括住資料提交](../../../../../../docs/framework/data/adonet/sql/linq/how-to-bracket-data-submissions-by-using-transactions.md)