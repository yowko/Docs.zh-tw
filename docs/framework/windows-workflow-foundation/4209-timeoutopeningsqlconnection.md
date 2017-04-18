---
title: "4209 - TimeoutOpeningSqlConnection | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f0e56518-9758-41dc-a760-50d1a10fba6e
caps.latest.revision: 2
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 2
---
# 4209 - TimeoutOpeningSqlConnection
## 屬性  
  
|||  
|-|-|  
|ID|4209|  
|關鍵字|WFInstanceStore|  
|層級|錯誤|  
|通道|Microsoft\-Windows\-Application Server\-Applications\/Debug|  
  
## 描述  
 表示嘗試開啟 SQL 連接時，發生逾時。  
  
## 訊息  
 嘗試開啟 SQL 連接時發生逾時。  無法在分配的逾時 %1 內完成作業。  分配給此作業的時間可能是較長逾時的一部分。  
  
## 詳細資料  
  
|資料項目名稱|資料項目型別|描述|  
|------------|------------|--------|  
|等候逾時|xs:string|開啟 SQL 連接的逾時值。|  
|AppDomain|xs:string|由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。|