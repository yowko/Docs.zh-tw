---
title: "3503 - DuplicateCorrelationQuery | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b857f8e6-ce4d-4da4-bc9d-6cd63fa558a4
caps.latest.revision: 2
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 2
---
# 3503 - DuplicateCorrelationQuery
## 屬性  
  
|||  
|-|-|  
|ID|3503|  
|關鍵字|WFServices|  
|層級|警告|  
|通道|Microsoft\-Windows\-Application Server\-Applications\/Analytic|  
  
## 描述  
 表示發現重複的 CorrelationQuery。  在計算相互關聯時，不會使用重複的查詢。  
  
## 訊息  
 發現 Where\='%1' 的重複 CorrelationQuery。  計算相互關聯時不會使用這個重複的查詢。  
  
## 詳細資料  
  
|資料項目名稱|資料項目型別|描述|  
|------------|------------|--------|  
|位置|xs:string|相互關聯查詢的 Where 部分。|  
|AppDomain|xs:string|由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。|