---
title: Windows Workflow 概觀
description: 本文說明 Workflow Foundation 工作流程，這些工作流程是描述真實世界進程的模型。
ms.date: 03/30/2017
ms.assetid: fc44adbe-1412-49ae-81af-0298be44aae6
ms.openlocfilehash: c54e405c5fff013f994f98cbf84fcce4d17d9d4e
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90558096"
---
# <a name="windows-workflow-overview"></a>Windows Workflow 概觀
工作流程是一組稱為活動的 elemental 單位，這些 *活動* 會儲存為描述真實世界進程的模型。 工作流程能夠描述執行的順序，以及短期工作和長期工作之間的相依關係。 這個工作會從頭到尾經過整個模型，而活動可能會由人員或系統功能執行。  
  
## <a name="workflow-run-time-engine"></a>工作流程執行階段引擎  
 每個執行中的工作流程執行個體是由同處理序執行階段引擎建立與維護的，主機處理序會透過以下其中一種方式與該引擎互動：  
  
- <xref:System.Activities.WorkflowInvoker>，如同方法一般叫用工作流程。  
  
- <xref:System.Activities.WorkflowApplication>，明確控制單一工作流程執行個體的執行。  
  
- 在多個執行個體的案例中進行訊息式互動的 <xref:System.ServiceModel.WorkflowServiceHost>。  
  
 這裡每個類別都會包含核心活動執行階段，此執行階段是以負責活動執行的 <xref:System.Activities.ActivityInstance> 來表示。 在並行執行的應用程式網域內可能有幾個 <xref:System.Activities.ActivityInstance> 物件。  
  
 前三個主機互動物件是從稱為工作流程程式的活動樹狀結構中所建立。 使用這些類型或包裝的自訂主機 <xref:System.Activities.ActivityInstance> ，工作流程可以在任何 Windows 進程內部執行，包括主控台應用程式、表單架構應用程式、Windows 服務、ASP.NET 網站，以及 Windows Communication Foundation (WCF) Services。  
  
 ![主機處理序中的工作流程元件](./media/44c79d1d-178b-4487-87ed-3e33015a3842.gif "44c79d1d-178b-4487-87ed-3e33015a3842")  
主機處理序中的工作流程元件  
  
## <a name="interaction-between-workflow-components"></a>工作流程元件之間的互動  
 下圖顯示工作流程元件之間的互動方式。  
  
 ![此圖顯示工作流程元件的互動方式。](./media/overview/workflow-component-interatction.gif)  
  
 在上圖中，<xref:System.Activities.WorkflowInvoker.Invoke%2A> 類別的 <xref:System.Activities.WorkflowInvoker> 方法是用於叫用幾個工作流程執行個體。 <xref:System.Activities.WorkflowInvoker> 是用於不需要從主機管理的輕量工作流程，需要從主機 (例如 <xref:System.Activities.Bookmark> 繼續) 管理的工作流程則必須改用 <xref:System.Activities.WorkflowApplication.Run%2A> 來執行。 不一定要先等候一個工作流程完成，才能叫用另一個工作流程，執行階段引擎支援同時執行多個工作流程執行個體。  叫用的工作流程如下：  
  
- 包含 <xref:System.Activities.Statements.Sequence> 子活動的 <xref:System.Activities.Statements.WriteLine> 活動。 父活動的 <xref:System.Activities.Variable> 會繫結至子活動的 <xref:System.Activities.InArgument>。 如需有關變數、引數和系結的詳細資訊，請參閱 [變數和自](variables-and-arguments.md)變數。  
  
- 稱為 `ReadLine` 的自訂活動。 <xref:System.Activities.OutArgument> 活動的 `ReadLine` 會傳回，以呼叫 <xref:System.Activities.WorkflowInvoker.Invoke%2A> 方法。  
  
- 衍生自 <xref:System.Activities.CodeActivity>抽象類別的自訂活動。 <xref:System.Activities.CodeActivity> 可存取使用 <xref:System.Activities.CodeActivityContext> 而可用來做為 <xref:System.Activities.CodeActivity.Execute%2A> 方法之參數的執行階段功能 (例如追蹤與屬性)。 如需這些執行時間功能的詳細資訊，請參閱 [工作流程追蹤和追蹤](workflow-tracking-and-tracing.md) 和 [工作流程執行屬性](workflow-execution-properties.md)。  
  
## <a name="see-also"></a>另請參閱

- [BizTalk Server 2006 或 WF？為您的專案選擇正確的工作流程工具](/previous-versions/dotnet/articles/cc303238(v=msdn.10))
