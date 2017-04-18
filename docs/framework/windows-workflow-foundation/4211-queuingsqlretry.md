---
title: "4211 - QueuingSqlRetry | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: df569f88-c86b-4503-840d-1399b67f4df7
caps.latest.revision: 2
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 2
---
# 4211 - QueuingSqlRetry
## 屬性  
  
|||  
|-|-|  
|ID|4211|  
|關鍵字|WFInstanceStore|  
|層級|警告|  
|通道|Microsoft\-Windows\-Application Server\-Applications\/Debug|  
  
## 描述  
 表示佇列 SQL 重試。  
  
## 訊息  
 佇列 SQL 重試，但延遲 %1 毫秒。  
  
## 詳細資料  
  
|資料項目名稱|資料項目型別|描述|  
|------------|------------|--------|  
|延遲|xs:string|重試之間的延遲。|  
|AppDomain|xs:string|由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。|