---
title: "執行屬性 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 31c009db-397c-4653-87e2-32dc77fa4b13
caps.latest.revision: 14
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 14
---
# 執行屬性
這個範例示範如何使用定義及使用自訂活動中的執行屬性。在這個範例中，執行屬性決定主控台的前景色彩。範例工作流程將示範不同的執行邏輯路徑 \(<xref:System.Activities.Statements.Parallel> 活動的分支\) 如何在活動交錯執行 \(跨 <xref:System.Activities.Statements.Parallel> 活動的分支\) 的情況下維持不同的主控台色彩。  
  
#### 若要安裝、建立及執行範例  
  
1.  在 [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] 中開啟 \[ExecutionProperties.sln\] 範例方案。  
  
    > [!NOTE]
    >  在建置方案之前檢視 ThreeColors.xaml 會顯示錯誤，因為使用的自訂活動必須與方案同時建置。  
  
2.  建立和執行方案。  
  
> [!IMPORTANT]
>  這些範例可能已安裝在您的電腦上。請先檢查下列 \(預設\) 目錄，然後再繼續。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目錄不存在，請移至[用於 .NET Framework 4 的 Windows Communication Foundation \(WCF\) 與 Windows Workflow Foundation \(WF\) 範例](http://go.microsoft.com/fwlink/?LinkId=150780)，以下載所有 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。此範例位於下列目錄。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\Code-Bodied\ExecutionProperties`  
  
## 請參閱