---
title: "4206 - UnlockInstanceException | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5a46dc5f-d517-4135-8905-25a42f01206b
caps.latest.revision: 2
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 2
---
# 4206 - UnlockInstanceException
## 屬性  
  
|||  
|-|-|  
|ID|4206|  
|關鍵字|WFInstanceStore|  
|層級|錯誤|  
|通道|Microsoft\-Windows\-Application Server\-Applications\/Debug|  
  
## 描述  
 表示在嘗試解除鎖定執行個體時，發生例外狀況。  
  
## 訊息  
 嘗試解除鎖定執行個體時，發生例外狀況 %1。  
  
## 詳細資料  
  
|資料項目名稱|資料項目型別|描述|  
|------------|------------|--------|  
|ExceptionMessage|xs:string|SQL 例外狀況的訊息。|  
|AppDomain|xs:string|由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。|