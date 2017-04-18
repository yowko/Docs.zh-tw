---
title: "基本 Windows Workflow 概念 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0e930e80-5060-45d2-8a7a-95c0690105d4
caps.latest.revision: 27
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 27
---
# 基本 Windows Workflow 概念
[!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] 中的工作流程開發運用了一些開發人員可能未曾使用過的概念。本主題描述其中的部分概念及其實作方式。  
  
## 工作流程與活動  
 工作流程是結構化的動作集合，這些動作會以處理序為模型。工作流程中的每一個活動都會製作成活動的模型。主機與工作流程互動的方式是使用 <xref:System.Activities.WorkflowInvoker>，將工作流程視為方法來叫用、使用 <xref:System.Activities.WorkflowApplication> 明確控制單一工作流程執行個體的執行，以及使用 <xref:System.ServiceModel.WorkflowServiceHost> 在多執行個體案例中進行以訊息為主的互動。由於工作流程的步驟定義為活動的階層，因此階層中最上方的活動可說是用於定義工作流程本身。這個階層模型取代了舊版中明確的 `SequentialWorkflow` 及 `StateMachineWorkflow` 類別。活動本身會開發做為其他活動的集合 \(使用 <xref:System.Activities.Activity> 類別做為基底，通常使用 XAML 來定義\)，或者使用 <xref:System.Activities.CodeActivity> 類別 \(可以使用執行階段進行資料存取\) 或 <xref:System.Activities.NativeActivity> 類別 \(會向活動作者公開工作執行階段的廣度\)，透過自訂方式來建立。使用 <xref:System.Activities.CodeActivity> 和 <xref:System.Activities.NativeActivity> 開發的活動是使用與 CLR 相容的語言 \(例如 C\#\) 開發而成的。  
  
## 活動資料模型  
 活動會利用下表所列的型別儲存及共用資料。  
  
|||  
|-|-|  
|變數|將資料儲存在活動中。|  
|引數|將資料移入與移出活動。|  
|運算式|具有提升用於引數繫結之傳回值的活動。|  
  
## 工作流程執行階段  
 工作流程執行階段是工作流程的執行環境。<xref:System.Activities.WorkflowInvoker> 是最簡單的工作流程執行方式。主機會使用 <xref:System.Activities.WorkflowInvoker> 進行下列作業：  
  
-   同步叫用工作流程。  
  
-   提供輸入至工作流程，或從工作流程擷取輸出。  
  
-   加入活動所使用的擴充。  
  
 <xref:System.Activities.ActivityInstance> 是具備執行緒安全的 Proxy，主機可利用它來與執行階段互動。主機會使用 <xref:System.Activities.ActivityInstance> 進行下列作業：  
  
-   透過建立執行個體，或從執行個體存放區載入來取得執行個體。  
  
-   收到執行個體開發生命週期事件通知。  
  
-   控制工作流程的執行。  
  
-   提供輸入至工作流程，或從工作流程擷取輸出。  
  
-   發出工作流程接續的訊號並將值傳入工作流程中。  
  
-   保存工作流程資料。  
  
-   加入活動所使用的擴充。  
  
 透過使用適當的 <xref:System.Activities.ActivityContext>派生類別，例如  <xref:System.Activities.NativeActivityContext>或  <xref:System.Activities.CodeActivityContext>，活動可存取工作流程執行階段環境。並且會利用這種方式解析引數與變數、排程子活動，以及用於許多其他用途。  
  
## 服務  
 工作流程提供使用傳訊活動自然實作及存取鬆散耦合服務的方式。傳訊活動建構於 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)]，也是用於傳入及傳出工作流程資料的主要機制。您可以一起撰寫傳訊活動，針對您所需的任何傳訊交換型式建立模型。[!INCLUDE[crdefault](../../../includes/crdefault-md.md)] 請參閱 [訊息活動](../../../docs/framework/wcf/feature-details/messaging-activities.md)。工作流程服務是使用 <xref:System.ServiceModel.Activities.WorkflowServiceHost> 類別裝載的。[!INCLUDE[crdefault](../../../includes/crdefault-md.md)][裝載工作流程服務概觀](../../../docs/framework/wcf/feature-details/hosting-workflow-services-overview.md).[!INCLUDE[crabout](../../../includes/crabout-md.md)] 工作流程服務，請參閱[工作流程服務](../../../docs/framework/wcf/feature-details/workflow-services.md)  
  
## 持續性工作流程、卸載工作流程，以及長期執行工作流程  
 Windows 工作流程透過提供下列功能，簡化長期執行反應式程式的製作：  
  
-   存取外部輸入的活動。  
  
-   建立可由主機接聽程式接續之 <xref:System.Activities.Bookmark> 物件的能力。  
  
-   能夠保存工作流程資料及卸載該工作流程，然後重新載入及重新啟動工作流程以回應 <xref:System.Activities.Bookmark> 物件在特定工作流程中繼續。  
  
 工作流程會持續執行活動，直到沒有其他可執行的活動，或者直到目前所有執行中的活動均在等候輸入為止。在第二種狀態中，工作流程是閒置的。主機卸載閒置的工作流程，並在訊息抵達時重新載入該工作流程以繼續執行，這是常見的程序。<xref:System.ServiceModel.Activities.WorkflowServiceHost> 提供此特性的功能，並且提供可延伸的卸載原則。若為使用變動性狀態資料或無法保存之資料的執行區塊，活動可以使用 <xref:System.Activities.NoPersistHandle> 指出不應保存的主機。工作流程也可以利用 <xref:System.Activities.Statements.Persist> 活動，將其資料明確地保存至長期性的儲存媒體中。