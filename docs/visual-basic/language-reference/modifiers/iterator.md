---
title: "Iterator (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.Iterator"
helpviewer_keywords: 
  - "Iterator keyword [Visual Basic]"
ms.assetid: 69cb0b04-ac87-49d0-bcfe-810c0d60daff
caps.latest.revision: 11
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 11
---
# Iterator (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

表示函式或`Get`存取子是 iterator。  
  
## 備註  
 *Iterator* 對集合進行反覆執行自訂的反覆項目。  使用 iterator [會產生](../../../visual-basic/language-reference/statements/yield-statement.md)陳述式來傳回一次一個集合中的每個項目。  當`Yield`到達陳述式時，仍可在程式碼中目前的位置。  執行已從該位置在下次重新啟動 iterator 函式所呼叫。  
  
 Iterator 可實作為函式或`Get`的屬性定義存取子。  `Iterator`修飾詞會出現在 iterator 函式宣告或`Get`存取子。  
  
 您從用戶端程式碼呼叫 iterator 藉由使用[For Each...Next 陳述式](../../../visual-basic/language-reference/statements/for-each-next-statement.md)。  
  
 將 iterator 函式的傳回型別或`Get`存取子可以是<xref:System.Collections.IEnumerable>， <xref:System.Collections.Generic.IEnumerable%601>， <xref:System.Collections.IEnumerator>，或<xref:System.Collections.Generic.IEnumerator%601>。  
  
 Iterator 不能有任何`ByRef`參數。  
  
 Iterator 不可以發生在事件、 執行個體建構函式、 靜態建構函式或靜態的解構函式。  
  
 Iterator 可以是匿名函式。  如需詳細資訊，請參閱 [迭代器](../Topic/Iterators%20\(C%23%20and%20Visual%20Basic\).md)。  
  
 如需 Iterator 的詳細資訊，請參閱 [迭代器](../Topic/Iterators%20\(C%23%20and%20Visual%20Basic\).md)。  
  
## 使用方式  
 `Iterator` 修飾詞可用於以下內容中：  
  
-   [Function Statement](../../../visual-basic/language-reference/statements/function-statement.md)  
  
-   [Property Statement](../../../visual-basic/language-reference/statements/property-statement.md)  
  
## 範例  
 下列範例會示範一個 iterator 函式。  Iterator 函數語法包含`Yield`陳述式中[縮排樣式下一步](../../../visual-basic/language-reference/statements/for-next-statement.md)迴圈。  每個反覆項目中的[為每個](../../../visual-basic/language-reference/statements/for-each-next-statement.md)中的陳述式主體`Main`建立呼叫`Power` iterator 函式。  每次呼叫 iterator 函式進行到下一步執行`Yield`陳述式，它的下一個反覆項目時，就會發生`For…Next`迴圈。  
  
 [!code-vb[VbVbalrStatements#98](../../../visual-basic/language-reference/error-messages/codesnippet/visualbasic/iterator_1.vb)]  
  
## 範例  
 下列範例會示範`Get`是 iterator 的存取子。  `Iterator`是在屬性宣告的修飾詞。  
  
 [!code-vb[VbVbalrStatements#99](../../../visual-basic/language-reference/error-messages/codesnippet/visualbasic/iterator_2.vb)]  
  
 如需其他範例，請參閱 [迭代器](../Topic/Iterators%20\(C%23%20and%20Visual%20Basic\).md)。  
  
## 請參閱  
 <xref:System.Runtime.CompilerServices.IteratorStateMachineAttribute>   
 [迭代器](../Topic/Iterators%20\(C%23%20and%20Visual%20Basic\).md)   
 [Yield 陳述式](../../../visual-basic/language-reference/statements/yield-statement.md)