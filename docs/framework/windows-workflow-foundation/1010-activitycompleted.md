---
title: 1010 - ActivityCompleted
ms.date: 03/30/2017
ms.assetid: d256284e-3fd2-4c33-82f4-abb617575706
ms.openlocfilehash: d0ebf32ec1d5fe5b34ffe650d5547891be0eb665
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96239909"
---
# <a name="1010---activitycompleted"></a>1010 - ActivityCompleted

## <a name="properties"></a>屬性  
  
|||  
|-|-|  
|識別碼|1010|  
|關鍵字|WFRuntime|  
|層級|資訊|  
|通路|Microsoft-Windows-Application Server-Applications/Debug|  
  
## <a name="description"></a>描述  

 表示活動已完成執行。  
  
## <a name="message"></a>訊息  

 活動 '%1'、DisplayName：'%2'、InstanceId：'%3' 已經以 '%4' 狀態完成。  
  
## <a name="details"></a>詳細資料  
  
|資料項目名稱|資料項目型別|描述|  
|--------------------|--------------------|-----------------|  
|活動|xs:string|活動的型別名稱。|  
|DisplayName|xs:string|活動的顯示名稱。|  
|InstanceId|xs:string|活動的執行個體 ID。|  
|州|xs:string|活動的狀態。|  
|AppDomain|xs:string|由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。|
