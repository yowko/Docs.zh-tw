---
title: 交易的佇列
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b1b011dd-5e0b-482c-9bb0-9d8727038f14
caps.latest.revision: 9
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 628e91589ad32a2646316401c7b2ddb31b13eace
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/27/2018
---
# <a name="transacted-queues"></a>交易的佇列
這個範例示範如何整合佇列和交易中 Windows Workflow Foundation (WF) 來建立可靠和可擴充的服務。 A <!--zz <xref:System.Activities.TransactionScope>--> `System.Activities.TransactionScope`在用戶端工作流程中用於傳送訊息至佇列，以在交易使用<xref:System.ServiceModel.NetMsmqBinding>。 在伺服器上使用 <xref:System.ServiceModel.Activities.TransactedReceiveScope>，在相同交易下從佇列接收訊息並更新工作流程狀態。  
  
## <a name="demonstrates"></a>示範  
 <xref:System.Activities.Statements.TransactionScope>、<xref:System.ServiceModel.Activities.TransactedReceiveScope>、<xref:System.ServiceModel.NetMsmqBinding>、<xref:System.ServiceModel.Activities.Receive> 和內容架構的相互關聯  
  
## <a name="discussion"></a>討論  
 為了示範這個範例中涵蓋的功能，我們會建立 `RewardsPoints` 工作流程服務，追蹤給定帳戶所得到和使用的點數。 用戶端使用 <xref:System.Activities.WorkflowInvoker> 模擬公佈至佇列的各種要求。 為了在交易下將訊息公佈至佇列，<xref:System.ServiceModel.Activities.Send> 活動可以置於 <xref:System.Activities.Statements.TransactionScope.Body%2A> 的 <xref:System.Activities.Statements.TransactionScope> 之中。 在這個範例中，先執行用戶端，接著執行伺服器，以示範佇列訊息如何分化用戶端和伺服器應用程式。  
  
 一旦用戶端完成，就會設定及裝載服務。 一旦服務開啟，就會開始處理已經排入佇列中的訊息。 每個訊息都是在相同伺服器交易下接收及處理的。 在這個範例中，第一個收到的訊息是 `CreateAccount` 要求，它會建立執行個體，並根據要求訊息中傳遞的帳戶名稱來初始化內容相互關聯。 以真實世界可預期的服務類型為模型，下列兩個處理 <xref:System.ServiceModel.Activities.TransactedReceiveScope> 和 `AddPoints` 訊息的 `UsePoints` 活動會放在 `while` 迴圈的平行分支中，以任何順序重複處理這些訊息。  
  
 <xref:System.Activities.Statements.TransactionScope> 和 <xref:System.ServiceModel.Activities.TransactedReceiveScope> 的範圍結尾都有隱含保存點，因此在 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 中使用這些活動結合佇列是將工作流程從某個一致狀態移至下一個狀態的可靠方式，同時可確保訊息永不遺失。  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>若要安裝、建置及執行範例  
  
1.  安裝及設定 MSMQ。 請參閱[安裝訊息佇列](http://go.microsoft.com/fwlink/?LinkId=178526)如需詳細資訊。  
  
2.  在命令列中執行下列命令，以確認 MSDTC 正在執行中。 `net start msdtc`  
  
3.  編譯專案並開啟可執行檔，或在 [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] 中開啟專案，然後從偵錯功能表選取啟動選項。 首先會建立佇列，接著執行用戶端並將訊息公佈至佇列，最後會啟動服務並處理訊息。 若要結束程式，請按 ENTER。  
  
> [!IMPORTANT]
>  這些範例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目錄不存在，請移至 [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4  (適用於 .NET Framework 4 的 Windows Communication Foundation (WCF) 與 Windows Workflow Foundation (WF) 範例)](http://go.microsoft.com/fwlink/?LinkId=150780) ，以下載所有 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。 此範例位於下列目錄。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Transactions\TransactedQueues`
