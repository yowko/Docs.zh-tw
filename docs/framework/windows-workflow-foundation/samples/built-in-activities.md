---
title: "內建活動 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 31e1b8c2-7f74-458a-b2e2-fddc5b10eac1
caps.latest.revision: 3
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 3
---
# 內建活動
本節包含的範例會示範內建的 [!INCLUDE[wf](../../../../includes/wf-md.md)] 活動。  
  
## 在本節中  
 [使用 TryCatch 錯誤處理流程圖活動](../../../../docs/framework/windows-workflow-foundation/samples/fault-handling-in-a-flowchart-activity-using-trycatch.md)  
 示範 <xref:System.Activities.Statements.TryCatch> 活動在複雜控制流程活動中的使用方式。  
  
 [While 活動中的模擬中斷](../../../../docs/framework/windows-workflow-foundation/samples/emulating-breaking-in-a-while-activity.md)  
 示範如何中斷下列活動的迴圈機制：<xref:System.Activities.Statements.DoWhile>、<xref:System.Activities.Statements.ForEach%601>、<xref:System.Activities.Statements.While> 和 <xref:System.Activities.Statements.ParallelForEach%601>。  
  
 [DynamicActivity 建立](../../../../docs/framework/windows-workflow-foundation/samples/dynamicactivity-creation.md)  
 示範在執行階段使用 <xref:System.Activities.DynamicActivity> 活動建立活動的兩種不同方式。  
  
 [搭配 .NET Framework 3.5 Ruleset 使用變數](../../../../docs/framework/windows-workflow-foundation/samples/using-variables-with-dotnet-ruleset.md)  
 示範如何建立使用 <xref:System.Activities.Statements.Interop> 活動整合 [!INCLUDE[netfx35_short](../../../../includes/netfx35-short-md.md)] 中使用原則和規則所撰寫自訂活動的工作流程。  
  
 [從 XAML 載入](../../../../docs/framework/windows-workflow-foundation/samples/load-from-xaml.md)  
 示範如何動態載入 XAML 工作流程，而不必執行 XamlBuildTask 工具。  
  
 [使用集合活動](../../../../docs/framework/windows-workflow-foundation/samples/using-collection-activities.md)  
 示範如何透過實作 <xref:System.Collections.ICollection> 介面的類別使用集合活動 \(<xref:System.Activities.Statements.AddToCollection%601>、<xref:System.Activities.Statements.ClearCollection%601>、<xref:System.Activities.Statements.ExistsInCollection%601> 和 <xref:System.Activities.Statements.RemoveFromCollection%601>\)，以及如何建立逐一查看集合以列印出集合中每一個項目內容的自訂活動。  
  
 [使用 InvokeMethod 活動](../../../../docs/framework/windows-workflow-foundation/samples/using-the-invokemethod-activity.md)  
 示範如何使用 <xref:System.Activities.Statements.InvokeMethod> 活動叫用公用類別中的公用方法。  
  
 [使用 Pick 活動](../../../../docs/framework/windows-workflow-foundation/samples/using-the-pick-activity.md)  
 示範如何使用 <xref:System.Activities.Statements.Pick> 活動。  
  
 [使用程序性活動](../../../../docs/framework/windows-workflow-foundation/samples/using-procedural-activities.md)  
 示範如何使用 <xref:System.Activities.Statements.Sequence>、<xref:System.Activities.Statements.Assign>、<xref:System.Activities.Statements.If>、<xref:System.Activities.Statements.While>、<xref:System.Activities.Statements.Switch%601>、<xref:System.Activities.Statements.TryCatch> 和 <xref:System.Activities.Statements.WriteLine> 活動實作猜測遊戲。  
  
 [使用 CancellationScope](../../../../docs/framework/windows-workflow-foundation/samples/using-cancellationscope.md)  
 示範如何使用 <xref:System.Activities.Statements.CancellationScope> 活動取消應用程式中的工作。  
  
 [InvokeMethod](../../../../docs/framework/windows-workflow-foundation/samples/invokemethod.md)  
 示範以不同的方式使用 <xref:System.Activities.Statements.InvokeMethod> 活動叫用類別的方法。  
  
 [使用自訂類型之切換活動的使用](../../../../docs/framework/windows-workflow-foundation/samples/usage-of-the-switch-activity-with-custom-types.md)  
 描述如何啟用 <xref:System.Activities.Statements.Switch%601> 活動，在執行階段評估使用者定義的複雜類型。  
  
 [和 3.5 規則集互通](../../../../docs/framework/windows-workflow-foundation/samples/interop-with-3-5-rule-set.md)  
 示範使用 <xref:System.Activities.Statements.Interop> 活動透過 <xref:System.Workflow.Activities.PolicyActivity> 和規則整合 [!INCLUDE[netfx35_short](../../../../includes/netfx35-short-md.md)] 中的自訂活動。