---
title: 206 - ErrorHandlerInvoked
ms.date: 03/30/2017
ms.assetid: 97340f4d-4e09-4e42-a17a-982b3868dbcf
ms.openlocfilehash: 40a92d77c57728249569a854eab8767ff371bca2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="206---errorhandlerinvoked"></a>206 - ErrorHandlerInvoked
## <a name="properties"></a>屬性  
  
|||  
|-|-|  
|識別碼|206|  
|關鍵字|Troubleshooting，ServiceModel|  
|層級|資訊|  
|通道|Microsoft-Windows-Application Server-Applications/Analytic|  
  
## <a name="description"></a>描述  
 這個事件是在 `ErrorHandler` 有機會處理服務作業中發生的例外狀況之後發出。  
  
## <a name="message"></a>訊息  
 發送器叫用類型 '%1' 的 ErrorHandler 與類型 '%3' 的例外狀況。 ErrorHandled == '%2'。  
  
## <a name="details"></a>詳細資料  
  
|資料項目名稱|資料項目型別|描述|  
|--------------------|--------------------|-----------------|  
|TypeName|`xs:string`|已叫用 `ErrorHandler` 之類型的 CLR FullName。|  
|Handled|`xs:unsignedByte`|如果錯誤處理常式已處理錯誤，則為 `true`，否則為 `false`。|  
|ExceptionTypeName|`xs:string`|已處理之例外狀況的 CLR FullName。|  
|HostReference|`xs:string`|若為 Web 託管服務，此欄位會唯一識別 Web 階層架構中的服務。 其格式定義為 ' Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'。 範例: ' Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'。|  
|AppDomain|`xs:string`|由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。|
