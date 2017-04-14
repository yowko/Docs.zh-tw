---
title: "規則運算式中的執行緒安全 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - ".NET Framework 規則運算式, 執行緒"
  - "使用規則運算式剖析文字, 執行緒"
  - "使用規則運算式的模式比對, 執行緒"
  - "規則運算式, 執行緒"
  - "使用規則運算式搜尋, 執行緒"
ms.assetid: 7c4a167b-5236-4cde-a2ca-58646230730f
caps.latest.revision: 7
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 7
---
# 規則運算式中的執行緒安全
<xref:System.Text.RegularExpressions.Regex> 類別本身是執行緒安全和不變的 \(唯讀\)。  也就是，**Regex** 物件可以建立在任何執行緒並在執行緒間共用；比對方法可以從任何執行緒中呼叫，而且絕不會變更任何全域狀態。  
  
 然而，**Regex** 傳回的結果物件 \(**Match** 和 **MatchCollection**\) 應該使用在單一執行緒上。  雖然這些物件中有許多在邏輯上是不變的，但是它們的實作可能會延遲某些結果的計算以改善效能，而結果是呼叫端必須序列化對它們的存取。  
  
 如果有需要在多個執行緒上共用 **Regex** 結果物件，這些物件可以呼叫它們的同步方法，以轉換為安全執行緒執行個體。  除了列舉值是例外，所有規則運算式類別都是安全執行緒，或者可以經由同步方法轉換為安全執行緒物件。  
  
 列舉值是唯一的例外。  應用程式必須序列化對集合列舉值的呼叫。  規則就是，如果集合可以在一個以上的執行緒中同時列舉，您應該在列舉值所周遊之集合的根物件上同步處理列舉值方法。  
  
## 請參閱  
 [.NET Framework 規則運算式](../../../docs/standard/base-types/regular-expressions.md)