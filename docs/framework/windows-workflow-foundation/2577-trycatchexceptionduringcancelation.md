---
title: "2577 - TryCatchExceptionDuringCancelation | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 35ee9f55-227f-4566-bcb4-4c7c75dea85b
caps.latest.revision: 2
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 2
---
# 2577 - TryCatchExceptionDuringCancelation
## 屬性  
  
|||  
|-|-|  
|ID|2577|  
|關鍵字|WFActivities|  
|層級|警告|  
|通道|Microsoft\-Windows\-Application Server\-Applications\/Debug|  
  
## 描述  
 表示 TryCatch 活動的子活動在取消期間擲回例外狀況。  
  
## 訊息  
 TryCatch 活動 '%1' 的子活動在取消期間擲回例外狀況。  
  
## 詳細資料  
  
|資料項目名稱|資料項目型別|描述|  
|------------|------------|--------|  
|DisplayName|xs:string|活動的顯示名稱。|  
|AppDomain|xs:string|由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。|