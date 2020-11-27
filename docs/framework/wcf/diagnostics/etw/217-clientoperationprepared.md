---
title: 217 - ClientOperationPrepared
ms.date: 03/30/2017
ms.assetid: ad207f04-b038-4f33-95e9-27a361df8ecd
ms.openlocfilehash: e8aaf65bdff0718e932d07937e052541b7134f11
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96278878"
---
# <a name="217---clientoperationprepared"></a>217 - ClientOperationPrepared

## <a name="properties"></a>屬性  
  
|||  
|-|-|  
|識別碼|217|  
|關鍵字|Troubleshooting，ServiceModel|  
|層級|資訊|  
|通路|Microsoft-Windows-Application Server-Applications/Analytic|  
  
## <a name="description"></a>描述  

 此事件由用戶端在作業傳送至服務之前發出。  
  
## <a name="message"></a>訊息  

 用戶端正在執行與 '%2' 合約相關聯的動作 '%1'。 訊息將傳送至 '%3'。  
  
## <a name="details"></a>詳細資料  
  
|資料項目名稱|資料項目型別|描述|  
|--------------------|--------------------|-----------------|  
|動作|`xs:string`|傳出訊息的 SOAP 動作標頭。|  
|合約名稱|`xs:string`|合約的名稱。 範例：ICalculator。|  
|Destination|`xs:string`|訊息將傳送至該處的服務端點位址。|  
|HostReference|`xs:string`|若為 Web 託管服務，此欄位會唯一識別 Web 階層架構中的服務。 其格式定義為 ' Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName '。 範例： ' Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService '。|  
|AppDomain|`xs:string`|由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。|
