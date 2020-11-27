---
title: 440 - StartSignpostEvent1
ms.date: 03/30/2017
ms.assetid: 27b551b5-ae76-49f8-bab8-6300009eb4c1
ms.openlocfilehash: 1e0278d665a961afab21445ab8490e3e5a94987c
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96293451"
---
# <a name="440---startsignpostevent1"></a>440 - StartSignpostEvent1

## <a name="properties"></a>屬性  
  
|||  
|-|-|  
|識別碼|440|  
|關鍵字|疑難排解|  
|層級|資訊|  
|通路|Microsoft-Windows-Application Server-Applications/Analytic|  
  
## <a name="description"></a>描述  

 在活動追蹤中，表示訊息已開始在傳送或接收終跨越活動界限。  
  
## <a name="message"></a>訊息  

 活動界限。  
  
## <a name="details"></a>詳細資料  
  
|資料項目名稱|資料項目型別|描述|  
|--------------------|--------------------|-----------------|  
|ExtendedData|`xs:string`|活動名稱。|  
|AppDomain|`xs:string`|由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。|
