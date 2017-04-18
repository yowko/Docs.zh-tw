---
title: "服務：每秒失敗的呼叫數 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5a2c7939-107d-4f0c-b43c-e02e079e8a9d
caps.latest.revision: 11
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 11
---
# 服務：每秒失敗的呼叫數
計數器名稱：每秒失敗的呼叫數。  
  
## 描述  
 未處理之例外狀況的呼叫數，以及此服務在一秒之內所收到的呼叫數。  
  
 這個計數器的效能計數器型別為 [PERF\_COUNTER\_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649) \(英文\)，其值是使用以下公式計算而來。  
  
 \(N 1 \- N 0 \) \/ \( \(D 1 \-D 0 \) \/ F\)  
  
 在 Managed 程式碼中，發生錯誤狀況時會擲回例外狀況。  
  
 在 Managed 程式碼中，發生錯誤狀況時會擲回例外狀況。  
  
 每當此服務有未處理的例外狀況時，此計數器就會遞增。  
  
## 請參閱  
 [指定與處理合約和服務中的錯誤](../../../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md)