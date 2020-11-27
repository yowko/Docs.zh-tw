---
title: 1017 - ScheduleCancelActivityWorkItem
ms.date: 03/30/2017
ms.assetid: 864546ab-d65c-4989-8fcb-537ba03a3cdd
ms.openlocfilehash: 6aed9773aa45251075520a0f955e9d71234f1357
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96275615"
---
# <a name="1017---schedulecancelactivityworkitem"></a>1017 - ScheduleCancelActivityWorkItem

## <a name="properties"></a>屬性  
  
|||  
|-|-|  
|識別碼|1017|  
|關鍵字|WFRuntime|  
|層級|「詳細資訊」|  
|通路|Microsoft-Windows-Application Server-Applications/Debug|  
  
## <a name="description"></a>描述  

 表示已排定 CancelActivityWorkItem。  
  
## <a name="message"></a>訊息  

 已排定活動 '%1'、DisplayName：'%2'、InstanceId：'%3' 的 CancelActivityWorkItem。  
  
## <a name="details"></a>詳細資料  
  
|資料項目名稱|資料項目型別|描述|  
|--------------------|--------------------|-----------------|  
|活動|xs:string|活動的型別名稱。|  
|DisplayName|xs:string|活動的顯示名稱。|  
|InstanceId|xs:string|活動的執行個體 ID。|  
|AppDomain|xs:string|由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。|
