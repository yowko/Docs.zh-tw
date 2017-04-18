---
title: "與外部資料交換服務互通使用 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 96f6fe26-5305-494f-9119-7748e0c4b3fa
caps.latest.revision: 6
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 6
---
# 與外部資料交換服務互通使用
<xref:System.Activities.Statements.Interop> 活動可用來從 [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)] 中的 [!INCLUDE[wf](../../../../includes/wf-md.md)] 及 [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)] \(WF3\) 執行活動，以及從 [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] \(WF4\) 的 [!INCLUDE[wf2](../../../../includes/wf2-md.md)] 執行工作流程。此範例示範如何使用 WF4 工作流程服務中的 <xref:System.Activities.Statements.Interop> 活動，以設定及執行 WF3 工作流程來使用 <xref:System.Workflow.Activities.ExternalDataExchangeService> \(以及用來呼叫方法和處理事件的對應自訂活動\)。  
  
> [!IMPORTANT]
>  這些範例可能已安裝在您的電腦上。請先檢查下列 \(預設\) 目錄，然後再繼續。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目錄不存在，請移至[用於 .NET Framework 4 的 Windows Communication Foundation \(WCF\) 與 Windows Workflow Foundation \(WF\) 範例](http://go.microsoft.com/fwlink/?LinkId=150780)，以下載所有 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。此範例位於下列目錄。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Migration\ExternalDataExchange`  
  
#### 若要使用這個範例  
  
1.  在 [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] 中開啟 ExternalDataExchange.sln 檔案。  
  
2.  若要建置範例，請按 CTRL\+SHIFT\+B。  
  
3.  若要執行範例，請按 F5。