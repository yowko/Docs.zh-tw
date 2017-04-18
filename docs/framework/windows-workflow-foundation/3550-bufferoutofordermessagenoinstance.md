---
title: "3550 - BufferOutOfOrderMessageNoInstance | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1299d294-99b8-430e-98b1-55f5f17002f3
caps.latest.revision: 2
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 2
---
# 3550 - BufferOutOfOrderMessageNoInstance
## 屬性  
  
|||  
|-|-|  
|ID|3550|  
|關鍵字|WFServices|  
|層級|資訊|  
|通道|Microsoft\-Windows\-Application Server\-Applications\/Analytic|  
  
## 描述  
 表示緩衝接收已失敗。  當服務執行個體準備好處理這個特定作業時，就會再次嘗試此作業。  
  
## 訊息  
 目前無法執行作業 '%1'。  將在服務執行個體準備就緒可以處理這個特定作業時，再次嘗試。  
  
## 詳細資料  
  
|資料項目名稱|資料項目型別|描述|  
|------------|------------|--------|  
|OperationName|xs:string|作業的名稱。|  
|AppDomain|xs:string|由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。|