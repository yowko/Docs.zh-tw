---
title: Transactions2
ms.date: 03/30/2017
ms.assetid: 51212219-a39e-448e-bff3-10064ff5de64
ms.openlocfilehash: 361022851d971c0b9350899e1fee6a27c557d666
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="transactions"></a>異動
本節包含示範工作流程異動中 Windows Workflow Foundation (WF) 範例。  
  
## <a name="in-this-section"></a>本節內容  
 [基本 TransactionScope](../../../../docs/framework/windows-workflow-foundation/samples/basic-transactionscope.md)  
 包含四個示範如何巢狀處理 <xref:System.Activities.Statements.TransactionScope> 執行個體的案例。  
  
 [TransactedReceiveScope 的使用](../../../../docs/framework/windows-workflow-foundation/samples/use-of-transactedreceivescope.md)  
 示範如何將交易從用戶端流送至伺服器，方式是使用 <xref:System.Activities.Statements.TransactionScope> 在用戶端建立新交易，以及在伺服器上使用 <xref:System.ServiceModel.Activities.TransactedReceiveScope> 接收有流動交易之訊息並設定交易存留期範圍。  
  
 [巢狀處理服務中的 TransactionScope](../../../../docs/framework/windows-workflow-foundation/samples/nesting-of-transactionscope-within-a-service.md)  
 包含兩個示範如何在服務中處理 <xref:System.Activities.Statements.TransactionScope> 活動執行個體的案例。
