---
title: "建立與執行工作流程執行個體 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 19d27f47-0491-4569-8f53-51bc1d940e80
caps.latest.revision: 6
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 6
---
# 建立與執行工作流程執行個體
這個範例示範如何執行工作流程執行個體。範例中會示範如何以同步和非同步方式執行。  
  
## 示範  
 <xref:System.Activities.WorkflowInvoker>, <xref:System.Activities.WorkflowApplication>.  
  
## 討論  
 範例的第一個部分會使用 <xref:System.Activities.WorkflowInvoker.Invoke%2A>。這是執行工作流程的最基本方式。使用 <xref:System.Activities.WorkflowInvoker.Invoke%2A> 執行的工作流程是以同步方式執行的。  
  
 範例第二部分使用 <xref:System.Activities.WorkflowApplication> 類別。<xref:System.Activities.WorkflowApplication> 可讓您更充分掌控每一個執行個體，包括與執行中工作流程進行互動以及透過非同步方式執行工作流程的能力。  
  
> [!IMPORTANT]
>  這些範例可能已安裝在您的電腦上。請先檢查下列 \(預設\) 目錄，然後再繼續。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目錄不存在，請移至[用於 .NET Framework 4 的 Windows Communication Foundation \(WCF\) 與 Windows Workflow Foundation \(WF\) 範例](http://go.microsoft.com/fwlink/?LinkId=150780)，以下載所有 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。此範例位於下列目錄。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Execution\CreatingWorkflowInstances`  
  
## 請參閱  
 [使用 WorkflowInvoker 與 WorkflowApplication](../../../../docs/framework/windows-workflow-foundation//using-workflowinvoker-and-workflowapplication.md)