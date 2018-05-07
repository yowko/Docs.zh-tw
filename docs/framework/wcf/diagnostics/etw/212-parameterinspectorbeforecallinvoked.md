---
title: 212 - ParameterInspectorBeforeCallInvoked
ms.date: 03/30/2017
ms.assetid: 063fc8d2-ceac-4c18-8368-de84f2c78035
ms.openlocfilehash: 02d4a4ed1e96983e132a1943dd39f9f885e5596a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="212---parameterinspectorbeforecallinvoked"></a>212 - ParameterInspectorBeforeCallInvoked
## <a name="properties"></a>屬性  
  
|||  
|-|-|  
|識別碼|212|  
|關鍵字|Troubleshooting，ServiceModel|  
|層級|資訊|  
|通道|Microsoft-Windows-Application Server-Applications/Analytic|  
  
## <a name="description"></a>描述  
 服務模型已在 `BeforeCall` 上叫用 `ParameterInspector` 方法之後，即會發出此事件。  
  
## <a name="message"></a>訊息  
 發送器在型別 '%1' 的 ParameterInspector 上叫用了 'BeforeCall'。  
  
## <a name="details"></a>詳細資料  
  
|資料項目名稱|資料項目型別|描述|  
|--------------------|--------------------|-----------------|  
|TypeName|`xs:string`|叫用之偵測器型別的 CLR FullName。|  
|HostReference|`xs:string`|若為 Web 託管服務，此欄位會唯一識別 Web 階層架構中的服務。 其格式定義為 ' Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'。 範例: ' Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'。|  
|AppDomain|`xs:string`|由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。|
