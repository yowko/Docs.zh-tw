---
title: "使用活動類別撰寫工作流程活動 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7b7b1c66-f093-43c3-b4d1-7173b46516da
caps.latest.revision: 7
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 7
---
# 使用活動類別撰寫工作流程活動
在 [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] 中使用 [!INCLUDE[wf](../../../includes/wf-md.md)] 建立活動，最基本的方式是建立繼承自 <xref:System.Activities.Activity> 的類別，此類別會透過組合自訂活動或 [內建活動程式庫](../../../docs/framework/windows-workflow-foundation//net-framework-4-5-built-in-activity-library.md) 中的活動建立功能。本主題示範如何建立會寫入兩個訊息至主控台的活動。  
  
### 若要使用活動設計工具建立自訂活動  
  
1.  開啟 [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)]。  
  
2.  依序選取 \[檔案\]、\[新增\]、\[專案\]。在 \[**專案類型**\] 視窗中，選取 \[**Visual C\#**\] 下方 \[**Workflow 4.0**\]，然後選取 \[**v2010**\] 節點。選取 \[**範本**\] 視窗中的 \[**活動程式庫**\]。將新專案命名為 HelloActivity。  
  
3.  開啟新活動。將 <xref:System.Activities.Statements.Sequence> 活動從工具箱拖曳至設計工具介面上。  
  
4.  將 <xref:System.Activities.Statements.WriteLine> 活動拖曳至 <xref:System.Activities.Statements.Sequence> 活動中。在 \[**文字**\] 欄位中輸入 `"Hello World"` \(含引號\)。  
  
5.  將第二個 <xref:System.Activities.Statements.WriteLine> 活動拖曳至 <xref:System.Activities.Statements.Sequence> 活動，放在第一個活動下方。在 \[**文字**\] 欄位中輸入 `"Goodbye"` \(含引號\)。