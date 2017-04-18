---
title: "工作流程服務主機內部 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: af44596f-bf6a-4149-9f04-08d8e8f45250
caps.latest.revision: 5
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 5
---
# 工作流程服務主機內部
<xref:System.ServiceModel.WorkflowServiceHost> 會提供工作流程服務的主機。它會負責接聽傳入訊息並將訊息路由傳送至適當的工作流程服務執行個體、控制閒置工作流程的卸載和保存作業，以及其他作業。本主題描述 WorkflowServiceHost 如何處理傳入訊息。  
  
## WorkflowServiceHost 概觀  
 <xref:System.ServiceModel.WorkflowServiceHost> 類別是用來裝載工作流程服務。它會接聽傳入訊息並將訊息路由傳送至適當的服務執行個體，並視需要建立新的執行個體或從永久性儲存裝置載入現有的執行個體。下圖概略說明 <xref:System.ServiceModel.WorkflowServiceHost> 的運作方式。  
  
 ![WorkflowServiceHost 概觀](../../../../docs/framework/wcf/feature-details/media/wfshhighlevel.gif "WFSHHighLevel")  
  
 這張圖表顯示 <xref:System.ServiceModel.WorkflowServiceHost> 會從 .xamlx 檔案載入工作流程服務定義，並且從組態檔載入組態資訊。它也會從追蹤設定檔載入追蹤組態。<xref:System.ServiceModel.WorkflowServiceHost> 會公開工作流程控制端點，可讓您將控制作業傳送至工作流程執行個體。如需詳細資訊，請參閱[工作流程控制端點](../../../../docs/framework/wcf/feature-details/workflow-control-endpoint.md)和[工作流程管理端點範例](../../../../docs/framework/windows-workflow-foundation/samples/workflow-management-endpoint-sample.md)。  
  
 <xref:System.ServiceModel.WorkflowServiceHost> 也會公開應用程式端點，以便接聽傳入的應用程式訊息。當傳入訊息送達時，它就會傳送至適當的工作流程服務執行個體 \(如果目前已載入的話\)。必要時，它也會建立新的工作流程執行個體。或者，如果現有的執行個體已經保存，就會從持續性存放區載入此執行個體。  
  
## WorkflowServiceHost 詳細資料  
 下圖稍微詳細說明 <xref:System.ServiceModel.WorkflowServiceHost> 如何處理訊息。  
  
 ![工作流程服務主控台訊息流程](../../../../docs/framework/wcf/feature-details/media/wfshmessageflow.gif "WFSHMessageFlow")  
  
 這張圖表顯示三個不同的端點：應用程式端點、工作流程控制端點和工作流程裝載端點。應用程式端點會接收要傳送至特定工作流程執行個體的訊息。工作流程控制端點會接聽控制作業。工作流程裝載端點會接聽讓 <xref:System.ServiceModel.WorkflowServiceHost> 載入並執行非服務工作流程的訊息。如圖表所示，所有訊息都會透過 WCF 執行階段處理。工作流程執行個體節流是使用 <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentInstances%2A> 屬性來達成。這個屬性會限制並行工作流程服務執行個體的數目。超過此節流時，系統就會將新工作流程服務執行個體的任何其他要求或啟動已保存之工作流程執行個體的要求排入佇列。已佇列的要求會按照 FIFO 順序來處理，不論它們是新執行個體或執行中之已保存執行個體的要求都一樣。然後，系統會載入主機原則資訊，以便判斷如何處理未處理的例外狀況，以及如何卸載並保存閒置的工作流程服務。[!INCLUDE[crabout](../../../../includes/crabout-md.md)]這些主題的詳細資訊，請參閱 [HOW TO：以 WorkflowServiceHost 設定工作流程服務的未處理例外狀況行為](../../../../docs/framework/wcf/feature-details/config-workflow-unhandled-exception-workflowservicehost.md)和 [HOW TO：以 WorkflowServiceHost 設定閒置行為](../../../../docs/framework/wcf/feature-details/how-to-configure-idle-behavior-with-workflowservicehost.md)。工作流程執行個體是根據主機原則來保存，並在必要時重新載入。如需工作流程持續性的詳細資訊，請參閱：[HOW TO：以 WorkflowServiceHost 設定持續性](../../../../docs/framework/wcf/feature-details/how-to-configure-persistence-with-workflowservicehost.md)、[建立長期執行的工作流程服務](../../../../docs/framework/wcf/feature-details/creating-a-long-running-workflow-service.md)和[工作流程持續性](../../../../docs/framework/windows-workflow-foundation//workflow-persistence.md)。  
  
 下圖顯示所呼叫的 WorkflowServiceHost.Open 項目。  
  
 ![當呼叫 WorkflowServiceHost.Open 時](../../../../docs/framework/wcf/feature-details/media/wfhostopen.gif "WFHostOpen")  
  
 系統會從 XAML 載入工作流程，並且建立活動樹狀結構。<xref:System.ServiceModel.WorkflowServiceHost> 會瀏覽活動樹狀結構並建立服務描述。然後，組態會套用至主機。最後，主機會開始接聽傳入訊息。  
  
 下圖顯示當 <xref:System.ServiceModel.WorkflowServiceHost> 接收要傳送至 CanCreateInstance 設定為 `true` 之 Receive 活動的訊息時，它所進行的作業。  
  
 ![工作流程服務主控台收到訊息](../../../../docs/framework/wcf/feature-details/media/wfhreceivemessagecci.gif "WFHReceiveMessageCCI")  
  
 當訊息送達時，就會由 WCF 通道堆疊處理。然後，系統會檢查節流並執行相互關聯查詢。如果此訊息要傳送至現有的執行個體，就會傳遞此訊息。如果需要建立新的執行個體，則會檢查 Receive 活動的 CanCreateInstance 屬性。如果此屬性設定為 true，就會建立新的執行個體並傳遞此訊息。  
  
 下圖顯示當 <xref:System.ServiceModel.WorkflowServiceHost> 接收要傳送至 CanCreateInstance 設定為 false 之 Receive 活動的訊息時，它所進行的作業。  
  
 ![WorkflowServiceHost 收到訊息](../../../../docs/framework/wcf/feature-details/media/wfshreceivemessage.gif "WFSHReceiveMessage")  
  
 當訊息送達時，就會由 WCF 通道堆疊處理。然後，系統會檢查節流並執行相互關聯查詢。此訊息要傳送至現有的執行個體 \(因為 CanCreateInstance 為 false\)，所以系統會從持續性存放區載入執行個體、繼續使用書籤，然後工作流程便執行。  
  
> [!WARNING]
>  如果 SQL Server 設定為只在 NamedPipe 通訊協定上接聽，工作流程服務主機將無法開啟。  
  
## 請參閱  
 [工作流程服務](../../../../docs/framework/wcf/feature-details/workflow-services.md)   
 [裝載工作流程服務](../../../../docs/framework/wcf/feature-details/hosting-workflow-services.md)   
 [工作流程控制端點](../../../../docs/framework/wcf/feature-details/workflow-control-endpoint.md)   
 [工作流程管理端點範例](../../../../docs/framework/windows-workflow-foundation/samples/workflow-management-endpoint-sample.md)   
 [HOW TO：以 WorkflowServiceHost 設定工作流程服務的未處理例外狀況行為](../../../../docs/framework/wcf/feature-details/config-workflow-unhandled-exception-workflowservicehost.md)   
 [建立長期執行的工作流程服務](../../../../docs/framework/wcf/feature-details/creating-a-long-running-workflow-service.md)   
 [工作流程持續性](../../../../docs/framework/windows-workflow-foundation//workflow-persistence.md)