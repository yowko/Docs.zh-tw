---
title: "3507 - ServiceEndpointAdded | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c068fc0e-07ee-4551-9824-ea7216e1fe37
caps.latest.revision: 2
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 2
---
# 3507 - ServiceEndpointAdded
## 屬性  
  
|||  
|-|-|  
|ID|3507|  
|關鍵字|WFServices|  
|層級|資訊|  
|通道|Microsoft\-Windows\-Application Server\-Applications\/Analytic|  
  
## 描述  
 表示已加入服務端點。  
  
## 訊息  
 已經針對位址 '%1'、繫結 '%2' 和合約 '%3' 加入服務端點。  
  
## 詳細資料  
  
|資料項目名稱|資料項目型別|描述|  
|------------|------------|--------|  
|地址|xs:string|端點的位址。|  
|繫結|xs:string|端點的繫結。|  
|合約|xs:string|端點的合約。|  
|AppDomain|xs:string|由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。|