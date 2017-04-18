---
title: "1131 - InvokeMethodUseAsyncPattern | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: eca50fa7-5276-4759-ad1c-e490b9bd1f82
caps.latest.revision: 2
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 2
---
# 1131 - InvokeMethodUseAsyncPattern
## 屬性  
  
|||  
|-|-|  
|ID|1131|  
|關鍵字|WFRuntime|  
|層級|資訊|  
|通道|Microsoft\-Windows\-Application Server\-Applications\/Debug|  
  
## 描述  
 在 CacheMetadata 步驟期間，InvokeMethod 活動指出其於叫用方法時，使用非同步模式。  
  
## 訊息  
 InvokeMethod '%1' \- 方法使用 '%2' 和 '%3' 非同步模式。  
  
## 詳細資料  
  
|資料項目名稱|資料項目型別|描述|  
|------------|------------|--------|  
|InvokeMethod|xs:string|InvokeMethod 活動的顯示名稱。|  
|BeginMethod|xs:string|Begin 方法的名稱。|  
|EndMethod|xs:string|End 方法的名稱。|  
|AppDomain|xs:string|由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。|