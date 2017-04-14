---
title: "每秒捨棄的可信賴傳訊訊息數 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a11b0b80-b242-48e1-b0bb-7f756db5486b
caps.latest.revision: 8
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 8
---
# 每秒捨棄的可信賴傳訊訊息數
計數器名稱：每秒捨棄的可信賴傳訊工作階段數。  
  
## 描述  
 在此服務中已捨棄的每秒可信賴傳訊訊息總數。  
  
 這個計數器的效能計數器型別為 [PERF\_COUNTER\_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649) \(本頁面可能為英文\)，其值是使用以下公式計算而來。  
  
 \(N 1 \- N 0 \) \/ \( \(D 1 \-D 0 \) \/ F\)