---
title: 301 - UserDefinedErrorOccurred
ms.date: 03/30/2017
ms.assetid: a0285d1c-550f-4c14-9c36-a96e97f1c4e4
ms.openlocfilehash: 2c3ff1905a1d17413211246f5b3cc156bcbb7320
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96243452"
---
# <a name="301---userdefinederroroccurred"></a>301 - UserDefinedErrorOccurred

## <a name="properties"></a>屬性  
  
|||  
|-|-|  
|識別碼|301|  
|關鍵字|Troubleshooting，HealthMonitoring，UserEvents，ServiceModel，EndToEndMonitoring|  
|層級|錯誤|  
|通路|Microsoft-Windows-Application Server-Applications/Analytic|  
  
## <a name="description"></a>描述  

 此事件是由使用者程式碼所發出。 當開發人員的服務中發生自訂定義錯誤時，可能會發出此事件。 這項操作可使用 <xref:System.Diagnostics.Eventing> API 達到目的。 另外還有 WCF 範例，可包裝該 API 並示範如何正確發出此事件。  
  
## <a name="message"></a>訊息  

 名稱:'%1'，參考:'%2'，承載:%3。  
  
## <a name="details"></a>詳細資料  
  
|資料項目名稱|資料項目型別|描述|  
|--------------------|--------------------|-----------------|  
|Name|`xs:string`|使用者定義的事件名稱。|  
|HostReference|`xs:string`|若為 Web 託管服務，此欄位會唯一識別 Web 階層架構中的服務。 其格式定義為 ' Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName '。 範例： ' Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService '。|  
|Payload|`xs:string`|使用者定義的事件裝載。|
