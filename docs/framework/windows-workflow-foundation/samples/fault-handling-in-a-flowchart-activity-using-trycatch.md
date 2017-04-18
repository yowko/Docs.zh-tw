---
title: "使用 TryCatch 錯誤處理流程圖活動 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 50922964-bfe0-4ba8-9422-0e7220d514fd
caps.latest.revision: 12
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 12
---
# 使用 TryCatch 錯誤處理流程圖活動
這個範例示範 <xref:System.Activities.Statements.TryCatch> 活動在複雜控制流程活動中的使用方式。  
  
 在這個範例中，促銷碼和小孩人數會當做變數傳遞至 <xref:System.Activities.Statements.Flowchart> 活動，根據對應於促銷碼的公式來計算折扣。此範例包含命令式程式碼和工作流程設計工具的範例版本。  
  
 下表詳細說明 `CreateFlowchartWithFaults` 活動的變數。  
  
|參數|說明|  
|--------|--------|  
|promoCode|促銷碼。類型：String<br /><br /> 可能的值，說明放在括號中：<br /><br /> -   Single \(單身\)<br />-   MNK \(已婚，沒有小孩\)<br />-   MWK \(已婚，有小孩\)|  
|numKids|小孩人數。類型：int|  
  
 `CreateFlowchartWithFaults` 活動使用 <xref:System.Activities.Statements.FlowSwitch%601> 活動，在 `promoCode` 引數上切換，並透過下列公式計算折扣。  
  
|`promoCode` 的值|折扣 \(%\)|  
|--------------------|--------------|  
|Single|10|  
|MNK|15|  
|MWK|15 \+ \(1 – 1\/`numberOfKids`\)\*10 **Note:**  此計算可能會擲回 <xref:System.DivideByZeroException>。因此，折扣計算是包裝在 <xref:System.Activities.Statements.TryCatch> 活動中，以攔截 <xref:System.DivideByZeroException> 例外狀況並將折扣設為零。|  
  
#### 若要使用這個範例  
  
1.  使用 [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] 開啟 FlowchartWithFaultHandling.sln 方案檔案。  
  
2.  若要建置此方案，請按下 CTRL\+SHIFT\+B。  
  
3.  若要執行此方案，請按 F5。  
  
> [!IMPORTANT]
>  這些範例可能已安裝在您的電腦上。請先檢查下列 \(預設\) 目錄，然後再繼續。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目錄不存在，請移至[用於 .NET Framework 4 的 Windows Communication Foundation \(WCF\) 與 Windows Workflow Foundation \(WF\) 範例](http://go.microsoft.com/fwlink/?LinkId=150780)，以下載所有 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。此範例位於下列目錄。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\FlowChartWithFaultHandling`  
  
## 請參閱  
 [Flowchart 工作流程](../../../../docs/framework/windows-workflow-foundation//flowchart-workflows.md)   
 [例外狀況](../../../../docs/framework/windows-workflow-foundation//exceptions.md)