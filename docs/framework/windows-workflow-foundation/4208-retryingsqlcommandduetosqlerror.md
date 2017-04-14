---
title: "4208 - RetryingSqlCommandDueToSqlError | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a8e6483a-a6e4-4bbf-82ec-cd8b6e711aad
caps.latest.revision: 2
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 2
---
# 4208 - RetryingSqlCommandDueToSqlError
## 屬性  
  
|||  
|-|-|  
|ID|4208|  
|關鍵字|WFInstanceStore|  
|層級|資訊|  
|通道|Microsoft\-Windows\-Application Server\-Applications\/Debug|  
  
## 描述  
 表示 SQL 提供者正在重試 SQL 命令，因為發生 SQL 錯誤。  
  
## 訊息  
 重試 SQL 命令，因為出現 SQL 錯誤代碼 %1。  
  
## 詳細資料  
  
|資料項目名稱|資料項目型別|描述|  
|------------|------------|--------|  
|ErrorNumber|xs:string|SQL 錯誤代碼。|  
|AppDomain|xs:string|由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。|