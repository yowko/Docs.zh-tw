---
title: "如何：使用 foreach 存取集合類別 (C# 程式設計手冊) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "集合類別 [C#], foreach 陳述式"
ms.assetid: a6b9cf5c-6c8d-4223-b12c-288949434493
caps.latest.revision: 21
caps.handback.revision: 21
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 如何：使用 foreach 存取集合類別 (C# 程式設計手冊)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

下列程式碼範例說明如何撰寫可搭配 [foreach](../../../csharp/language-reference/keywords/foreach-in.md) 使用的非泛型集合類別。  此範例會定義從字串中取出語彙基元的類別。  
  
> [!NOTE]
>  此範例所呈現的建議作法，只適用於無法使用泛型集合類別的情況。  如需如何實作支援 <xref:System.Collections.Generic.IEnumerable%601> 之型別安全泛型集合類別的範例，請參閱 [迭代器](../Topic/Iterators%20\(C%23%20and%20Visual%20Basic\).md)。  
  
 在範例中，下列程式碼區段會使用 `Tokens` 類別將 "This is a sample sentence." 這個句子分成多個語彙基元 \(使用 ' ' 和 '\-' 做為分隔符號\)。  然後程式碼會使用 `foreach` 陳述式顯示這些語彙基元。  
  
 [!code-cs[csProgGuideCollections#3](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-access-a-collection-class-with-foreach_1.cs)]  
  
## 範例  
 `Tokens` 類別會在內部使用陣列儲存語彙基元。  由於陣列會實作 <xref:System.Collections.IEnumerator> 和 <xref:System.Collections.IEnumerable>，因此這個程式碼範例可能使用了陣列的列舉方法 \(<xref:System.Collections.IEnumerable.GetEnumerator%2A>、<xref:System.Collections.IEnumerator.MoveNext%2A>、<xref:System.Collections.IEnumerator.Reset%2A> 和 <xref:System.Collections.IEnumerator.Current%2A>\)，而不是在 `Tokens` 類別中定義這些方法。  範例中會包含方法定義，用以釐清其定義方式及各自的功能。  
  
 [!code-cs[csProgGuideCollections#2](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-access-a-collection-class-with-foreach_2.cs)]  
  
 在 C\# 中，集合類別不一定要實作 <xref:System.Collections.IEnumerable> 和 <xref:System.Collections.IEnumerator>，也能與 `foreach` 相容。  如果類別具有必要的 <xref:System.Collections.IEnumerable.GetEnumerator%2A>、<xref:System.Collections.IEnumerator.MoveNext%2A>、<xref:System.Collections.IEnumerator.Reset%2A> 和 <xref:System.Collections.IEnumerator.Current%2A> 成員，就可以搭配 `foreach` 使用。  省略介面的優點是，您可以為 `Current` 定義比 <xref:System.Object> 更明確的傳回型別。  這樣就能提供型別安全。  
  
 例如，變更上述範例中的下列幾行。  
  
<CodeContentPlaceHolder>0</CodeContentPlaceHolder>  
 由於 `Current` 傳回字串，因此當 `foreach` 陳述式中使用了不相容的型別時，編譯器便可偵測出來，如下列程式碼中所示。  
  
<CodeContentPlaceHolder>1</CodeContentPlaceHolder>  
 省略 <xref:System.Collections.IEnumerable> 和 <xref:System.Collections.IEnumerator> 的缺點是，集合類別不再能夠與其他 Common Language Runtime 語言的 `foreach` 陳述式 \(或對等陳述式\) 交互作用。  
  
## 請參閱  
 <xref:System.Collections.Generic>   
 [C\# 參考](../../../visual-basic/reference/command-line-compiler/index.md)   
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [陣列](../../../csharp/programming-guide/arrays/index.md)   
 [集合](../Topic/Collections%20\(C%23%20and%20Visual%20Basic\).md)