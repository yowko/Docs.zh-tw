---
title: "1132 - InvokeMethodDoesNotUseAsyncPattern | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 436b3767-4460-46b0-9ea3-fc2963260c11
caps.latest.revision: 2
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 2
---
# 1132 - InvokeMethodDoesNotUseAsyncPattern
## 屬性  
  
|||  
|-|-|  
|ID|1132|  
|關鍵字|WFRuntime|  
|層級|資訊|  
|通道|Microsoft\-Windows\-Application Server\-Applications\/Debug|  
  
## 描述  
 在 CacheMetadata 步驟期間，InvokeMethod 活動表示其於叫用方法時，未使用非同步模式。  
  
## 訊息  
 InvokeMethod '%1' \- 方法未使用非同步模式。  
  
## 詳細資料  
  
|資料項目名稱|資料項目型別|描述|  
|------------|------------|--------|  
|InvokeMethod|xs:string|InvokeMethod 活動的顯示名稱。|  
|AppDomain|xs:string|由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。|