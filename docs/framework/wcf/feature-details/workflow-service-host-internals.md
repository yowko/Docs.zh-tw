---
title: 工作流程服務主機內部
ms.date: 03/30/2017
ms.assetid: af44596f-bf6a-4149-9f04-08d8e8f45250
ms.openlocfilehash: 0596e15e27460a08f859ec3398afbeae752c86fc
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/02/2019
ms.locfileid: "58826024"
---
# <a name="workflow-service-host-internals"></a>工作流程服務主機內部
<xref:System.ServiceModel.WorkflowServiceHost> 會提供工作流程服務的主機。 它會負責接聽傳入訊息並將訊息路由傳送至適當的工作流程服務執行個體、控制閒置工作流程的卸載和保存作業，以及其他作業。 本主題描述 WorkflowServiceHost 如何處理傳入訊息。  
  
## <a name="workflowservicehost-overview"></a>WorkflowServiceHost 概觀  

<xref:System.ServiceModel.WorkflowServiceHost> 類別是用來裝載工作流程服務。 它會接聽傳入訊息並將訊息路由傳送至適當的服務執行個體，並視需要建立新的執行個體或從永久性儲存裝置載入現有的執行個體。 下圖說明概略<xref:System.ServiceModel.WorkflowServiceHost>的運作方式： 
  
 ![顯示的工作流程服務主機概觀的圖表。](./media/workflow-service-host-internals/workflow-service-host-high-level-overview.gif)  
  
 這張圖表顯示 <xref:System.ServiceModel.WorkflowServiceHost> 會從 .xamlx 檔案載入工作流程服務定義，並且從組態檔載入組態資訊。 它也會從追蹤設定檔載入追蹤組態。 <xref:System.ServiceModel.WorkflowServiceHost> 會公開工作流程控制端點，可讓您將控制作業傳送至工作流程執行個體。  如需詳細資訊，請參閱[流程控制端點範例](../../../../docs/framework/wcf/feature-details/workflow-control-endpoint.md)。  
  
 <xref:System.ServiceModel.WorkflowServiceHost> 也會公開應用程式端點，以便接聽傳入的應用程式訊息。 當傳入訊息送達時，它就會傳送至適當的工作流程服務執行個體 (如果目前已載入的話)。 必要時，它也會建立新的工作流程執行個體。 或者，如果現有的執行個體已經保存，就會從持續性存放區載入此執行個體。  
  
## <a name="workflowservicehost-details"></a>WorkflowServiceHost 詳細資料  
 下圖顯示如何<xref:System.ServiceModel.WorkflowServiceHost>處理更多詳細資料中的訊息：  
  
 ![顯示的工作流程服務主機訊息流程的圖表。](./media/workflow-service-host-internals/workflow-service-host-message-flow.gif)  
  
 這張圖表顯示三個不同的端點：應用程式端點、工作流程控制端點和工作流程裝載端點。 應用程式端點會接收要傳送至特定工作流程執行個體的訊息。 工作流程控制端點會接聽控制作業。 工作流程裝載端點會接聽讓 <xref:System.ServiceModel.WorkflowServiceHost> 載入並執行非服務工作流程的訊息。 如圖表所示，所有訊息都會透過 WCF 執行階段處理。  工作流程執行個體節流是使用 <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentInstances%2A> 屬性來達成。 這個屬性會限制並行工作流程服務執行個體的數目。 超過此節流時，系統就會將新工作流程服務執行個體的任何其他要求或啟動已保存之工作流程執行個體的要求排入佇列。 已佇列的要求會按照 FIFO 順序來處理，不論它們是新執行個體或執行中之已保存執行個體的要求都一樣。 系統會載入主機原則資訊，以便判斷如何處理未處理的例外狀況，以及如何卸載並保存閒置的工作流程服務。 如需這些主題的詳細資訊，請參閱[How to:設定工作流程未處理的例外狀況行為，使用 WorkflowServiceHost](../../../../docs/framework/wcf/feature-details/config-workflow-unhandled-exception-workflowservicehost.md)和[How to:使用 WorkflowServiceHost 設定閒置行為](../../../../docs/framework/wcf/feature-details/how-to-configure-idle-behavior-with-workflowservicehost.md)。 工作流程執行個體是根據主機原則來保存，並在必要時重新載入。 如需有關工作流程持續性，請參閱的詳細資訊：[如何：使用 WorkflowServiceHost 設定持續性](../../../../docs/framework/wcf/feature-details/how-to-configure-persistence-with-workflowservicehost.md)，[建立長時間執行的工作流程服務](../../../../docs/framework/wcf/feature-details/creating-a-long-running-workflow-service.md)，以及[工作流程持續性](../../../../docs/framework/windows-workflow-foundation/workflow-persistence.md)。  
  
 下圖會顯示流程 workflowservicehost.open 項目呼叫時：  
  
 ![顯示流程 workflowservicehost.open 項目呼叫時的圖表。](./media/workflow-service-host-internals/workflow-service-host-open.gif)  
  
 系統會從 XAML 載入工作流程，並且建立活動樹狀。 <xref:System.ServiceModel.WorkflowServiceHost> 會瀏覽活動樹狀並建立服務說明。 然後，組態會套用至主機。 最後，主機會開始接聽傳入訊息。  
  
 下圖顯示當<xref:System.ServiceModel.WorkflowServiceHost>時收到訊息之 Receive 活動的 cancreateinstance 設定為繫結`true`:  
  
 ![決策樹狀結構，當它收到的訊息，並且 CanCreateInstance，則為 true 時，由工作流程主機使用。](./media/workflow-service-host-internals/workflow-service-host-receive-message-cancreateinstance.gif)  
  
 當訊息送達時，就會由 WCF 通道堆疊處理。 然後，系統會檢查節流並執行相互關聯查詢。 如果此訊息要傳送至現有的執行個體，就會傳遞此訊息。 如果需要建立新的執行個體，則會檢查 Receive 活動的 CanCreateInstance 屬性。 如果此屬性設定為 true，就會建立新的執行個體並傳遞此訊息。  
  
 下圖顯示當 <xref:System.ServiceModel.WorkflowServiceHost> 接收要傳送至 CanCreateInstance 設定為 false 之 Receive 活動的訊息時，它所進行的作業。  
  
 ![決策樹狀目錄中由工作流程主應用程式，當它收到的訊息，而且 CanCreateInstance 為 false。](./media/workflow-service-host-internals/workflow-service-host-receive-message.gif)  
  
 當訊息送達時，就會由 WCF 通道堆疊處理。 然後，系統會檢查節流並執行相互關聯查詢。 此訊息要傳送至現有的執行個體 (因為 CanCreateInstance 為 false)，所以系統會從持續性存放區載入執行個體、繼續使用書籤，然後工作流程便執行。  
  
> [!WARNING]
> 如果 SQL Server 設定為只在 NamedPipe 通訊協定上接聽，工作流程服務主機將無法開啟。  
  
## <a name="see-also"></a>另請參閱

- [工作流程服務](../../../../docs/framework/wcf/feature-details/workflow-services.md)
- [裝載工作流程服務](../../../../docs/framework/wcf/feature-details/hosting-workflow-services.md)
- [工作流程控制端點](../../../../docs/framework/wcf/feature-details/workflow-control-endpoint.md)
- [如何：設定工作流程未處理的例外狀況行為，使用 WorkflowServiceHost](../../../../docs/framework/wcf/feature-details/config-workflow-unhandled-exception-workflowservicehost.md)
- [建立長期執行的工作流程服務](../../../../docs/framework/wcf/feature-details/creating-a-long-running-workflow-service.md)
- [工作流程持續性](../../../../docs/framework/windows-workflow-foundation/workflow-persistence.md)
