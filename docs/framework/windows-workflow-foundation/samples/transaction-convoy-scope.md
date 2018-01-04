---
title: "異動防護範圍"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 37141708-a29f-4b6a-81fe-f8a11f825061
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 854e04c53bf438c3356072d762f129b7f21b7dd5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="transaction-convoy-scope"></a>異動防護範圍
這個範例示範如何建立 Parallel Convoy 訊息活動模式搭配 <xref:System.ServiceModel.Activities.TransactedReceiveScope>，以建立多個作業可依任何順序同時在相同交易中發生的通訊協定模型。 這個範例也示範 <xref:System.ServiceModel.Activities.TransactedReceiveScope> 如何在沒有交易流向伺服器時自動建立新交易，因此用戶端不會利用任何交易。  
  
 這個範例包含兩個代表用戶端和伺服器的工作流程專案。 用戶端專案執行的工作流程一開始會先傳送訊息，以啟動載入伺服器工作流程，後者則會初始化相互關聯，並為其餘訊息活動啟動交易式範圍。 用戶端 <xref:System.Activities.Statements.Sequence> 活動包含初始 <xref:System.ServiceModel.Activities.Send> 和 <xref:System.ServiceModel.Activities.ReceiveReply> 配對，接著是含有三個分支的 <xref:System.Activities.Statements.Parallel> 活動。 每個分支會傳送單向訊息給伺服器。 <xref:System.Activities.Statements.Parallel.CompletionCondition%2A> 活動的 <xref:System.Activities.Statements.Parallel> 屬性設為 `false`，因此所有三個分支已完成。  
  
 伺服器工作流程與用戶端工作流程類似，不同之處在於訊息活動導向通訊的伺服器端，而且包含在 <xref:System.ServiceModel.Activities.TransactedReceiveScope> 活動中，因此所有完成的工作都是在相同交易中執行。 當伺服器接收第一個訊息時，會建立交易，而此交易會成為 <xref:System.ServiceModel.Activities.TransactedReceiveScope> 主體範圍的環境交易，於是此範圍內的任何活動都可以存取此交易。 在此之後，所有接收活動都會平行執行。 所有接收活動只能執行一次，如平行活動的完成交易所描述。 <xref:System.ServiceModel.Activities.TransactedReceiveScope> 主體結尾有隱含持續點，而且持續性作業也會在相同交易中執行。  
  
#### <a name="to-use-this-sample"></a>若要使用這個範例  
  
1.  使用 [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] 開啟 ParallelConvoySample.sln 方案檔案。  
  
2.  若要建置此方案，請按 CTRL+SHIFT+B。  
  
3.  確認兩個專案都是設為起始專案。  
  
    1.  在**方案總管 中**，以滑鼠右鍵按一下方案，然後選取**設定啟始專案**。  
  
    2.  選取**多個啟始專案**，請確定這兩個專案的動作設定為**啟動**。  
  
4.  若要執行此方案，請按下 CTRL+F5。  
  
     伺服器會列印 `Server is running`，表示伺服器就緒。  
  
     在用戶端主控台視窗中按任何鍵，以啟動範例。  
  
> [!IMPORTANT]
>  這些範例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目錄不存在，請移至 [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4  (適用於 .NET Framework 4 的 Windows Communication Foundation (WCF) 與 Windows Workflow Foundation (WF) 範例)](http://go.microsoft.com/fwlink/?LinkId=150780) ，以下載所有 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。 此範例位於下列目錄。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Transactions\TransactedConvoyScope`