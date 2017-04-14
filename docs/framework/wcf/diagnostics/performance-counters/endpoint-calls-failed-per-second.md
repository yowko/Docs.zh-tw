---
title: "端點：每秒失敗的呼叫數 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: bcbe9da4-c8dd-4e27-b630-11611adc7580
caps.latest.revision: 9
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 9
---
# 端點：每秒失敗的呼叫數
計數器名稱：每秒失敗的呼叫數。  
  
## 描述  
 具有未處理的例外狀況以及由這個端點在一秒內收到的呼叫數目。  
  
 這個計數器的效能計數器型別為 [PERF\_COUNTER\_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649)，其值是使用以下公式計算而來。  
  
 \(N 1 \- N 0 \) \/ \( \(D 1 \-D 0 \) \/ F\)  
  
 每當這個端點有未處理的例外狀況時，這個計數器就會遞增。  
  
## 請參閱  
 [指定與處理合約和服務中的錯誤](../../../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md)