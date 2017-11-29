---
title: Iterator (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.Iterator
helpviewer_keywords: Iterator keyword [Visual Basic]
ms.assetid: 69cb0b04-ac87-49d0-bcfe-810c0d60daff
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 503d586c0515b4cb53f8ec5656e5fe765cc094a7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="iterator-visual-basic"></a>Iterator (Visual Basic)
指定的函式或`Get`存取子是迭代器。  
  
## <a name="remarks"></a>備註  
 *迭代器*集合上執行自訂反覆項目。 迭代器會使用[產生](../../../visual-basic/language-reference/statements/yield-statement.md)陳述式來一次一個集合中傳回每個項目。 當`Yield`到達陳述式時，保留在程式碼中的目前位置。 下一次呼叫 Iterator 函式時，便會從這個位置重新開始執行。  
  
 可以實作迭代器，為函式或`Get`屬性定義的存取子。 `Iterator`修飾詞會出現在迭代器函式宣告或`Get`存取子。  
  
 從用戶端程式碼呼叫迭代器使用[每個...下一個陳述式](../../../visual-basic/language-reference/statements/for-each-next-statement.md)。  
  
 Iterator 函式的傳回型別或`Get`存取子可以是<xref:System.Collections.IEnumerable>， <xref:System.Collections.Generic.IEnumerable%601>， <xref:System.Collections.IEnumerator>，或<xref:System.Collections.Generic.IEnumerator%601>。  
  
 迭代器不能有任何`ByRef`參數。  
  
 迭代器不能出現在事件、執行個體建構函式、靜態建構函式或靜態解構函式中。  
  
 迭代器可以是匿名函式。 如需詳細資訊，請參閱[迭代器](http://msdn.microsoft.com/library/f45331db-d595-46ec-9142-551d3d1eb1a7)。  
  
 如需迭代器的詳細資訊，請參閱 [Iterators](http://msdn.microsoft.com/library/f45331db-d595-46ec-9142-551d3d1eb1a7) (迭代器)。  
  
## <a name="usage"></a>使用方式  
 `Iterator` 修飾詞可用於以下內容：  
  
-   [Function 陳述式](../../../visual-basic/language-reference/statements/function-statement.md)  
  
-   [Property 陳述式](../../../visual-basic/language-reference/statements/property-statement.md)  
  
## <a name="example"></a>範例  
 下列範例會示範 iterator 函式。 迭代器函式有`Yield`陳述式內[For...下一步](../../../visual-basic/language-reference/statements/for-next-statement.md)迴圈。 每個反覆項目[每個](../../../visual-basic/language-reference/statements/for-each-next-statement.md)陳述式主體中的`Main`建立呼叫`Power`iterator 函式。 每次呼叫 Iterator 函式都會執行下一個 `Yield` 陳述式，這會在 `For…Next` 迴圈的下一個反覆項目期間發生。  
  
 [!code-vb[VbVbalrStatements#98](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/iterator_1.vb)]  
  
## <a name="example"></a>範例  
 下列範例將示範本身為迭代器的 `Get` 存取子。 `Iterator`修飾詞是屬性宣告中。  
  
 [!code-vb[VbVbalrStatements#99](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/iterator_2.vb)]  
  
 如需其他範例，請參閱[迭代器](http://msdn.microsoft.com/library/f45331db-d595-46ec-9142-551d3d1eb1a7)。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Runtime.CompilerServices.IteratorStateMachineAttribute>  
 [迭代器](http://msdn.microsoft.com/library/f45331db-d595-46ec-9142-551d3d1eb1a7)  
 [Yield 陳述式](../../../visual-basic/language-reference/statements/yield-statement.md)
