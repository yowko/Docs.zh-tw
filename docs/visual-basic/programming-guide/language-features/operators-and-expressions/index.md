---
title: "Visual Basic 中的運算子和運算式 | Microsoft Docs"
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
- operators [Visual Basic], operands
- operators [Visual Basic]
- operands, definition
- Visual Basic code, operators
- Visual Basic code, expressions
- operands
- expressions [Visual Basic]
ms.assetid: b86f3131-94ee-448f-96cd-79611e028b26
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
ms.translationtype: Human Translation
ms.sourcegitcommit: 31905a37f09db5f5192123f0118252fbe8b02eff
ms.openlocfilehash: 069178fe753c3e09116c8a4845f96faf13eb72ec
ms.contentlocale: zh-tw
ms.lasthandoff: 05/26/2017

---
<a id="operators-and-expressions-in-visual-basic" class="xliff"></a>

# Visual Basic 中的運算子和運算式
「運算子」是一種程式碼項目，可對保留值的一或多個程式碼項目執行運算。 值項目包含 `Function` 與 `Operator` 程序和運算式的變數、常數、常值、屬性、傳回值。  
  
 「運算式」是一系列與運算子合併的值項目，可產生新的值。 運算子透過執行計算、比較或其他作業來當成值項目。  
  
<a id="types-of-operators" class="xliff"></a>

## 運算子類型  
 [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] 提供下列運算子類型：  
  
-   [算術運算子](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)可對數值執行類似的計算，包括移位其位元模式。  
  
-   [比較運算子](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)可比較兩個運算式，並傳回代表比較結果的 `Boolean` 值。  
  
-   [串連運算子](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/concatenation-operators.md)可將多個字串連成單一字串。  
  
-   [Visual Basic 中的邏輯運算子和位元運算子](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)可合併 `Boolean` 或數值，並傳回與值相同之資料類型的結果。  
  
 與運算子合併使用的值項目稱為該運算子的「運算元」。 與值項目合併使用的運算子可形成運算式，但不含可形成「陳述式」的指派運算子。 如需詳細資訊，請參閱[陳述式](../../../../visual-basic/programming-guide/language-features/statements.md)。  
  
<a id="evaluation-of-expressions" class="xliff"></a>

## 運算式評估  
 運算式的最終結果代表值，通常是熟悉的資料類型，例如 `Boolean`、`String` 或數值類型。  
  
 下列是運算式範例。  
  
 `5 + 4`  
  
 `' The preceding expression evaluates to 9.`  
  
 `15 * System.Math.Sqrt(9) + x`  
  
 `' The preceding expression evaluates to 45 plus the value of x.`  
  
 `"Concat" & "ena" & "tion"`  
  
 `' The preceding expression evaluates to "Concatenation".`  
  
 `763 < 23`  
  
 `' The preceding expression evaluates to False.`  
  
 數個運算子可以在單一運算式或陳述式中執行動作，如下列範例所示。  
  
 [!code-vb[VbVbalrOperators#56](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/index_1.vb)]  
  
 在上述範例中，[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] 可在指派運算子 (`=`) 右側的運算式中執行作業，然後將產生的值指派給左側的 `x` 變數。 可合併到運算式的運算子數目沒有實際限制，但需要了解 [Visual Basic 中的運算子優先順序](../../../../visual-basic/language-reference/operators/operator-precedence.md)，才能確保您取得所要的結果。  
  
 如需詳細資訊和範例，請參閱 [Operator Overloading in Visual Basic 2005](http://go.microsoft.com/fwlink/?LinkId=101703) (Visual Basic 2005 中的運算子多載)。  
  
<a id="see-also" class="xliff"></a>

## 另請參閱  
 [運算子](../../../../visual-basic/language-reference/operators/index.md)   
 [有效的運算子組合](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/efficient-combination-of-operators.md)   
 [陳述式](../../../../visual-basic/language-reference/statements/index.md)
