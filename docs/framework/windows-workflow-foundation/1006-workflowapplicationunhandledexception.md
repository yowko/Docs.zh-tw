---
title: "1006 - WorkflowApplicationUnhandledException | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: dfe0f316-e03b-47fb-b6a3-622c56bfd753
caps.latest.revision: 3
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 3
---
# 1006 - WorkflowApplicationUnhandledException
## 屬性  
  
|||  
|-|-|  
|ID|1006|  
|關鍵字|WFRuntime|  
|層級|錯誤|  
|通道|Microsoft\-Windows\-Application Server\-Applications\/Debug|  
  
## 描述  
 表示工作流程應用程式發生未處理的例外狀況。  
  
## 訊息  
 WorkflowInstance Id：'%1' 發現未處理的例外狀況。例外狀況源自活動 '%2'、DisplayName：'%3'。將採取下列動作：%4。  
  
## 詳細資料  
  
|資料項目名稱|資料項目型別|描述|  
|------------|------------|--------|  
|WorkflowInstanceId|`xs:string`|工作流程的執行個體 ID。|  
|例外狀況|`xs:string`|例外狀況的例外狀況詳細資料|  
|AppDomain|`xs:string`|由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。|