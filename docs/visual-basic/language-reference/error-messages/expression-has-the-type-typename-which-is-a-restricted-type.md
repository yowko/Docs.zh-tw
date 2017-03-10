---
title: "Expression has the type &#39;&lt;typename&gt;&#39; which is a restricted type and cannot be used to access members inherited from &#39;Object&#39; or &#39;ValueType&#39; | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "bc31393"
  - "vbc31393"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC31393"
ms.assetid: 2963cf3f-c527-4aa7-b67c-ee80b6d23186
caps.latest.revision: 6
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 6
---
# Expression has the type &#39;&lt;typename&gt;&#39; which is a restricted type and cannot be used to access members inherited from &#39;Object&#39; or &#39;ValueType&#39;
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

運算式會評估為無法由 Common Language Runtime \(CLR\) 進行 Box 處理的型別，但會存取需要 Boxing 的成員。  
  
 *Boxing* 會參考將型別轉換為 `Object` \(或者，有時會轉換為 <xref:System.ValueType>\) 的必要處理。  Common Language Runtime 無法 Box 特定結構型別，例如 <xref:System.ArgIterator>、<xref:System.RuntimeArgumentHandle> 和 <xref:System.TypedReference>。  
  
 這個運算式會嘗試使用受限制的型別，呼叫從 <xref:System.Object> 或 <xref:System.ValueType> 繼承的方法，例如 <xref:System.Object.GetHashCode%2A> 或 <xref:System.Object.ToString%2A>。  為了存取這個方法，[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 已嘗試進行隱含 Boxing 轉換，而導致這項錯誤。  
  
 **錯誤 ID：**BC31393  
  
### 若要更正這個錯誤  
  
1.  尋找評估為引用型別的運算式。  
  
2.  在您的陳述式中，找出嘗試呼叫繼承自 <xref:System.Object> 或 <xref:System.ValueType> 之方法的部分。  
  
3.  重新撰寫陳述式，避免進行方法呼叫。  
  
## 請參閱  
 [Implicit and Explicit Conversions](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)