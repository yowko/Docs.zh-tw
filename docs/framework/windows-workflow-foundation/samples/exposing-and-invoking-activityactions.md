---
title: "公開及叫用 ActivityActions | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 97ce4797-426e-463d-9cc4-1261afad6df4
caps.latest.revision: 11
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 11
---
# 公開及叫用 ActivityActions
這個範例示範如何開發有 <xref:System.Activities.ActivityAction> 的自訂活動。此外，也示範如何提供 <xref:System.Activities.ActivityAction> 實作，使用此活動。  
  
 <xref:System.Activities.ActivityAction> 可讓活動作者使用特定的簽章以公開「洞孔」，活動使用者可在此插入自訂行為。例如，<xref:System.Activities.Statements.ForEach> 活動 \(在項目集合上操作\) 有 <xref:System.Activities.ActivityAction>，可讓活動使用者插入可在目前反覆運算項目上操作的行為。  
  
#### 若要安裝、建立及執行範例  
  
1.  在 [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] 中開啟 **ActivityAction.sln** 範例方案。  
  
2.  建立和執行方案。  
  
> [!IMPORTANT]
>  這些範例可能已安裝在您的電腦上。請先檢查下列 \(預設\) 目錄，然後再繼續。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目錄不存在，請移至[用於 .NET Framework 4 的 Windows Communication Foundation \(WCF\) 與 Windows Workflow Foundation \(WF\) 範例](http://go.microsoft.com/fwlink/?LinkId=150780)，以下載所有 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。此範例位於下列目錄。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\Code-Bodied\ActivityAction`  
  
## 請參閱