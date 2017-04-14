---
title: "流速控制平行 ForEach | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f2855b5f-e9a7-433d-96a4-40fc31025215
caps.latest.revision: 6
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 6
---
# 流速控制平行 ForEach
`ThrottleParallelForEach` 活動與 <xref:System.Activities.Statements.ParallelForEach> 活動十分類似，唯一的例外是前者允許設定並行因數來限制同時執行的分支數目。`ThrottleParallelForEach` 活動衍生自 <xref:System.Activities.NativeActivity>，因為它必須排程其他活動 \(子活動\)，而且這只能透過 <xref:System.Activities.NativeActivityContext> 類別存取。  
  
## 專案  
  
||||  
|-|-|-|  
|**專案名稱**|**說明**|**主要檔案**|  
|ThrottledParallelForEach|包含 `ThrottledParallelForEach` 活動和其設計工具|ThrottledParallelForEach.cs<br /><br /> `ThrottledParallelForEach` 活動定義。|  
|CodeTestClient|範例用戶端應用程式，可透過使用命令式程式碼的 `ThrottledParallelForEach` 來設定及執行工作流程。|Program.cs<br /><br /> 定義及執行範例工作流程的執行個體。|  
  
#### 若要使用這個範例  
  
1.  使用 [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] 開啟 ThrottledParallelForEach.sln 檔案。  
  
2.  若要建置此方案，請按下 CTRL\+SHIFT\+B。  
  
3.  若要執行此方案，請按 F5。  
  
> [!IMPORTANT]
>  這些範例可能已安裝在您的電腦上。請先檢查下列 \(預設\) 目錄，然後再繼續。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目錄不存在，請移至[用於 .NET Framework 4 的 Windows Communication Foundation \(WCF\) 與 Windows Workflow Foundation \(WF\) 範例](http://go.microsoft.com/fwlink/?LinkId=150780)，以下載所有 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。此範例位於下列目錄。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\ThrottledParallelForEach`  
  
## 請參閱