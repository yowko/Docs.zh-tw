---
title: "在 Visual Basic 中的串連運算子 |Microsoft 文件"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- '& operator [Visual Basic], concatenation'
- concatenation operators
- operators [Visual Basic], concatenation
- Visual Basic code, operators
- + operator [Visual Basic], concatenation
- concatenation operators, Visual Basic strings
ms.assetid: e59908c3-89e0-41ae-933d-3e8826c16a04
caps.latest.revision: 18
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: fa11f1dcff2c333861596cbac03391403cf962c1
ms.lasthandoff: 03/13/2017

---
# <a name="concatenation-operators-in-visual-basic"></a>Visual Basic 中的串連運算子
串連運算子會將多個字串連成單一字串。 串連運算子有兩種：`+` 和 `&`。 兩者都會進行基本的串連作業，如下例所示。  
  
```vb
Dim x As String = "Mic" & "ro" & "soft" 
Dim y As String = "Mic" + "ro" + "soft" 
' The preceding statements set both x and y to "Microsoft".
```  
  
 這些運算子也可以串連 `String` 變數，如下列所示。  
  
 [!code-vb[VbVbalrOperators #&76;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/concatenation-operators_1.vb)]  
  
## <a name="differences-between-the-two-concatenation-operators"></a>兩種串連運算子之間的差異  
 [+ 運算子](../../../../visual-basic/language-reference/operators/addition-operator.md)新增兩個數字的主要目的。 不過，它也可以串連數值運算元與字串運算元。 `+`運算子有一組複雜的規則，以決定是否要加入、 串連、 通知編譯器錯誤，或擲回執行階段<xref:System.InvalidCastException>例外狀況。</xref:System.InvalidCastException>  
  
 [i 運算子](../../../../visual-basic/language-reference/operators/concatenation-operator.md)定義僅適用於`String`運算元和它一律會將運算元擴展到`String`，不論設定`Option Strict`。 建議使用 `&` 運算元進行字串串連，因為它的定義為專門針對字串，且能減少您產生意外轉換的機會。  
  
## <a name="performance-string-and-stringbuilder"></a>效能：String 和 StringBuilder  
 如果您有大量的字串，例如串連、 刪除和取代，操作您的效能可能可以藉由<xref:System.Text.StringBuilder>類別<xref:System.Text>命名空間。</xref:System.Text> </xref:System.Text.StringBuilder> 它會採用額外的指令，來建立和初始化<xref:System.Text.StringBuilder>物件，並將其最終值轉換成另一個指令`String`，但您可以彌補這個時間，因為<xref:System.Text.StringBuilder>執行地更快速。</xref:System.Text.StringBuilder> </xref:System.Text.StringBuilder>  
  
## <a name="see-also"></a>另請參閱  
 [Option Strict 陳述式](../../../../visual-basic/language-reference/statements/option-strict-statement.md)   
 [在 Visual Basic 中字串管理方法的類型](../../../../visual-basic/programming-guide/language-features/strings/types-of-string-manipulation-methods.md)   
 [在 Visual Basic 中的算術運算子](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)   
 [在 Visual Basic 中的比較運算子](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)   
 [在 Visual Basic 中的邏輯和位元運算子](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
