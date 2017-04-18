---
title: "219 - ServiceException | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 81e2efac-39aa-4ed2-85a9-97eb8793b844
caps.latest.revision: 5
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 5
---
# 219 - ServiceException
## 屬性  
  
|||  
|-|-|  
|ID|219|  
|關鍵字|EndToEndMonitoring，HealthMonitoring，Troubleshooting，ServiceModel|  
|層級|Error|  
|通道|Microsoft\-Windows\-Application Server\-Applications\/Analytic|  
  
## 描述  
 當 WCF 服務遇到未處理的例外狀況時，就會發出此事件。這包含啟動期間、訊息處理期間和使用者程式碼中的未處理例外狀況。  
  
## 訊息  
 訊息處理期間發生了未處理的例外狀況 \(型別為 '%2'\)。完整例外狀況 ToString: %1。  
  
## 詳細資料  
  
|資料項目名稱|資料項目型別|描述|  
|------------|------------|--------|  
|ExceptionToString|`xs:string`|在 CLR 例外狀況上呼叫 `ToString`\(\) 的結果。|  
|ExceptionTypeName|`xs:string`|例外狀況型別的 CLR FullName。|  
|HostReference|`xs:string`|若為 Web 託管服務，此欄位會唯一識別 Web 階層架構中的服務。其格式定義為 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'。範例：'Default Web Site\/CalculatorApplication&#124;\/CalculatorService.svc&#124;CalculatorService'。|  
|AppDomain|`xs:string`|由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。|