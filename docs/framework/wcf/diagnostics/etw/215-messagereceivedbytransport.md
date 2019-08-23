---
title: 215 - MessageReceivedByTransport
ms.date: 03/30/2017
ms.assetid: bb32aa60-5207-4711-9f08-110e8ac327e5
ms.openlocfilehash: aa1ad30526aa65501e5d9875d3877631ca00879b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964180"
---
# <a name="215---messagereceivedbytransport"></a>215 - MessageReceivedByTransport
## <a name="properties"></a>屬性  
  
|||  
|-|-|  
|id|215|  
|關鍵字|Troubleshooting，ServiceModel|  
|層級|內容|  
|通道|Microsoft-Windows-Application Server-Applications/Analytic|  
  
## <a name="description"></a>描述  
 此事件會在 TCP 傳輸接收訊息時發生。 請注意，在傳輸層級，用戶端與服務之間可以針對單一作業交換多個訊息。 這可能是由於基礎結構行為所致，安全性就是一個很好的例子。 因此，發出的 `MessageReceivedByTransport` 事件數目會根據服務的繫結及其組態而有所不同。  
  
> [!NOTE]
> 單向傳輸不會發出此事件。  
  
## <a name="message"></a>訊息  
 傳輸收到來自 '%1' 的訊息。  
  
## <a name="details"></a>詳細資料  
  
|資料項目名稱|資料項目型別|描述|  
|--------------------|--------------------|-----------------|  
|ListenAddress|`xs:string`|收到訊息的位址。|  
|HostReference|`xs:string`|若為 Web 託管服務，此欄位會唯一識別 Web 階層架構中的服務。 其格式定義為 ' 網站名稱應用程式虛擬路徑&#124;服務虛擬路徑&#124;ServiceName '。 範例：' Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService '。|  
|AppDomain|`xs:string`|由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。|
