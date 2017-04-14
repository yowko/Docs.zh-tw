---
title: "SendParameters 及 ReceiveParameters 活動的基本使用 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1b6b1681-3d41-403f-bfe2-3f600f24aa8c
caps.latest.revision: 6
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 6
---
# SendParameters 及 ReceiveParameters 活動的基本使用
這個範例示範 <xref:System.ServiceModel.Activities.SendParametersContent> 和 <xref:System.ServiceModel.Activities.ReceiveParametersContent> 的使用方式。服務會公開依向作業，該作業會使用字串引數並將輸入 echo 至用戶端。這個範例將示範如何設定這些訊息處理活動的參數。  
  
> [!IMPORTANT]
>  這些範例可能已安裝在您的電腦上。請先檢查下列 \(預設\) 目錄，然後再繼續。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目錄不存在，請移至[用於 .NET Framework 4 的 Windows Communication Foundation \(WCF\) 與 Windows Workflow Foundation \(WF\) 範例](http://go.microsoft.com/fwlink/?LinkId=150780)，以下載所有 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。此範例位於下列目錄。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\SendReceiveParameters`  
  
#### 使用這個範例  
  
1.  在 [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] 中載入專案方案，然後建置專案。  
  
2.  請先執行 \[方案基底目錄\]\\EchoWorkflowService\\bin\\debug 中產生的 EchoWorkflowService 應用程式。  
  
3.  接著執行 \[方案基底目錄\]\\EchoWorkflowClient\\bin\\debug 中產生的 EchoWorkflowClient 應用程式。  
  
4.  用戶端會在服務上呼叫 Echo 作業並列印結果。完成時，按下 ENTER 結束用戶端，再結束服務。  
  
## 請參閱