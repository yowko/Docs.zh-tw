---
title: "223 - OperationFaulted | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 2f7d89d7-3a6a-40fe-9610-5424eb6bbf61
caps.latest.revision: 6
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 6
---
# 223 - OperationFaulted
## 屬性  
  
|||  
|-|-|  
|ID|223|  
|關鍵字|EndToEndMonitoring，HealthMonitoring，Troubleshooting，ServiceModel|  
|層級|Warning|  
|通道|Microsoft\-Windows\-Application Server\-Applications\/Analytic|  
  
## 描述  
 當服務模型的預設 `OperationInvoker` 在叫用其方法而遭遇衍生自 `FaultException` 的例外狀況時，便會發出此事件。  
  
## 訊息  
 由 OperationInvoker 叫用時，'%1' 方法擲回 FaultException。此方法的呼叫持續時間為 '%2' 毫秒。  
  
## 詳細資料  
  
|資料項目名稱|資料項目型別|描述|  
|------------|------------|--------|  
|MethodName|`xs:string`|`OperationInvoker` 叫用之方法的 CLR 名稱。|  
|持續時間|`xs:long`|`OperationInvoker` 叫用方法所花費的時間，以毫秒為單位。|  
|HostReference|`xs:string`|若為 Web 託管服務，此欄位會唯一識別 Web 階層架構中的服務。其格式定義為 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'。範例：'Default Web Site\/CalculatorApplication&#124;\/CalculatorService.svc&#124;CalculatorService'。|  
|AppDomain|`xs:string`|由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。|