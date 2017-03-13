---
title: "Yield 陳述式 (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.Yield"
helpviewer_keywords: 
  - "迭代器，Yield 陳述式 [Visual Basic]"
  - "迭代器 [Visual Basic]"
  - "Yield 陳述式 [Visual Basic]"
ms.assetid: f33126c5-d7c4-43e2-8e36-4ae3f0703d97
caps.latest.revision: 22
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 22
---
# Yield 陳述式 (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

傳送集合中的下一個元素為 `For Each...Next` 陳述式。  
  
## 語法  
  
```  
Yield expression  
```  
  
#### 參數  
  
|||  
|-|-|  
|詞彙|定義|  
|`expression`|必要項。  隱含地轉換為 Iterator 函式或 `Get` 存取子的型別包含 `Yield` 陳述式的運算式。|  
  
## 備註  
 `Yield` 陳述式一次傳回集合中的項目。  `Yield` 陳述式在 Iterator 函式或 `Get` 存取子中，對集合的自訂反覆項目。  
  
 使用 [For Each...Next 陳述式](../../../visual-basic/language-reference/statements/for-each-next-statement.md) 或 LINQ 查詢，您使用 Iterator 函式。  `For Each` 迴圈的每次查看呼叫 Iterator 函式。  執行 `Yield` 陳述式在 Iterator 函式時到達，則會傳回 `expression` ，因此，目前位置在程式碼中保留。  執行從該位置下次重新啟動 Iterator 函式呼叫。  
  
 隱含轉換必須從 `expression` 型別在 `Yield` 陳述式的存在於 Iterator 的傳回型別。  
  
 您可以使用 `Exit Function` 或 `Return` 陳述式結束反覆運算。  
  
 只有在使用 `Iterator` 函式或 `Get` 存取子中， 「Yield」不是保留字而且具有特殊的意義。  
  
 如需 Iterator 函式和 `Get` 存取子的詳細資訊，請參閱 [迭代器](../Topic/Iterators%20\(C%23%20and%20Visual%20Basic\).md)。  
  
## Iterator 函式和 Get 存取子  
 Iterator 函式或 `Get` 存取子的宣告必須符合下列需求:  
  
-   它必須包含 [Iterator](../../../visual-basic/language-reference/modifiers/iterator.md) 修飾詞。  
  
-   傳回型別必須是 <xref:System.Collections.IEnumerable>、 <xref:System.Collections.Generic.IEnumerable%601>、 <xref:System.Collections.IEnumerator>或 <xref:System.Collections.Generic.IEnumerator%601>。  
  
-   它不能有任何 `ByRef` 參數。  
  
 Iterator 函式在事件、執行個體建構函式、靜態建構函式或靜態解構函式不會發生。  
  
 Iterator 函式可以是匿名函式。  如需詳細資訊，請參閱[迭代器](../Topic/Iterators%20\(C%23%20and%20Visual%20Basic\).md)。  
  
## 例外狀況處理  
 `Yield` 陳述式可以是 [Try...Catch...Finally Statement](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)的 `Try` 區塊內。  具有 `Yield` 陳述式的 `Try` 區塊有 `Catch` 區塊，而且可以有 `Finally` 區塊。  
  
 `Yield` 陳述式不可以在 `Catch` 區塊或 `Finally` 區塊內。  
  
 如果 `For Each` 主體 \(在 Iterator 函式之外\) 會擲回例外狀況，在 Iterator 函式的 `Catch` 區塊未執行，不過，在 Iterator 函式的 `Finally` 區塊執行。  在 Iterator 的函式中 `Catch` 區塊攔截發生在 Iterator 函式內的例外狀況。  
  
## 技術實作  
 下列程式碼會從 Iterator 函式的 `IEnumerable (Of String)` 將 `IEnumerable (Of String)`的項目集合。  
  
```vb  
Dim elements As IEnumerable(Of String) = MyIteratorFunction()  
    …  
For Each element As String In elements  
Next  
```  
  
 對 `MyIteratorFunction` 的呼叫不執行函式的主體。  反而呼叫傳回 `IEnumerable(Of String)` 加入至 `elements` 變數中。  
  
 在 `For Each` 迴圈的反覆項目， <xref:System.Collections.IEnumerator.MoveNext%2A> 方法會呼叫 `elements`。  這稱為執行 `MyIteratorFunction` 主體，直到下一個 `Yield` 陳述式為止。  `Yield` 陳述式傳回迴圈主體判斷 `element` 變數的不僅值使用的，而且項目的 <xref:System.Collections.Generic.IEnumerator%601.Current%2A> 屬性，則為 `IEnumerable (Of String)`。  
  
 在 `For Each` 迴圈的每個後續反覆項目， Iterator 主體的執行與繼續它停止的地方，再停止，並在到達 `Yield` 陳述式。  當 Iterator 函式或 `Return` 或 `Exit Function` 陳述式的結尾到達， `For Each` 迴圈完成。  
  
## 範例  
 下列範例會在 [對於 Each…Next](../../../visual-basic/language-reference/statements/for-next-statement.md) 迴圈中的 `Yield` 陳述式。  [對於每個](../../../visual-basic/language-reference/statements/for-each-next-statement.md) 陳述式主體的每個反覆項目在 `Main` 建立呼叫 `Power` Iterator 函式。  將 Iterator 函式的每個呼叫執行 `Yield` 陳述式的下執行，迴圈會出現在 `For…Next` 下一個反覆項目時。  
  
 Iterator 方法的傳回型別是 <xref:System.Collections.Generic.IEnumerable%601>， Iterator 介面型別。  當 Iterator 方法呼叫時，它會傳回可列舉的物件包含數字的階乘冪。  
  
 [!code-vb[VbVbalrStatements#98](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/yield-statement_1.vb)]  
  
## 範例  
 下列範例示範是 Iterator 的 `Get` 存取子。  屬性宣告包含一個 `Iterator` 修飾詞。  
  
 [!code-vb[VbVbalrStatements#99](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/yield-statement_2.vb)]  
  
 如需其他範例，請參閱 [迭代器](../Topic/Iterators%20\(C%23%20and%20Visual%20Basic\).md)。  
  
## 需求  
 [!INCLUDE[vs_dev11_long](../../../csharp/includes/vs-dev11-long-md.md)]  
  
## 請參閱  
 [迭代器](../Topic/Iterators%20\(C%23%20and%20Visual%20Basic\).md)   
 [Statements](../../../visual-basic/language-reference/statements/index.md)