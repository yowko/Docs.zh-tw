---
title: 1008 - WorkflowApplicationUnloaded
ms.date: 03/30/2017
ms.assetid: a605b780-4a7e-43ab-92e7-0a3b01d053b0
ms.openlocfilehash: 6ea121e7901d877d4f0d8f9f5bfd259c2f93696d
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96239817"
---
# <a name="1008---workflowapplicationunloaded"></a>1008 - WorkflowApplicationUnloaded

## <a name="properties"></a>屬性  
  
|||  
|-|-|  
|識別碼|1008|  
|關鍵字|WFRuntime|  
|層級|資訊|  
|通路|Microsoft-Windows-Application Server-Applications/Debug|  
  
## <a name="description"></a>描述  

 表示工作流程應用程式已卸載。  
  
## <a name="message"></a>訊息  

 WorkflowInstance Id：'%1' 已卸載。  
  
## <a name="details"></a>詳細資料  
  
|資料項目名稱|資料項目型別|描述|  
|--------------------|--------------------|-----------------|  
|WorkflowInstanceId|`xs:string`|工作流程的執行個體 ID。|  
|AppDomain|`xs:string`|由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。|
