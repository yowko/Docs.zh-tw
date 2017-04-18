---
title: "3557 - TransactedReceiveScopeEndCommitFailed | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 079f0188-8146-49ee-b6ae-a08f4e4d2b9b
caps.latest.revision: 2
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 2
---
# 3557 - TransactedReceiveScopeEndCommitFailed
## 屬性  
  
|||  
|-|-|  
|ID|3557|  
|關鍵字|WFServices|  
|層級|資訊|  
|通道|Microsoft\-Windows\-Application Server\-Applications\/Analytic|  
  
## 描述  
 表示呼叫 CommittableTransaction 上的 EndCommit 擲回 TransactionException。  
  
## 訊息  
 呼叫 ID \= '%1' 之 CommittableTransaction 上的 EndCommit 擲回 TransactionException，並出現下列訊息：'%2'。  
  
## 詳細資料  
  
|資料項目名稱|資料項目型別|描述|  
|------------|------------|--------|  
|TransactionId|xs:string|CommittableTransaction 的 ID。|  
|例外狀況|xs:string|例外狀況的例外狀況詳細資料|  
|AppDomain|xs:string|由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。|