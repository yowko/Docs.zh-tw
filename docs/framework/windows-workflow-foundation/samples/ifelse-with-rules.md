---
title: "搭配規則的 IfElse | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c4ad9bb2-9037-413a-8b14-59ed7b927a9e
caps.latest.revision: 8
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 8
---
# 搭配規則的 IfElse
這個範例會示範搭配 <xref:System.Workflow.Activities.IfElseActivity> 活動來使用規則條件。  
  
 此範例會從主機傳入 `OrderValue` 參數。該參數的值會在 <xref:System.Workflow.Activities.IfElseActivity> 活動的第一個分支上的規則條件中使用。如果其值小於 10,000，第一個分支便會執行，而且第一個分支中的 <xref:System.Workflow.Activities.CodeActivity> 活動會將 **Get Manager Approval** 列印到主控台中。如果其值大於 10,000，第二個分支中的 <xref:System.Workflow.Activities.CodeActivity> 活動便會執行，並會列印 **Get VP Approval**。  
  
### 若要建置範例  
  
1.  在 [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] 中開啟方案。  
  
2.  按 CTRL\+SHIFT\+B 建置此方案。  
  
3.  按 CTRL\+F5 執行方案，但不進行偵錯。  
  
### 若要執行範例  
  
-   在 \[SDK 命令提示字元\] 視窗中，於 IfElseWithRules\\bin\\debug 資料夾 \(若是 Visual Basic 版本的範例，則是 IfElseWithRules\\bin 資料夾\) 中執行此 .exe 檔案，該資料夾位於此範例的主要資料夾下方。  
  
> [!IMPORTANT]
>  這些範例可能已安裝在您的電腦上。請先檢查下列 \(預設\) 目錄，然後再繼續：  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目錄不存在，請移至[用於 .NET Framework 4 的 Windows Communication Foundation \(WCF\) 與 Windows Workflow Foundation \(WF\) 範例](http://go.microsoft.com/fwlink/?LinkId=150780)，以下載所有 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。此範例位於下列目錄：  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Rules\IfElseWithRules`  
  
## 請參閱  
 <xref:System.Workflow.Activities.Rules>   
 <xref:System.Workflow.Activities.IfElseActivity>   
 <xref:System.Workflow.Activities.CodeActivity>   
 <xref:System.Workflow.Activities.Rules.RuleDefinitions>