---
title: "1023 - CompleteBookmarkWorkItem | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: fc5dac57-b3eb-4826-b505-c6d269e4774d
caps.latest.revision: 3
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 3
---
# 1023 - CompleteBookmarkWorkItem
## 屬性  
  
|||  
|-|-|  
|ID|1023|  
|關鍵字|WFRuntime|  
|層級|詳細資訊|  
|通道|Microsoft\-Windows\-Application Server\-Applications\/Debug|  
  
## 描述  
 表示 BookmarkWorkItem 已完成。  
  
## 訊息  
 已完成活動 '%1'、DisplayName：'%2'、InstanceId：'%3' 的 BookmarkWorkItem。  BookmarkName：%4、BookmarkScope：%5。  
  
## 詳細資料  
  
|資料項目名稱|資料項目型別|描述|  
|------------|------------|--------|  
|活動|xs:string|活動的型別名稱。|  
|DisplayName|xs:string|活動的顯示名稱。|  
|InstanceId|xs:string|活動的執行個體 ID。|  
|BookmarkName|xs:string|書籤的名稱。|  
|BookmarkScope|xs:string|書籤的範圍。|  
|AppDomain|xs:string|由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。|