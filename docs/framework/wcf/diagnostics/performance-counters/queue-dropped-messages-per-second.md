---
title: "每秒佇列捨棄的訊息數 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 74540f52-8762-4147-b5ba-e171180515a3
caps.latest.revision: 8
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 8
---
# 每秒佇列捨棄的訊息數
計數器名稱：每秒捨棄的佇列訊息。  
  
## 描述  
 此服務的佇列傳輸每秒捨棄的訊息數。  
  
 這個計數器的效能計數器型別為 [PERF\_COUNTER\_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649) \(本頁面可能為英文\)，其值是使用以下公式計算而來。  
  
 \(N 1 \- N 0 \) \/ \( \(D 1 \-D 0 \) \/ F\)