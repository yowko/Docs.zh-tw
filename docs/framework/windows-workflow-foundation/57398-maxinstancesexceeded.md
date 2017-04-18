---
title: "57398 - MaxInstancesExceeded | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f943d209-dfeb-43e5-b572-c9a06217936e
caps.latest.revision: 2
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 2
---
# 57398 - MaxInstancesExceeded
## 屬性  
  
|||  
|-|-|  
|ID|57398|  
|關鍵字|WFServices|  
|層級|警告|  
|通道|Microsoft\-Windows\-Application Server\-Applications\/Analytic|  
  
## 描述  
 表示系統已到達針對 'MaxConcurrentInstances' 節流所設定的限制。  
  
## 訊息  
 系統已到達針對 'MaxConcurrentInstances' 節流所設定的限制。  此節流的限制設為 %1。  若要變更節流值，請修改 serviceThrottle 元素中的屬性 'maxConcurrentInstances'，或修改行為 ServiceThrottlingBehavior 的 'MaxConcurrentInstances' 屬性。  
  
## 詳細資料  
  
|資料項目名稱|資料項目型別|描述|  
|------------|------------|--------|  
|名稱|xs:string|項目的名稱。|  
|AppDomain|xs:string|由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。|