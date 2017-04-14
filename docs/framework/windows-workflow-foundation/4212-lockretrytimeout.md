---
title: "4212 - LockRetryTimeout | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d4ad415a-9871-49fc-85b8-8ee2ea149b1d
caps.latest.revision: 2
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 2
---
# 4212 - LockRetryTimeout
## 屬性  
  
|||  
|-|-|  
|ID|4212|  
|關鍵字|WFInstanceStore|  
|層級|警告|  
|通道|Microsoft\-Windows\-Application Server\-Applications\/Debug|  
  
## 描述  
 SQL 提供者嘗試擷取執行個體鎖定時發生逾時。  
  
## 訊息  
 嘗試擷取執行個體鎖定時發生逾時。無法在分配的逾時 %1 內完成作業。  分配給此作業的時間可能是較長逾時的一部分。  
  
## 詳細資料  
  
|資料項目名稱|資料項目型別|描述|  
|------------|------------|--------|  
|延遲|xs:string|重試之間的延遲。|  
|AppDomain|xs:string|由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。|