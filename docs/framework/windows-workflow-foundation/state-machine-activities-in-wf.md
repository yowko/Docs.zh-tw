---
title: "WF 中的狀態機器活動 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 93312eaf-07e0-4a55-b4f7-4cdbbc4dee2d
caps.latest.revision: 7
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 7
---
# WF 中的狀態機器活動
[!INCLUDE[net_v45](../../../includes/net-v45-md.md)] 提供數種系統提供的活動和活動設計工具，用於建立狀態電腦工作流程。  
  
|||  
|-|-|  
|<xref:System.Activities.Statements.StateMachine>|使用熟悉的狀態電腦開發架構執行包含的活動。|  
|<xref:System.Activities.Statements.State>|表示狀態電腦中的狀態。|  
|<xref:System.Activities.Core.Presentation.FinalState>|表示狀態電腦中的終止狀態。<xref:System.Activities.Core.Presentation.FinalState> 是活動設計工具，使用時會建立預先設定為終止狀態的 <xref:System.Activities.Statements.State>。如需詳細資訊，請參閱 [FinalState 活動設計工具](../Topic/FinalState%20Activity%20Designer.md)。|  
|<xref:System.Activities.Statements.Transition>|表示在兩個狀態之間轉換。<xref:System.Activities.Statements.Transition> 沒有 **工具箱** 項目；轉換會在工作流程設計工具上利用拖曳兩個狀態之間的線條而建立，或透過將狀態放置在三角形上建立，該三角形會在滑鼠移到其中一個狀態上方時出現。如需詳細資訊，請參閱[轉換活動設計工具](../Topic/Transition%20Activity%20Designer.md)。|  
  
## 請參閱  
 [快速入門教學課程](../../../docs/framework/windows-workflow-foundation//getting-started-tutorial.md)