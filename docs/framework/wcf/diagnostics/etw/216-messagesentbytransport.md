---
title: 216 - MessageSentByTransport
ms.date: 03/30/2017
ms.assetid: 150c3167-4154-4225-8d94-57cc94341233
ms.openlocfilehash: b3e9e1a48951ad5a2e5e7820dc1828c20e310635
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96278904"
---
# <a name="216---messagesentbytransport"></a>216 - MessageSentByTransport

## <a name="properties"></a>屬性  
  
|||  
|-|-|  
|識別碼|216|  
|關鍵字|Troubleshooting，ServiceModel|  
|層級|資訊|  
|通路|Microsoft-Windows-Application Server-Applications/Analytic|  
  
## <a name="description"></a>描述  

 這個事件會發生在 TCP 傳輸傳送訊息時。 請注意，在傳輸層級，用戶端與服務之間可以針對單一作業交換多個訊息。 這可能是由於基礎結構行為所致，安全性就是一個很好的例子。 因此，發出的 **MessageSentByTransport** 事件數目會根據您服務的系結及其設定而有所不同。  
  
## <a name="message"></a>訊息  

 傳輸傳送了訊息至 '%1'。  
  
## <a name="details"></a>詳細資料  
  
|資料項目名稱|資料項目型別|描述|  
|--------------------|--------------------|-----------------|  
|DestinationAddress|`xs:string`|要求訊息傳送至的位址。|  
|HostReference|xs:string|若為 Web 託管服務，此欄位會唯一識別 Web 階層架構中的服務。 其格式定義為 ' Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName '。 範例： ' Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService '。|  
|AppDomain|`xs:string`|由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。|
