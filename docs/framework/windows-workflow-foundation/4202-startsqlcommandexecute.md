---
title: "4202 - StartSqlCommandExecute | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 4559f64f-c824-4075-9e7e-4710bf30f805
caps.latest.revision: 2
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 2
---
# 4202 - StartSqlCommandExecute
## 屬性  
  
|||  
|-|-|  
|ID|4202|  
|關鍵字|WFInstanceStore|  
|層級|詳細資訊|  
|通道|Microsoft\-Windows\-Application Server\-Applications\/Debug|  
  
## 描述  
 表示正在執行 SQL 命令。  
  
## 訊息  
 開始 SQL 命令執行：%1  
  
## 詳細資料  
  
|資料項目名稱|資料項目型別|描述|  
|------------|------------|--------|  
|SqlCommand|xs:string|所執行的 SQL 命令。|  
|AppDomain|xs:string|由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。|