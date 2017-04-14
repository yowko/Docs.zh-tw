---
title: "3508 - TrackingProfileNotFound | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 4cee3c4a-0490-4c94-aa19-ef7ce7287c02
caps.latest.revision: 2
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 2
---
# 3508 - TrackingProfileNotFound
## 屬性  
  
|||  
|-|-|  
|ID|3508|  
|關鍵字|WFServices|  
|層級|詳細資訊|  
|通道|Microsoft\-Windows\-Application Server\-Applications\/Analytic|  
  
## 描述  
 表示在組態檔中找不到 TrackingProfile，或是 ActivityDefinitionId 不符合設定檔。  
  
## 訊息  
 找不到 ActivityDefinitionId '%2' 的 TrackingProfile '%1'。  在組態檔中找不到 TrackingProfile，或者 ActivityDefinitionId 不相符。  
  
## 詳細資料  
  
|資料項目名稱|資料項目型別|描述|  
|------------|------------|--------|  
|TrackingProfile|xs:string|追蹤設定檔的名稱。|  
|ActivityDefinitionId|xs:string|活動定義 ID。|  
|AppDomain|xs:string|由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。|