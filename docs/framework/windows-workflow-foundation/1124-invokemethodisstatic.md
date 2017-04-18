---
title: "1124 - InvokeMethodIsStatic | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b9643641-fb52-4fa8-b354-4dd6617d68f6
caps.latest.revision: 2
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 2
---
# 1124 - InvokeMethodIsStatic
## 屬性  
  
|||  
|-|-|  
|ID|1124|  
|關鍵字|WFRuntime|  
|層級|資訊|  
|通道|Microsoft\-Windows\-Application Server\-Applications\/Debug|  
  
## 描述  
 在 CacheMetadata 步驟期間，InvokeMethod 活動指出要叫用的方法是靜態的。  
  
## 訊息  
 InvokeMethod '%1' \- 方法是靜態方法。  
  
## 詳細資料  
  
|資料項目名稱|資料項目型別|描述|  
|------------|------------|--------|  
|InvokeMethod|xs:string|InvokeMethod 活動的顯示名稱。|  
|AppDomain|xs:string|由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。|