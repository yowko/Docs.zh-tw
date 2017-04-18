---
title: "1033 - StartRuntimeWorkItem | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 172b5346-9f3b-46ae-bc06-39872022376a
caps.latest.revision: 3
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 3
---
# 1033 - StartRuntimeWorkItem
## 屬性  
  
|||  
|-|-|  
|ID|1033|  
|關鍵字|WFRuntime|  
|層級|詳細資訊|  
|通道|Microsoft\-Windows\-Application Server\-Applications\/Debug|  
  
## 描述  
 表示 RuntimeWorkItem 開始執行。  
  
## 訊息  
 開始執行活動 '%1'、DisplayName：'%2'、InstanceId：'%3' 的執行階段工作項目。  
  
## 詳細資料  
  
|資料項目名稱|資料項目型別|描述|  
|------------|------------|--------|  
|活動|xs:string|活動的型別名稱。|  
|DisplayName|xs:string|活動的顯示名稱。|  
|InstanceId|xs:string|活動的執行個體 ID。|  
|AppDomain|xs:string|由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。|