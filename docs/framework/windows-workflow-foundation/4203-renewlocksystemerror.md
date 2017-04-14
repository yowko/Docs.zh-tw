---
title: "4203 - RenewLockSystemError | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6ec9ec6f-4ae2-45cf-b99b-02cdb9dc9ec9
caps.latest.revision: 2
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 2
---
# 4203 - RenewLockSystemError
## 屬性  
  
|||  
|-|-|  
|ID|4203|  
|關鍵字|WFInstanceStore|  
|層級|錯誤|  
|通道|Microsoft\-Windows\-Application Server\-Applications\/Debug|  
  
## 描述  
 表示因為已超過鎖定期限或已刪除鎖定擁有人，所以 SQL 提供者無法延長鎖定期限。  SqlWorkflowInstanceStore 即將中止。  
  
## 訊息  
 無法延長鎖定期限，已超過鎖定期限或已刪除鎖定擁有人。  正在中止 SqlWorkflowInstanceStore。  
  
## 詳細資料  
  
|資料項目名稱|資料項目型別|描述|  
|------------|------------|--------|  
|AppDomain|xs:string|由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。|