---
title: "220 - MessageSentToTransport | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: aef4e781-240b-45bc-bff8-400053037e71
caps.latest.revision: 6
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 6
---
# 220 - MessageSentToTransport
## 屬性  
  
|||  
|-|-|  
|ID|220|  
|關鍵字|EndToEndMonitoring，Troubleshooting，ServiceModel|  
|層級|Information|  
|通道|Microsoft\-Windows\-Application Server\-Applications\/Analytic|  
  
## 描述  
 服務模型將訊息傳送至傳輸時，便會發出此事件。  
  
> [!NOTE]
>  單向傳輸將不會發出此事件。  
  
## 訊息  
 發送器已將訊息傳送至傳輸。相互關聯 ID \=\= '%1'。  
  
## 詳細資料  
  
|資料項目名稱|資料項目型別|描述|  
|------------|------------|--------|  
|相互關聯 ID|`xs:GUID`|活動識別碼，會將來自服務或用戶端的 `MessageSentToTransport` 事件，與另一端對應的 `MessageReceivedFromTransport` 相互關聯。|  
|HostReference|`xs:string`|若為 Web 託管服務，此欄位會唯一識別 Web 階層架構中的服務。其格式定義為 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'。範例：'Default Web Site\/CalculatorApplication&#124;\/CalculatorService.svc&#124;CalculatorService'。|  
|AppDomain|`xs:string`|由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。|