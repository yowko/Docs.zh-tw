---
title: 213 - ServiceHostStarted
ms.date: 03/30/2017
ms.assetid: a6f7facc-342f-46bb-9d52-a470178ba6bb
ms.openlocfilehash: 87a98d30f5ecde6f81580a95e337df22341c23d4
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96279021"
---
# <a name="213---servicehoststarted"></a>213 - ServiceHostStarted

## <a name="properties"></a>屬性  
  
|||  
|-|-|  
|識別碼|213|  
|關鍵字|EndToEndMonitoring，HealthMonitoring，Troubleshooting，ServiceHost|  
|層級|LogAlways|  
|通路|Microsoft-Windows-Application Server-Applications/Analytic|  
  
## <a name="description"></a>描述  

 此事件是在 Web 裝載服務主機啟動時發出。 這種情況通常是在訊息啟動服務時發生。 此外也可能在服務設定為自動啟動時發生。  
  
## <a name="message"></a>訊息  

 ServiceHost 已啟動: '%1'。  
  
## <a name="details"></a>詳細資料  
  
|資料項目名稱|資料項目型別|描述|  
|--------------------|--------------------|-----------------|  
|服務型別名稱|`xs:string`|服務實作之型別的 CLR FullName。|  
|HostReference|`xs:string`|若是 Web 裝載的服務，此欄位會唯一識別 Web 階層架構中的服務。 其格式定義為 ' Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName '。 範例： ' Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService '。|  
|AppDomain|`xs:string`|由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。|
