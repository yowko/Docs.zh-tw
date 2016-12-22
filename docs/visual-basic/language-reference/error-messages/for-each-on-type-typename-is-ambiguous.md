---
title: "&#39;For Each&#39; on type &#39;&lt;typename&gt;&#39; is ambiguous because the type implements multiple instantiations of &#39;System.Collections.Generic.IEnumerable(Of T)&#39; | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc32096"
  - "bc32096"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC32096"
ms.assetid: ed20d09c-913f-482e-89f8-c0a596c3ec24
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;For Each&#39; on type &#39;&lt;typename&gt;&#39; is ambiguous because the type implements multiple instantiations of &#39;System.Collections.Generic.IEnumerable(Of T)&#39;
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

`For Each` 陳述式 \(Statement\) 會指定具有多個 <xref:System.Collections.IEnumerable.GetEnumerator%2A> 方法的 Iterator 變數。  
  
 Iterator 變數必須是在 [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] 的其中一個 `Collections` 命名空間中實作 <xref:System.Collections.IEnumerable?displayProperty=fullName> 或 <xref:System.Collections.Generic.IEnumerable%601?displayProperty=fullName> 介面的型別。  類別可能會對每個語法結構使用不同的型別引數，實作多個結構化泛型介面。  如果執行上述動作的類別用於 Iterator 變數，表示該變數具有多個 <xref:System.Collections.IEnumerable.GetEnumerator%2A> 方法。  在這種情形下，[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] 無法選擇要呼叫的方法。  
  
 **錯誤 ID**：BC32096  
  
### 若要更正這個錯誤  
  
-   使用 [DirectCast Operator](../../../visual-basic/language-reference/operators/directcast-operator.md) 或 [TryCast Operator](../../../visual-basic/language-reference/operators/trycast-operator.md)，將 Iterator 變數型別轉換為定義所要使用之 <xref:System.Collections.IEnumerable.GetEnumerator%2A> 方法的介面。  
  
## 請參閱  
 [For Each...Next 陳述式](../../../visual-basic/language-reference/statements/for-each-next-statement.md)   
 [Interfaces](../../../visual-basic/programming-guide/language-features/interfaces/index.md)