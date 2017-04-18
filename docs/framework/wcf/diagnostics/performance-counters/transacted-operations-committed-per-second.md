---
title: "每秒認可的交易作業數 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7318921b-47c4-4c8c-9fdd-41a92061c53f
caps.latest.revision: 7
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 7
---
# 每秒認可的交易作業數
計數器名稱：每秒認可的交易作業數。  
  
## 描述  
 此服務每秒所認可的交易作業數。  
  
 這個計數器的效能計數器型別為 [PERF\_COUNTER\_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649) \(本頁面可能為英文\)，其值是使用以下公式計算而來。  
  
 \(N 1 \- N 0 \) \/ \( \(D 1 \-D 0 \) \/ F\)