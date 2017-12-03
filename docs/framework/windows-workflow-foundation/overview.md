---
title: "Windows Workflow 概觀"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fc44adbe-1412-49ae-81af-0298be44aae6
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: b74ecc3363e84d006d82ecb14accbf40de7e2738
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="windows-workflow-overview"></a>Windows Workflow 概觀
工作流程是一組元素的單元*活動*，會儲存為描述真實世界的處理序模型。 工作流程能夠描述執行的順序，以及短期工作和長期工作之間的相依關係。 這個工作會從頭到尾經過整個模型，而活動可能會由人員或系統功能執行。  
  
## <a name="workflow-run-time-engine"></a>工作流程執行階段引擎  
 每個執行中的工作流程執行個體是由同處理序執行階段引擎建立與維護的，主機處理序會透過以下其中一種方式與該引擎互動：  
  
-   <xref:System.Activities.WorkflowInvoker>，如同方法一般叫用工作流程。  
  
-   <xref:System.Activities.WorkflowApplication>，明確控制單一工作流程執行個體的執行。  
  
-   在多個執行個體的案例中進行訊息式互動的 <xref:System.ServiceModel.WorkflowServiceHost>。  
  
 這裡每個類別都會包含核心活動執行階段，此執行階段是以負責活動執行的 <xref:System.Activities.ActivityInstance> 來表示。 在並行執行的應用程式網域內可能有幾個 <xref:System.Activities.ActivityInstance> 物件。  
  
 前三個主機互動物件是從稱為工作流程程式的活動樹狀結構中所建立。 使用這些型別或包含的 <xref:System.Activities.ActivityInstance> 自訂主機，工作流程即可在任何 Windows 處理序內部執行，包括主控台應用程式、表單架構應用程式、Windows 服務、[!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] 網站和 [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] 服務。  
  
 ![在主控件程序中的工作流程元件](../../../docs/framework/windows-workflow-foundation/media/44c79d1d-178b-4487-87ed-3e33015a3842.gif "44c79d1d-178b-4487-87ed-3e33015a3842")  
主機處理序中的工作流程元件  
  
## <a name="interaction-between-workflow-components"></a>工作流程元件之間的互動  
 下圖顯示工作流程元件之間的互動方式。  
  
 ![工作流程互動](../../../docs/framework/windows-workflow-foundation/media/workflowinteraction.gif "WorkflowInteraction")  
  
 在上圖中，<xref:System.Activities.WorkflowInvoker.Invoke%2A> 類別的 <xref:System.Activities.WorkflowInvoker> 方法是用於叫用幾個工作流程執行個體。 <xref:System.Activities.WorkflowInvoker> 是用於不需要從主機管理的輕量工作流程，需要從主機 (例如 <xref:System.Activities.Bookmark> 繼續) 管理的工作流程則必須改用 <xref:System.Activities.WorkflowApplication.Run%2A> 來執行。 不一定要先等候一個工作流程完成，才能叫用另一個工作流程，執行階段引擎支援同時執行多個工作流程執行個體。  叫用的工作流程如下：  
  
-   包含 <xref:System.Activities.Statements.Sequence> 子活動的 <xref:System.Activities.Statements.WriteLine> 活動。 父活動的 <xref:System.Activities.Variable> 會繫結至子活動的 <xref:System.Activities.InArgument>。 [!INCLUDE[crabout](../../../includes/crabout-md.md)]變數、 引數，以及繫結，請參閱[變數和引數](../../../docs/framework/windows-workflow-foundation/variables-and-arguments.md)。  
  
-   稱為 `ReadLine` 的自訂活動。 <xref:System.Activities.OutArgument> 活動的 `ReadLine` 會傳回，以呼叫 <xref:System.Activities.WorkflowInvoker.Invoke%2A> 方法。  
  
-   衍生自 <xref:System.Activities.CodeActivity>抽象類別的自訂活動。 <xref:System.Activities.CodeActivity> 可存取使用 <xref:System.Activities.CodeActivityContext> 而可用來做為 <xref:System.Activities.CodeActivity.Execute%2A> 方法之參數的執行階段功能 (例如追蹤與屬性)。 [!INCLUDE[crabout](../../../includes/crabout-md.md)]這些執行階段功能，請參閱[工作流程追蹤](../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)和[工作流程執行屬性](../../../docs/framework/windows-workflow-foundation/workflow-execution-properties.md)。  
  
## <a name="see-also"></a>另請參閱  
 [BizTalk Server 2006 或 WF？為您的專案選擇正確的工作流程工具](http://go.microsoft.com/fwlink/?LinkId=154901)
