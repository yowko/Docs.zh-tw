---
title: 303 - UserDefinedInformationEventOccured
ms.date: 03/30/2017
ms.assetid: 5ed5acaf-3755-4417-92c4-4ebc8e854ca1
ms.openlocfilehash: 0b782b5ac0527b5acb3ebf0bf11c117563042495
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33459136"
---
# <a name="303---userdefinedinformationeventoccured"></a>303 - UserDefinedInformationEventOccured
## <a name="properties"></a>屬性  
  
|||  
|-|-|  
|識別碼|303|  
|關鍵字|Troubleshooting，HealthMonitoring，UserEvents，ServiceModel，EndToEndMonitoring|  
|層級|資訊|  
|通道|Microsoft-Windows-Application Server-Applications/Analytic|  
  
## <a name="description"></a>描述  
 此事件是由使用者程式碼所發出。 當自定義資訊事件在開發人員的服務中發生時，他們可以發出此事件。 這項操作可使用 <xref:System.Diagnostics.Eventing> API 達到目的。 另外還有 WCF 範例，可包裝該 API 並示範如何正確發出此事件。  
  
## <a name="message"></a>訊息  
 名稱:'%1'，參考:'%2'，承載:%3。  
  
## <a name="details"></a>詳細資料  
  
|資料項目名稱|資料項目型別|描述|  
|--------------------|--------------------|-----------------|  
|名稱|`xs:string`|使用者定義的事件名稱|  
|HostReference|`xs:string`|若是 Web 裝載的服務，此欄位會唯一識別 Web 階層架構中的服務。 其格式定義為 ' Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'。 範例: ' Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'。|  
|承載|`xs:string`|使用者定義的事件裝載。|
