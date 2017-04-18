---
title: "1103 - WorkflowActivitySuspend | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b64e15c2-cb2c-4314-9074-ce2c6717232e
caps.latest.revision: 2
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 2
---
# 1103 - WorkflowActivitySuspend
## 屬性  
  
|||  
|-|-|  
|ID|1103|  
|關鍵字|WFRuntime|  
|層級|資訊|  
|通道|Microsoft\-Windows\-Application Server\-Applications\/Debug|  
  
## 描述  
 表示已暫停工作流程活動。  
  
## 訊息  
 WorkflowInstance Id：'%1' E2E 活動  
  
## 詳細資料  
  
|資料項目名稱|資料項目型別|描述|  
|------------|------------|--------|  
|WorkflowInstanceId|xs:string|工作流程執行個體 ID。|  
|AppDomain|xs:string|由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。|