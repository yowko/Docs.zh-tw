---
title: "3552 - MaxPendingMessagesPerChannelExceeded | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: fc8309d9-eb3a-4636-a6f0-dd0018c1361d
caps.latest.revision: 3
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 3
---
# 3552 - MaxPendingMessagesPerChannelExceeded
## 屬性  
  
|||  
|-|-|  
|ID|3552|  
|關鍵字|配額、WFServices|  
|層級|警告|  
|通道|Microsoft\-Windows\-Application Server\-Applications\/Analytic|  
  
## 描述  
 表示已達到節流 'MaxPendingMessagesPerChannel' 限制。  
  
## 訊息  
 已達到 '%1' 的節流 'MaxPendingMessagesPerChannel' 限制。  若要增加此限制，請調整 BufferedReceiveServiceBehavior 上的 MaxPendingMessagesPerChannel 屬性。  
  
## 詳細資料  
  
|資料項目名稱|資料項目型別|描述|  
|------------|------------|--------|  
|限制|xs:string|已達到 MaxPendingMessagesPerChannel 節流的限制。|  
|AppDomain|xs:string|由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。|