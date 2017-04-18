---
title: "服務：每秒的呼叫數 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6261d28d-d449-425a-b9fc-a4ee14079134
caps.latest.revision: 9
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 9
---
# 服務：每秒的呼叫數
計數器名稱：每秒呼叫數。  
  
## 描述  
 對這個服務的每秒呼叫數。  
  
 這個計數器的效能計數器型別為 [PERF\_COUNTER\_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649)，其值是使用以下公式計算而來。  
  
 \(N 1 \- N 0 \) \/ \( \(D 1 \-D 0 \) \/ F\)，其中，分子 \(N\) 表示最新樣本間隔期間的已執行作業數，分母 \(D\) 表示最新樣本間隔期間的已耗用時間，而 F 是刻度的頻率。