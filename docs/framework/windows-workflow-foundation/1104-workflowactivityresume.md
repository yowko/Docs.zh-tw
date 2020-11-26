---
title: 1104 - WorkflowActivityResume
ms.date: 03/30/2017
ms.assetid: 7fe95d1e-34bd-43ca-b92e-587d2d248fff
ms.openlocfilehash: 2a9c40e2c403d43dc980af116e4b6e98b3b2090b
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96243556"
---
# <a name="1104---workflowactivityresume"></a>1104 - WorkflowActivityResume

## <a name="properties"></a>屬性  
  
|||  
|-|-|  
|識別碼|1104|  
|關鍵字|WFRuntime|  
|層級|資訊|  
|通路|Microsoft-Windows-Application Server-Applications/Debug|  
  
## <a name="description"></a>描述  

 表示已繼續工作流程活動。  
  
## <a name="message"></a>訊息  

 WorkflowInstance Id：'%1' E2E 活動  
  
## <a name="details"></a>詳細資料  
  
|資料項目名稱|資料項目型別|描述|  
|--------------------|--------------------|-----------------|  
|WorkflowInstanceId|xs:string|工作流程執行個體 ID。|  
|AppDomain|xs:string|由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。|
