---
title: "工作流程裝載選項"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 37bcd668-9c5c-4e7c-81da-a1f1b3a16514
caps.latest.revision: "3"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 06d39fc37d40747eef323d83f65426e015099913
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="workflow-hosting-options"></a>工作流程裝載選項
大部分的 [!INCLUDE[wf](../../../includes/wf-md.md)] 範例是使用裝載於主控台應用程式中的工作流程，但這並不是真實世界工作流程中的實際情況。 實際商務應用程式中的工作流程會裝載在持續性程序中，可能是開發人員撰寫的 Windows 服務，或是像 [!INCLUDE[iisver](../../../includes/iisver-md.md)] 或 AppFabric 之類的伺服器應用程式。 這些方法之間差異如下。  
  
## <a name="hosting-workflows-in-iis-with-windows-appfabric"></a>在具有 Windows AppFabric 的 IIS 中裝載工作流程  
 使用具有 AppFabric 的 IIS 是工作流程的慣用主機。 使用 AppFabric 的工作流程主應用程式是 Windows 啟用服務，它會單獨由 IIS 中移除對 HTTP 的相依性。  
  
## <a name="hosting-workflows-in-iis-alone"></a>只在 IIS 中裝載工作流程  
 不建議單獨使用 [!INCLUDE[iisver](../../../includes/iisver-md.md)]，因為 AppFabric 有管理和監視工具，可協助維護執行中的應用程式。 如果有移至 AppFabric 的相關基礎結構顧慮，則工作流程應該只裝載在 [!INCLUDE[iisver](../../../includes/iisver-md.md)]。  
  
> [!WARNING]
>  [!INCLUDE[iisver](../../../includes/iisver-md.md)] 會因為各種理由定期回收應用程式集區。 回收應用程式集區時，IIS 會停止接受訊息至舊集區，並產生新的應用程式集區以接受新的要求。 如果工作流程在傳送回應之後繼續運作，[!INCLUDE[iisver](../../../includes/iisver-md.md)] 不會感知已執行的工作，且可能會回收進行裝載的應用程式集區。 如果發生這種情況，將會中止工作流程，並追蹤服務會記錄[1004-WorkflowInstanceAborted](../../../docs/framework/windows-workflow-foundation/1004-workflowinstanceaborted.md)空白的 [原因] 欄位的訊息。  
>   
>  如果使用持續性，主機必須從上次的保存點，明確地將中止的執行個體重新啟動。  
>   
>  如果使用 AppFabric，工作流程管理服務最後會從上次的成功保存點 (如果使用持續性) 繼續工作流程。 如果沒有使用持續性，而且工作流程不是以「要求/回應」模式執行作業，資料將會在工作流程中止時遺失。  
  
## <a name="hosting-a-workflow-in-a-custom-windows-service"></a>在自訂 Windows 服務中裝載工作流程  
 建立自訂工作流程服務來裝載工作流程，需要開發人員重複許多由 AppFabric 提供的全新功能，不過在自訂功能方面較有彈性。 唯有確定 AppFabric 不是選項時，才能考慮此選項。
