---
title: 1019 - CompleteCancelActivityWorkItem
ms.date: 03/30/2017
ms.assetid: 75a4a1ab-e5a3-4f4e-88e4-d19806e671d7
ms.openlocfilehash: 903b497fb3f244fd40c6888829ef71dddd455251
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96275475"
---
# <a name="1019---completecancelactivityworkitem"></a>1019 - CompleteCancelActivityWorkItem

## <a name="properties"></a>屬性  
  
|||  
|-|-|  
|識別碼|1019|  
|關鍵字|WFRuntime|  
|層級|「詳細資訊」|  
|通路|Microsoft-Windows-Application Server-Applications/Debug|  
  
## <a name="description"></a>描述  

 表示 CancelActivityWorkItem 已完成。  
  
## <a name="message"></a>訊息  

 已完成活動 '%1'、DisplayName：'%2'、InstanceId：'%3' 的 CancelActivityWorkItem。  
  
## <a name="details"></a>詳細資料  
  
|資料項目名稱|資料項目型別|描述|  
|--------------------|--------------------|-----------------|  
|活動|xs:string|活動的型別名稱。|  
|DisplayName|xs:string|活動的顯示名稱。|  
|InstanceId|xs:string|活動的執行個體 ID。|  
|AppDomain|xs:string|由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。|
