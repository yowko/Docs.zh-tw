---
title: 工作流程控制端點
ms.date: 03/30/2017
ms.assetid: 1b883334-1590-4fbb-b0d6-65197efe0700
ms.openlocfilehash: 40fec2902598daed178e070b02c1067c308507c9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33502588"
---
# <a name="workflow-control-endpoint"></a>工作流程控制端點
工作流程控制端點可讓開發人員呼叫控制作業，以便從遠端控制使用 <xref:System.ServiceModel.Activities.WorkflowServiceHost> 所裝載的工作流程執行個體。 這項功能可以使用程式設計的方式執行多種控制作業，像是暫停、繼續及終止。  
  
> [!WARNING]
>  如果在交易內使用工作流程控制端點，而且所控制的工作流程包含 <xref:System.Activities.Statements.Persist> 活動，則工作流程執行個體將會停止回應，直到交易逾時為止。  
  
## <a name="workflow-instance-management"></a>工作流程執行個體管理  
 [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] 定義了一個新合約，稱為 <xref:System.ServiceModel.Activities.IWorkflowInstanceManagement>。 這個合約定義了一系列的控制作業，可讓您從遠端控制 <xref:System.ServiceModel.Activities.WorkflowServiceHost> 裝載的工作流程執行個體。 <xref:System.ServiceModel.Activities.WorkflowControlEndpoint> 是標準的端點，提供 <xref:System.ServiceModel.Activities.IWorkflowInstanceManagement> 合約的實作。 <xref:System.ServiceModel.Activities.WorkflowControlClient> 是一個類別，用來傳送控制作業至 <xref:System.ServiceModel.Activities.WorkflowControlEndpoint>。  
  
 工作流程執行個體可能處於下列其中一種狀態：  
  
 作用中  
 工作流程執行個體尚未達到完成狀態，而且不是在暫停狀態。 處於此狀態時，工作流程執行個體將會執行及處理應用程式訊息。  
  
 擱置  
 處於此狀態時，即使有活動尚未開始執行或已執行一部分，工作流程執行個體也不會執行。  
  
 已完成  
 工作流程執行個體的最終狀態。 工作流程執行個體達到完成狀態之後，就不能再執行了。  
  
## <a name="iworkflowinstancemanagement"></a>工作流程執行個體管理  
 <xref:System.ServiceModel.Activities.IWorkflowInstanceManagement> 介面定義了一組控制作業，分為同步與非同步的版本。 交易版本需要使用交易感知繫結。 下表列出支援的控制作業。  
  
|控制作業|描述|  
|-----------------------|-----------------|  
|Abort|強制停止工作流程執行個體的執行。|  
|取消|工作流程執行個體從作用中或已暫停狀態轉換為已完成狀態。|  
|執行|為工作流程執行個體提供執行的機會。|  
|暫止|工作流程執行個體從作用中狀態轉換為已暫停狀態。|  
|結束|工作流程執行個體從作用中或已暫停狀態轉換為已完成狀態。|  
|Unsuspend|工作流程執行個體從已暫停狀態轉換為作用中狀態。|  
|TransactedCancel|執行異動 (從用戶端流動進入或在本機建立) 之下的 [取消] 作業。 如果系統會維持工作流程執行個體的長期狀態，則在此項作業執行期間工作流程執行個體必須保存。|  
|TransactedRun|執行異動 (從用戶端流動進入或在本機建立) 之下的 [執行] 作業。 如果系統會維持工作流程執行個體的長期狀態，則在此項作業執行期間工作流程執行個體必須保存。|  
|TransactedSuspend|執行交易 (從用戶端流動進入或在本機建立) 之下的 [暫停] 作業。 如果系統會維持工作流程執行個體的長期狀態，則在此項作業執行期間工作流程執行個體必須保存。|  
|TransactedTerminate|執行異動 (從用戶端流動進入或在本機建立) 之下的 [結束] 作業。 如果系統會維持工作流程執行個體的長期狀態，則在此項作業執行期間工作流程執行個體必須保存。|  
|TransactedUnsuspend|執行交易 (從用戶端流動進入或在本機建立) 之下的 [取消暫停] 作業。 如果系統會維持工作流程執行個體的長期狀態，則在此項作業執行期間工作流程執行個體必須保存。|  
  
 <xref:System.ServiceModel.Activities.IWorkflowInstanceManagement> 合約並未提供建立新工作流程執行個體的方法，只能管理現有的工作流程執行個體。 如需從遠端建立新的工作流程執行個體的詳細資訊，請參閱[工作流程服務主機擴充性](../../../../docs/framework/wcf/feature-details/workflow-service-host-extensibility.md)。  
  
## <a name="workflowcontrolendpoint"></a>WorkflowControlEndpoint  
 <xref:System.ServiceModel.Activities.WorkflowControlEndpoint> 是標準端點，含有固定合約 <xref:System.ServiceModel.Activities.IWorkflowInstanceManagement>。 將此端點加入至 <xref:System.ServiceModel.Activities.WorkflowServiceHost> 執行個體之後，可以使用此端點傳送命令作業給主機執行個體所裝載的任何工作流程執行個體。 如需標準端點的詳細資訊，請參閱[標準端點](../../../../docs/framework/wcf/feature-details/standard-endpoints.md)。  
  
## <a name="workflowcontrolclient"></a>WorkflowControlClient  
 <xref:System.ServiceModel.Activities.WorkflowControlClient> 類別可讓您傳送控制訊息至 <xref:System.ServiceModel.Activities.WorkflowControlEndpoint> 上的 <xref:System.ServiceModel.Activities.WorkflowServiceHost>。 其中包含方法，而該方法會提供給 <xref:System.ServiceModel.Activities.IWorkflowInstanceManagement> 合約所支援的各項作業 (交易的作業除外)。 <xref:System.ServiceModel.Activities.WorkflowControlClient> 會使用環境交易來判斷是否應該使用交易的作業。
