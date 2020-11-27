---
title: 1016 - CompleteCompletionWorkItem
ms.date: 03/30/2017
ms.assetid: 246929fb-6f14-440a-814b-cd8349350644
ms.openlocfilehash: a192ffe19777ca3e2e9784f6506a0c2929ced000
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96275527"
---
# <a name="1016---completecompletionworkitem"></a>1016 - CompleteCompletionWorkItem

## <a name="properties"></a>屬性  
  
|||  
|-|-|  
|識別碼|1016|  
|關鍵字|WFRuntime|  
|層級|「詳細資訊」|  
|通路|Microsoft-Windows-Application Server-Applications/Debug|  
  
## <a name="description"></a>描述  

 表示 CompletionWorkItem 已完成。  
  
## <a name="message"></a>訊息  

 已完成父活動 '%1'、DisplayName：'%2'、InstanceId：'%3' 的 CompletionWorkItem。 已完成活動 '%4'、DisplayName：'%5'、InstanceId：'%6'。  
  
## <a name="details"></a>詳細資料  
  
|資料項目名稱|資料項目型別|描述|  
|--------------------|--------------------|-----------------|  
|ParentActivity|xs:string|父活動的型別名稱。|  
|ParentDisplayName|xs:string|父活動的顯示名稱。|  
|ParentInstanceId|xs:string|父活動的執行個體 ID。|  
|CompletedActivity|xs:string|已完成之活動的型別名稱。|  
|CompletedActivityDisplayName|xs:string|已完成之活動的顯示名稱。|  
|CompletedActivityInstanceId|xs:string|已完成之活動的執行個體 ID。|  
|AppDomain|xs:string|由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。|
