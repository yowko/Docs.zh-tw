---
title: 223 - OperationFaulted
ms.date: 03/30/2017
ms.assetid: 2f7d89d7-3a6a-40fe-9610-5424eb6bbf61
ms.openlocfilehash: cf4a455d80a1a0ac09e99bad967c1feba3653842
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="223---operationfaulted"></a>223 - OperationFaulted
## <a name="properties"></a>屬性  
  
|||  
|-|-|  
|識別碼|223|  
|關鍵字|EndToEndMonitoring，HealthMonitoring，Troubleshooting，ServiceModel|  
|層級|警告|  
|通道|Microsoft-Windows-Application Server-Applications/Analytic|  
  
## <a name="description"></a>描述  
 當服務模型的預設 `OperationInvoker` 在叫用其方法而遭遇衍生自 `FaultException` 的例外狀況時，便會發出此事件。  
  
## <a name="message"></a>訊息  
 由 OperationInvoker 叫用時，'%1' 方法擲回 FaultException。 此方法的呼叫持續時間為 '%2' 毫秒。  
  
## <a name="details"></a>詳細資料  
  
|資料項目名稱|資料項目型別|描述|  
|--------------------|--------------------|-----------------|  
|MethodName|`xs:string`|`OperationInvoker` 叫用之方法的 CLR 名稱。|  
|持續期間|`xs:long`|`OperationInvoker` 叫用方法所花費的時間，以毫秒為單位。|  
|HostReference|`xs:string`|若為 Web 託管服務，此欄位會唯一識別 Web 階層架構中的服務。 其格式定義為 ' Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'。 範例: ' Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'。|  
|AppDomain|`xs:string`|由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。|
