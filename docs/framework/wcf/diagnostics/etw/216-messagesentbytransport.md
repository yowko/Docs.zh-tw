---
title: "216 - MessageSentByTransport | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 150c3167-4154-4225-8d94-57cc94341233
caps.latest.revision: 6
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 6
---
# 216 - MessageSentByTransport
## 屬性  
  
|||  
|-|-|  
|ID|216|  
|關鍵字|Troubleshooting，ServiceModel|  
|層級|資訊|  
|通道|Microsoft\-Windows\-Application Server\-Applications\/Analytic|  
  
## 描述  
 這個事件會發生在 TCP 傳輸傳送訊息時。請注意，在傳輸層級，用戶端與服務之間可以針對單一作業交換多個訊息。這可能是由於基礎結構行為所致，安全性就是一個很好的例子。因此，發出 **MessageSentByTransport** 事件的數目，會由於服務的繫結及其組態而有所不同。  
  
## 訊息  
 傳輸傳送了訊息至 '%1'。  
  
## 詳細資料  
  
|資料項目名稱|資料項目型別|描述|  
|------------|------------|--------|  
|DestinationAddress|`xs:string`|要求訊息傳送至的位址。|  
|HostReference|xs:string|若為 Web 託管服務，此欄位會唯一識別 Web 階層架構中的服務。其格式定義為 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'。範例：'Default Web Site\/CalculatorApplication&#124;\/CalculatorService.svc&#124;CalculatorService'。|  
|AppDomain|`xs:string`|由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。|