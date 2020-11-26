---
title: 1003 - WorkflowInstanceCanceled
ms.date: 03/30/2017
ms.assetid: 64754dc2-c160-4bf3-869a-13d56694e2dc
ms.openlocfilehash: bd8abf173ab6588d4a35ba59c6cd14fb53445e9f
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96239896"
---
# <a name="1003---workflowinstancecanceled"></a>1003 - WorkflowInstanceCanceled

## <a name="properties"></a>屬性  
  
|||  
|-|-|  
|識別碼|1003|  
|關鍵字|WFRuntime|  
|層級|資訊|  
|通路|Microsoft-Windows-Application Server-Applications/Debug|  
  
## <a name="description"></a>描述  

 表示工作流程執行個體已在 Canceled 狀態中完成。  
  
## <a name="message"></a>訊息  

 WorkflowInstance Id：'%1' 已在 Canceled 狀態中完成。  
  
## <a name="details"></a>詳細資料  
  
|資料項目名稱|資料項目型別|描述|  
|--------------------|--------------------|-----------------|  
|WorkflowInstanceId|`xs:string`|工作流程的執行個體 ID。|  
|AppDomain|`xs:string`|由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。|
