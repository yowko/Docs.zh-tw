---
title: 224 - MessageThrottleAtSeventyPercent
ms.date: 03/30/2017
ms.assetid: 82bbbfd7-10d2-41fd-805d-2443b0c1b96b
ms.openlocfilehash: f70dc235e037b4f490a25866940fe2bccceae2a1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61916301"
---
# <a name="224---messagethrottleatseventypercent"></a>224 - MessageThrottleAtSeventyPercent
## <a name="properties"></a>屬性  
  
|||  
|-|-|  
|識別碼|224|  
|關鍵字|EndToEndMonitoring，HealthMonitoring，Troubleshooting，ServiceModel|  
|層級|警告|  
|通道|Microsoft-Windows-Application Server-Applications/Analytic|  
  
## <a name="description"></a>描述  
 當超出其中一個主要服務節流閥時，便會發出 `MessageThrottleExceeded` 事件。 當活動增量速度變慢且節流閥的目前值為目前限制的 70% 時，就會發出此事件。 請注意，此事件只會在活動速度變慢時發出一次。 如果目前值停在 70% 標記處 (例如 70,69,70,71,70,69)，則只會在出現第一個 70% 時發出此事件。 此事件發出之後，後續出現超出節流閥限制的情況都會造成 `MessageThrottleExceeded` 事件。  
  
## <a name="message"></a>訊息  
 '%2' 的 '%1' 節流閥限制為 70%%。  
  
## <a name="details"></a>詳細資料  
  
|資料項目名稱|資料項目型別|描述|  
|--------------------|--------------------|-----------------|  
|節流閥名稱|`xs:string`|已超出的節流閥名稱。 `MaxConcurrentCalls`、`MaxConcurrentInstances` 或 `MaxConcurrentSessions`。|  
|限制|`xs:long`|目前設定的節流閥限制。|  
|HostReference|`xs:string`|若為 Web 託管服務，此欄位會唯一識別 Web 階層架構中的服務。 其格式定義為 ' Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'。 範例：' Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'。|  
|AppDomain|`xs:string`|由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。|
