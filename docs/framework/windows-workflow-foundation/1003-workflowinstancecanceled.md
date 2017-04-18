---
title: "1003 - WorkflowInstanceCanceled | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 64754dc2-c160-4bf3-869a-13d56694e2dc
caps.latest.revision: 4
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 4
---
# 1003 - WorkflowInstanceCanceled
## 屬性  
  
|||  
|-|-|  
|ID|1003|  
|關鍵字|WFRuntime|  
|層級|資訊|  
|通道|Microsoft\-Windows\-Application Server\-Applications\/Debug|  
  
## 描述  
 表示工作流程執行個體已在 Canceled 狀態中完成。  
  
## 訊息  
 WorkflowInstance Id：'%1' 已在 Canceled 狀態中完成。  
  
## 詳細資料  
  
|資料項目名稱|資料項目型別|描述|  
|------------|------------|--------|  
|WorkflowInstanceId|`xs:string`|工作流程的執行個體 ID。|  
|AppDomain|`xs:string`|由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。|