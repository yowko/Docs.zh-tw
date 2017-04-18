---
title: "1035 - RuntimeTransactionSet | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 03b37de9-778c-4beb-b0e3-de73ece6088e
caps.latest.revision: 3
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 3
---
# 1035 - RuntimeTransactionSet
## 屬性  
  
|||  
|-|-|  
|ID|1035|  
|關鍵字|WFRuntime|  
|層級|詳細資訊|  
|通道|Microsoft\-Windows\-Application Server\-Applications\/Debug|  
  
## 描述  
 表示活動已設定執行階段交易。  
  
## 訊息  
 活動 '%1'、DisplayName：'%2'、InstanceId：'%3' 已設定執行階段交易。執行已隔離到活動 '%4'、DisplayName：'%5'、InstanceId：'%6'。  
  
## 詳細資料  
  
|資料項目名稱|資料項目型別|描述|  
|------------|------------|--------|  
|活動|xs:string|活動的型別名稱。|  
|DisplayName|xs:string|活動的顯示名稱。|  
|InstanceId|xs:string|活動的執行個體 ID。|  
|IsolatedActivity|xs:string|隔離交易之目標活動的型別名稱。|  
|IsolatedActivityDisplayName|xs:string|隔離交易之目標活動的顯示名稱。|  
|IsolatedActivityInstanceId|xs:string|隔離交易之目標活動的執行個體 ID。|  
|AppDomain|xs:string|由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。|