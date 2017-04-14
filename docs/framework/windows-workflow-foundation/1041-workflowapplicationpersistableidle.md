---
title: "1041 - WorkflowApplicationPersistableIdle | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 966adf2f-e21d-44df-a3ec-a8e285e0a316
caps.latest.revision: 2
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 2
---
# 1041 - WorkflowApplicationPersistableIdle
## 屬性  
  
|||  
|-|-|  
|ID|1041|  
|關鍵字|WFRuntime|  
|層級|資訊|  
|通道|Microsoft\-Windows\-Application Server\-Applications\/Debug|  
  
## 描述  
 表示工作流程應用程式處於閒置狀態且為永續性。  工作流程應用程式將會閒置或持續。  
  
## 訊息  
 WorkflowApplication Id：'%1' 閒置且為永續性。將採取列動作：%2。  
  
## 詳細資料  
  
|資料項目名稱|資料項目型別|描述|  
|------------|------------|--------|  
|WorkflowApplicationId|xs:string|工作流程應用程式 ID|  
|ActionTaken|xs:string|將要對工作流程應用程式要採取的動作。|  
|AppDomain|xs:string|由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。|