---
title: "4210 - SqlExceptionCaught | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f0ce8af3-eb4c-48c8-b3d9-dd2f94b5574b
caps.latest.revision: 2
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 2
---
# 4210 - SqlExceptionCaught
## 屬性  
  
|||  
|-|-|  
|ID|4210|  
|關鍵字|WFInstanceStore|  
|層級|警告|  
|通道|Microsoft\-Windows\-Application Server\-Applications\/Debug|  
  
## 描述  
 表示已攔截到 SQL 例外狀況。  
  
## 訊息  
 攔截到 SQL 例外狀況編號 %1 訊息 %2。  
  
## 詳細資料  
  
|資料項目名稱|資料項目型別|描述|  
|------------|------------|--------|  
|ErrorNumber|xs:string|SQL 錯誤代碼。|  
|ExceptionMessage|xs:string|SQL 例外狀況的訊息。|  
|AppDomain|xs:string|由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。|