---
title: "225 - TraceCorrelationKeys | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d9083aaf-3816-4c1c-bae0-2d7f49628345
caps.latest.revision: 5
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 5
---
# 225 - TraceCorrelationKeys
## 屬性  
  
|||  
|-|-|  
|ID|225|  
|關鍵字|Troubleshooting，ServiceModel|  
|層級|資訊|  
|通道|Microsoft\-Windows\-Application Server\-Applications\/Analytic|  
  
## 描述  
 此事件是在內容架構相互關聯用於工作流程服務時發出。其中包含套用的相互關聯索引鍵，可用來讓訊息與執行個體相互關聯。  
  
## 訊息  
 在父範圍 '%3' 中使用 '%2' 值計算的相互關聯索引鍵 '%1'。  
  
## 詳細資料  
  
|資料項目名稱|資料項目型別|描述|  
|------------|------------|--------|  
|執行個體索引鍵|`xs:GUID`|產生自相互關聯值的索引鍵。|  
|值|`xs:string`|用來計算相互關聯執行個體索引鍵的值。|  
|父範圍|`xs:string`||  
|HostReference|`xs:string`|若是 Web 裝載的服務，此欄位會唯一識別 Web 階層架構中的服務。其格式定義為 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'。範例：'Default Web Site\/CalculatorApplication&#124;\/CalculatorService.svc&#124;CalculatorService'。|  
|AppDomain|`xs:string`|由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。|