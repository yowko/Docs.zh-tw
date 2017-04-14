---
title: "1025 - BookmarkScopeInitialized | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 63584434-e709-471d-9e96-97d3d99e70d6
caps.latest.revision: 3
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 3
---
# 1025 - BookmarkScopeInitialized
## 屬性  
  
|||  
|-|-|  
|ID|1025|  
|關鍵字|WFRuntime|  
|層級|詳細資訊|  
|通道|Microsoft\-Windows\-Application Server\-Applications\/Debug|  
  
## 描述  
 表示已初始化 BookmarkScope。  
  
## 訊息  
 已用 ID：'%2' 初始化具有 TemporaryId：'%1' 的 BookmarkScope。  
  
## 詳細資料  
  
|資料項目名稱|資料項目型別|描述|  
|------------|------------|--------|  
|TemporaryId|xs:string|書籤的暫時 ID。|  
|InitializedId|xs:string|書籤的初始化 ID。|  
|AppDomain|xs:string|由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。|