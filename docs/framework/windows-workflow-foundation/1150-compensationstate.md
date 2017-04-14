---
title: "1150 - CompensationState | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: eb015842-cc5a-47be-bce5-6af39e567723
caps.latest.revision: 3
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 3
---
# 1150 - CompensationState
## 屬性  
  
|||  
|-|-|  
|ID|1150|  
|關鍵字|WFActivities|  
|層級|資訊|  
|通道|Microsoft\-Windows\-Application Server\-Applications\/Debug|  
  
## 描述  
 表示 CompensableActivity 中的狀態變更。  
  
## 訊息  
 CompensableActivity '%1' 處於 '%2' 狀態。  
  
## 詳細資料  
  
|資料項目名稱|資料項目型別|描述|  
|------------|------------|--------|  
|DisplayName|xs:string|活動的顯示名稱。|  
|狀態|xs:string|補償狀態。|  
|AppDomain|xs:string|由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。|