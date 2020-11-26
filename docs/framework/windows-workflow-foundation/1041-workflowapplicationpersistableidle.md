---
title: 1041 - WorkflowApplicationPersistableIdle
ms.date: 03/30/2017
ms.assetid: 966adf2f-e21d-44df-a3ec-a8e285e0a316
ms.openlocfilehash: 9995823753fc78ca3f278cd635fcf6c7d2b84325
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96238934"
---
# <a name="1041---workflowapplicationpersistableidle"></a>1041 - WorkflowApplicationPersistableIdle

## <a name="properties"></a>屬性  
  
|||  
|-|-|  
|識別碼|1041|  
|關鍵字|WFRuntime|  
|層級|資訊|  
|通路|Microsoft-Windows-Application Server-Applications/Debug|  
  
## <a name="description"></a>描述  

 表示工作流程應用程式處於閒置狀態且為永續性。 工作流程應用程式將會閒置或持續。  
  
## <a name="message"></a>訊息  

 WorkflowApplication 識別碼： ' %1 ' 為閒置和永久性。  將採取下列動作： %2。  
  
## <a name="details"></a>詳細資料  
  
|資料項目名稱|資料項目型別|描述|  
|--------------------|--------------------|-----------------|  
|WorkflowApplicationId|xs:string|工作流程應用程式 ID|  
|ActionTaken|xs:string|將要對工作流程應用程式要採取的動作。|  
|AppDomain|xs:string|由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。|
