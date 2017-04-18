---
title: "1007 - WorkflowApplicationPersisted | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f4ea4452-28e3-4e66-93c6-eb12ee29bcb1
caps.latest.revision: 3
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 3
---
# 1007 - WorkflowApplicationPersisted
## 屬性  
  
|||  
|-|-|  
|ID|1007|  
|關鍵字|WFRuntime|  
|層級|資訊|  
|通道|Microsoft\-Windows\-Application Server\-Applications\/Debug|  
  
## 描述  
 表示工作流程應用程式是永續性。  
  
## 訊息  
 WorkflowApplication Id：'%1' 是永續性的。  
  
## 詳細資料  
  
|資料項目名稱|資料項目型別|描述|  
|------------|------------|--------|  
|WorkflowApplicationId|`xs:string`|工作流程應用程式 ID|  
|AppDomain|`xs:string`|由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。|