---
title: "WF 中的控制流程活動 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6892885b-f7c5-4aea-8f5e-28863fb4ae75
caps.latest.revision: 16
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 16
---
# WF 中的控制流程活動
[!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] 提供數種活動，可用於控制工作流程內的執行流程。其中部分活動 \(例如 `Switch` 和 `If`\) 會實作與 [!INCLUDE[csprcs](../../../includes/csprcs-md.md)] 等程式設計環境類似的流程控制架構，其他活動則以新的程式設計架構 \(例如 `Pick`\) 為模型。  
  
 請注意，`Parallel` 和 `ParallelForEach` 之類的活動排定多個同時執行的子活動時，工作流程只能使用單一執行緒。這些活動的每個子活動會循序執行，在先前的活動完成或閒置之前，後續的活動均不會執行。因此，最適合使用這些活動的應用程式即為必須交錯執行數個可能封鎖之活動的應用程式。如果這些活動的子活動均閒置，`Parallel` 活動會像 `Sequence` 活動般執行，而 `ParallelForEach` 活動則會像 `ForEach` 活動般執行。然而，如果使用非同步活動 （例如衍生自 <xref:System.Activities.AsyncCodeActivity> 的活動\) 或傳訊活動，控制項會傳遞至下一個分支，而子活動則會等候接收其訊息或非同步工作完成。  
  
## 流量控制活動  
  
|活動|說明|  
|--------|--------|  
|<xref:System.Activities.Statements.DoWhile>|執行所包含的活動一次，並繼續執行直到條件為 `true` 為止。|  
|<xref:System.Activities.Statements.ForEach%601>|針對集合中的每個項目，循序執行內嵌陳述式。<xref:System.Activities.Statements.ForEach%601> 與關鍵字 `foreach` 相似，但會做為活動而非語言陳述式來實作。|  
|<xref:System.Activities.Statements.If>|如果條件為 `true` 則執行所包含的活動，如果條件為 `false`，則可執行包含在 <xref:System.Activities.Statements.If.Else%2A> 屬性中的活動。|  
|<xref:System.Activities.Statements.Parallel>|平行執行所包含的活動。|  
|<xref:System.Activities.Statements.ParallelForEach%601>|針對集合中的每個項目，平行執行內嵌陳述式。|  
|<xref:System.Activities.Statements.Pick>|提供事件架構控制流程模型。|  
|<xref:System.Activities.Statements.PickBranch>|在 <xref:System.Activities.Statements.Pick> 活動中代表潛在的執行路徑。|  
|<xref:System.Activities.Statements.Sequence>|循序執行所包含的活動。|  
|<xref:System.Activities.Statements.Switch%601>|根據此指定運算式的值，從活動成員中選取要執行的一個選項。|  
|<xref:System.Activities.Statements.While>|當條件為 `true` 時執行所包含的活動。|